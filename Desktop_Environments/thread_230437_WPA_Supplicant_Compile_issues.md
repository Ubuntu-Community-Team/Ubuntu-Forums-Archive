---
title: "WPA Supplicant Compile issues"
date: 2006-08-05
forum: Desktop Environments
---

### Post by taskic on 2006-08-05
Hey Guys, 
I've been trying to compile WPA_supplicant 0.5.4 or 0.4.9 and get this same compile error with both:

cc  -o wpa_supplicant config.o common.o md5.o md4.o rc4.o sha1.o os_unix.o eloop.o config_file.o base64.o l2_packet_linux.o eap_tls.o eap_peap.o eap_ttls.o eap_md5.o eap_mschapv2.o eap_gtc.o eap_otp.o eap_leap.o eap_tlv.o eapol_sm.o eap.o eap_methods.o eap_tls_common.o tls_openssl.o ms_funcs.o crypto.o ctrl_iface.o ctrl_iface_unix.o wpa.o preauth.o pmksa_cache.o aes_wrap.o wpa_supplicant.o events.o main.o drivers.o driver_hostap.o driver_ndiswrapper.o driver_ipw.o driver_wired.o driver_wext.o -L/usr/local/ssl/lib -lssl -lcrypto
/usr/local/ssl/lib/libcrypto.a(dso_dlfcn.o): In function `dlfcn_load':dso_dlfcn.c:(.text+0x45): undefined reference to `dlopen'
:dso_dlfcn.c:(.text+0xa1): undefined reference to `dlclose'
:dso_dlfcn.c:(.text+0xcc): undefined reference to `dlerror'
/usr/local/ssl/lib/libcrypto.a(dso_dlfcn.o): In function `dlfcn_unload':dso_dlfcn.c:(.text+0x15b): undefined reference to `dlclose'
/usr/local/ssl/lib/libcrypto.a(dso_dlfcn.o): In function `dlfcn_bind_var':dso_dlfcn.c:(.text+0x21b): undefined reference to `dlsym'
:dso_dlfcn.c:(.text+0x291): undefined reference to `dlerror'
/usr/local/ssl/lib/libcrypto.a(dso_dlfcn.o): In function `dlfcn_bind_func':dso_dlfcn.c:(.text+0x30d): undefined reference to `dlsym'
:dso_dlfcn.c:(.text+0x389): undefined reference to `dlerror'
collect2: ld returned 1 exit status
make: *** [wpa_supplicant] Error 1

Can anyone tell me what i need to do to fix this. I have openssl installed also and tested and working and the correct paths in my .config file
I am using 6.06

Thanks Heaps

---

### Post by sir_mud on 2006-08-05
Are you sure you have the -dev version installed. The package name is libssl-dev.

---

### Post by taskic on 2006-08-06
AAAHHHHHHH that has solved it. Thanks heaps sir mud i was lost and trying to use the openssl package and not the libssl-dev one.
Cheers

---

