#----------------------------------------------------------------------------
#
# Postgres-XC GTM proxy Makefile
#
# Copyright(c) 2010-2012 Postgres-XC Development Group
#
# src/gtm/proxy/Makefile
#
#-----------------------------------------------------------------------------
top_builddir=../../..
include $(top_builddir)/src/Makefile.global
subdir=src/gtm/proxy

ifneq ($(PORTNAME), win32)
override CFLAGS += $(PTHREAD_CFLAGS)
endif

OBJS=proxy_main.o proxy_thread.o proxy_utils.o gtm_proxy_opt.o

OTHERS= ../libpq/libpqcomm.a ../path/libgtmpath.a ../recovery/libgtmrecovery.a ../client/libgtmclient.a ../common/libgtm.a

LDFLAGS=-L$(top_builddir)/common -L$(top_builddir)/libpq

LIBS=-lpthread

gtm_proxy:$(OBJS)
	$(CC) $(CFLAGS) $(LDFLAGS) $(LIBS) $^ $(OTHERS) ../../port/libpgport_srv.a -o gtm_proxy

all:gtm_proxy

clean:
	rm -f $(OBJS)
	rm -f gtm_proxy

distclean: clean

maintainer-clean: distclean
