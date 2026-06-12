---
title: "compiling error for NCL NCARG and GRADS"
date: 2009-11-11
forum: Education &amp; Science
---

### Post by kzhang on 2009-11-11
Hello Ubuntu experts, 

I encountered some problems when compiling NCL NCARG 5.1.1 and GRADS 2.0 on the new ubuntu 9.10 32 bit system.  The compile log shows me following error messages (example for GRADS, but similar message for NCARG):
```

/usr/lib/libX11.a(xim_trans.o): In function `_XimXTransSocketOpen':
(.text+0x66e): warning: Using 'getaddrinfo' in statically linked applications requires at runtime the shared libraries from the glibc version used for linking
/usr/lib/libX11.a(xim_trans.o): In function `_XimXTransSocketUNIXConnect':
(.text+0xe1b): warning: Using 'gethostbyname' in statically linked applications requires at runtime the shared libraries from the glibc version used for linking
/usr/lib/libX11.a(xim_trans.o): In function `_XimXTransSocketINETConnect':
(.text+0x22aa): warning: Using 'getservbyname' in statically linked applications requires at runtime the shared libraries from the glibc version used for linking
/usr/lib/libX11.a(CrGlCur.o): In function `open_library':
(.text+0x3b): warning: Using 'dlopen' in statically linked applications requires at runtime the shared libraries from the glibc version used for linking
/usr/lib/libX11.a(ClDisplay.o): In function `XCloseDisplay':
(.text+0xbd): undefined reference to `xcb_disconnect'
/usr/lib/libX11.a(OpenDis.o): In function `OutOfMemory':
(.text+0x3f9): undefined reference to `xcb_disconnect'
/usr/lib/libX11.a(OpenDis.o): In function `XOpenDisplay':
(.text+0x7a4): undefined reference to `xcb_get_setup'
/usr/lib/libX11.a(OpenDis.o): In function `XOpenDisplay':
(.text+0xd1d): undefined reference to `xcb_get_maximum_request_length'
/usr/lib/libX11.a(xcb_disp.o): In function `_XConnectXCB':
(.text+0xa8): undefined reference to `xcb_parse_display'
/usr/lib/libX11.a(xcb_disp.o): In function `_XConnectXCB':
(.text+0x16e): undefined reference to `xcb_connect_to_display_with_auth_info'
/usr/lib/libX11.a(xcb_disp.o): In function `_XConnectXCB':
(.text+0x18c): undefined reference to `xcb_get_file_descriptor'
/usr/lib/libX11.a(xcb_disp.o): In function `_XConnectXCB':
(.text+0x1b3): undefined reference to `xcb_generate_id'
/usr/lib/libX11.a(xcb_disp.o): In function `_XConnectXCB':
(.text+0x1e8): undefined reference to `pthread_cond_init'
/usr/lib/libX11.a(xcb_disp.o): In function `_XConnectXCB':
(.text+0x1f0): undefined reference to `xcb_connection_has_error'
/usr/lib/libX11.a(xcb_disp.o): In function `_XConnectXCB':
(.text+0x224): undefined reference to `xcb_connect'
/usr/lib/libX11.a(xcb_io.o): In function `require_socket':
(.text+0x384): undefined reference to `xcb_take_socket'
/usr/lib/libX11.a(xcb_io.o): In function `wait_or_poll_for_event':
(.text+0x40c): undefined reference to `xcb_wait_for_event'
/usr/lib/libX11.a(xcb_io.o): In function `wait_or_poll_for_event':
(.text+0x475): undefined reference to `xcb_poll_for_event'
/usr/lib/libX11.a(xcb_io.o): In function `process_responses':
(.text+0x53b): undefined reference to `xcb_poll_for_reply'
/usr/lib/libX11.a(xcb_io.o): In function `process_responses':
(.text+0x6ba): undefined reference to `xcb_connection_has_error'
/usr/lib/libX11.a(xcb_io.o): In function `_XAllocIDs':
(.text+0x7ac): undefined reference to `xcb_generate_id'
/usr/lib/libX11.a(xcb_io.o): In function `_XIDHandler':
(.text+0x81e): undefined reference to `xcb_generate_id'
/usr/lib/libX11.a(xcb_io.o): In function `_XSend':
(.text+0xa19): undefined reference to `xcb_writev'
/usr/lib/libX11.a(xcb_io.o): In function `_XReply':
(.text+0xc0a): undefined reference to `xcb_wait_for_reply'
make[2]: *** [grads] Error 1
make[2]: Leaving directory `/usr/software/grads-2.0.a7.1 (2)/src'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/usr/software/grads-2.0.a7.1 (2)/src'
make: *** [all-recursive] Error 1

```It is wired that there was no problem when compiling same packages on previous version of UBUNTU.  I've no idea what cause those problems.  Any advise would be much appreciated!

---

