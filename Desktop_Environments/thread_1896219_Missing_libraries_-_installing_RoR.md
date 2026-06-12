---
title: "Missing libraries - installing RoR"
date: 2011-12-16
forum: Desktop Environments
---

### Post by isri on 2011-12-16
Hello,

I'm trying to install RoR using ror_installer and I'm getting following error

```

> ./ror_installer
./ror_installer: error while loading shared libraries: libwx_baseu-2.8.so.0: cannot open shared object file: No such file or directory
zsh: exit 127   ./ror_installer

> whereis libwx_baseu-2.8.so.0
libwx_baseu-2.8.so: /usr/lib/libwx_baseu-2.8.so /usr/lib/libwx_baseu-2.8.so.0 /usr/lib64/libwx_baseu-2.8.so /usr/lib64/libwx_baseu-2.8.so.0 /usr/local/lib/libwx_baseu-2.8.so.0

> ldd ror_installer
    linux-gate.so.1 =>  (0xf76e5000)
    libwx_baseu-2.8.so.0 => not found
    libwx_gtk2u_core-2.8.so.0 => not found
    libwx_gtk2u_html-2.8.so.0 => not found
    libwx_gtk2u_adv-2.8.so.0 => not found
    libstdc++.so.6 => /usr/lib32/libstdc++.so.6 (0xf75c9000)
    libm.so.6 => /lib32/libm.so.6 (0xf75a3000)
    libgcc_s.so.1 => /usr/lib32/libgcc_s.so.1 (0xf7584000)
    libpthread.so.0 => /lib32/libpthread.so.0 (0xf756a000)
    libc.so.6 => /lib32/libc.so.6 (0xf7410000)
    /lib/ld-linux.so.2 (0xf76e6000)

> whereis libwx_gtk2u_core-2.8.so.0
libwx_gtk2u_core-2.8.so: /usr/lib/libwx_gtk2u_core-2.8.so /usr/lib/libwx_gtk2u_core-2.8.so.0 /usr/lib64/libwx_gtk2u_core-2.8.so /usr/lib64/libwx_gtk2u_core-2.8.so.0

> whereis libwx_gtk2u_html-2.8.so.0
libwx_gtk2u_html-2.8.so: /usr/lib/libwx_gtk2u_html-2.8.so /usr/lib/libwx_gtk2u_html-2.8.so.0 /usr/lib64/libwx_gtk2u_html-2.8.so /usr/lib64/libwx_gtk2u_html-2.8.so.0

> whereis libwx_gtk2u_adv-2.8.so.0
libwx_gtk2u_adv-2.8.so: /usr/lib/libwx_gtk2u_adv-2.8.so /usr/lib/libwx_gtk2u_adv-2.8.so.0 /usr/lib64/libwx_gtk2u_adv-2.8.so /usr/lib64/libwx_gtk2u_adv-2.8.so.0


```

As You can see script doesn't see libraries but those exists.

Whet could be the source of problem?

Thanks

---

### Post by ncrause on 2013-04-17
I had the same issue when installing BOINC (for working with SETI @ Home). Ignore the underscores, and look for libwxgtk in your ap repository (under Xubuntu 12.20 I used libwxgtk2.8-0 and libwxgtk2.8-dev).

---

### Post by overdrank on 2013-04-17
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/misc.php?do=showrules")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

