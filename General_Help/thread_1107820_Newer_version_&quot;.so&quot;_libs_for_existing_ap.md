---
title: "Newer version &quot;.so&quot; libs for existing app??"
date: 2009-03-27
forum: General Help
---

### Post by ddastoor on 2009-03-27
Hi, 
I had this problem on solaris, but it applies to all.
"wget" would not work:
-----------------------------------
ld.so.1: wget: fatal: libssl.so.0.9.6: open failed: No such file or directory
Killed
--------------------------------------

So, I did an ldd on "wget" on my system and got:
----------------------------------------------
        libmd5.so.1 =>   /usr/lib/libmd5.so.1
        libssl.so.0.9.6 =>       (file not found)
        libcrypto.so.0.9.6 =>    (file not found)
        libdl.so.1 =>    /usr/lib/libdl.so.1
        libsocket.so.1 =>        /usr/lib/libsocket.so.1
        libnsl.so.1 =>   /usr/lib/libnsl.so.1
        libc.so.1 =>     /usr/lib/libc.so.1
        libmp.so.2 =>    /usr/lib/libmp.so.2
        /usr/platform/SUNW,Netra-T12/lib/libmd5_psr.so.1
        /usr/platform/SUNW,Netra-T12/lib/libc_psr.so.1
----------------------------------------------------------
Note the 2 libs that said "(file not found)".
When I searched for these 2 libs, I found them but with a newer version, viz. "lib...0.9.7".

My question:
Is there an ALTERNATIVE to getting the newer version of "wget" that accesses these 2 "0.9.7" version libs ? 
                               Or 
Is there a tool that I can use to make the existing "wget binary" read the new lib versions?


I sym-linked: 
libssl.so.0.9.6 --> libssl.so.0.9.7 and
libcrypto.so.0.9.6 --> libcrypto.so.0.9.7
Now, "wget" ran, but then I got a symbol undefined problem.

Thanks.

---

