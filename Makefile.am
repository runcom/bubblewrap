AM_CFLAGS = $(WARN_CFLAGS)

bin_PROGRAMS = bwrap

bwrap_srcpath := $(srcdir)
include Makefile-bwrap.am

install-exec-hook:
if PRIV_MODE_SETUID
	$(SUDO_BIN) chown root $(DESTDIR)$(bindir)/bwrap
	$(SUDO_BIN) chmod u+s $(DESTDIR)$(bindir)/bwrap
else
if PRIV_MODE_FILECAPS
	$(SUDO_BIN) setcap cap_sys_admin,cap_sys_chroot+ep $(DESTDIR)$(bindir)/bwrap
endif
endif

include Makefile-docs.am

TESTS = tests/test-basic.sh
TESTS_ENVIRONMENT = PATH=$$(cd $(top_builddir) && pwd):$${PATH}
