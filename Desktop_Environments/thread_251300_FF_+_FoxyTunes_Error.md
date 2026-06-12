---
title: "FF + FoxyTunes Error"
date: 2006-09-05
forum: Desktop Environments
---

### Post by mattmac24 on 2006-09-05
hello,

ive been using firefox for a while now and am using amarok to manage my music. i wanted to control my music from a web browser so i installed foxytunes.

However when i click on the foxytunes icon and go up and select "player" i get the message "Installation problem. click for help". i then click and it leads me to the default foxy tunes FAQ which is of no help.

and just to be clear it isnt really an error message as its actually in the menu...if that makes sense..wont let me take screen shot for you because as soon as i press alt the menu closes:-k 

and ive tried reinstalling it, im using the most recent version of everything.

thanks for ur help.

matt

---

### Post by mattmac24 on 2006-09-06
bump...with this being one of the more popular progs running on ubuntu would of thought there would be better documentation for ths.

Any ideas, anyone?

Matt

---

### Post by legesh on 2006-09-06
hi,

as I know, FoxyTunes should work with Ubuntu, *unless* you have a 64-bit system, on which the extension is not supported.

legesh

---

### Post by mattmac24 on 2006-09-06
nop using 32 bit, acer travelmate 3200

thx for da idea thou.

---

### Post by legesh on 2006-09-06
Could you execute this ```
$cd (HOME)/.mozilla/firefox/YOUR_PROFILE/{463F6CA5-EE3C-4be1-B7E6-7FEE11953374}/components
ldd FoxyTunes.dll
``` and post here the output

-legesh

---

### Post by mattmac24 on 2006-09-06
well after a bit of a hunt for the file, and then changing the files permissions so i could actually do what you told me to do i got the following:
linux-gate.so.1 =>  (0xffffe000)
        libgmodule-1.2.so.0 => not found
        libglib-1.2.so.0 => not found
        libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb7fb3000)
        libXi.so.6 => /usr/lib/libXi.so.6 (0xb7fab000)
        libXext.so.6 => /usr/lib/libXext.so.6 (0xb7f9e000)
        libX11.so.6 => /usr/lib/libX11.so.6 (0xb7eb7000)
        libstdc++.so.5 => /usr/lib/libstdc++.so.5 (0xb7dfd000)
        libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb7ddb000)
        libgcc_s.so.1 => /lib/libgcc_s.so.1 (0xb7dd1000)
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7ca2000)
        /lib/ld-linux.so.2 (0x80000000)
        libXau.so.6 => /usr/lib/libXau.so.6 (0xb7c9f000)

am now searching for the packages it says are missing.
will post back soon.

Matt


edit: Installed the missing one, reinstalled and all good,
thanks heaps:D

Matt

---

### Post by sethvath on 2007-01-01
> **mattmac24 said:**
> well after a bit of a hunt for the file, and then changing the files permissions so i could actually do what you told me to do i got the following:
linux-gate.so.1 =>  (0xffffe000)
        libgmodule-1.2.so.0 => not found
        libglib-1.2.so.0 => not found
        libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb7fb3000)
        libXi.so.6 => /usr/lib/libXi.so.6 (0xb7fab000)
        libXext.so.6 => /usr/lib/libXext.so.6 (0xb7f9e000)
        libX11.so.6 => /usr/lib/libX11.so.6 (0xb7eb7000)
        libstdc++.so.5 => /usr/lib/libstdc++.so.5 (0xb7dfd000)
        libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb7ddb000)
        libgcc_s.so.1 => /lib/libgcc_s.so.1 (0xb7dd1000)
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7ca2000)
        /lib/ld-linux.so.2 (0x80000000)
        libXau.so.6 => /usr/lib/libXau.so.6 (0xb7c9f000)

am now searching for the packages it says are missing.
will post back soon.

Matt


edit: Installed the missing one, reinstalled and all good,
thanks heaps:D

Matt

Weird that I only have 6 libs listed and no missing:
        linux-gate.so.1 =>  (0xffffe000)
        libstdc++.so.5 => /usr/lib/libstdc++.so.5 (0xb7ef4000)
        libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb7ece000)
        libgcc_s.so.1 => /lib/libgcc_s.so.1 (0xb7ec3000)
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7d8e000)
        /lib/ld-linux.so.2 (0x80000000)

Any help with getting Foxytunes to work with Rhythmbox?
Thanks in advance

---

### Post by Gourgi on 2008-02-07
hi , i can't make it work either :(
[B]ubuntu hardy8.04 alpha4 amd64,
Rhythmbox 0.11.4,
 Firefox 2.0.0.10 ,
 FoxyTunes 2.95[/B]


**ldd FoxyTunes.dll ** output : 
```
	linux-gate.so.1 =>  (0xffffe000)
	libstdc++.so.5 => /usr/lib32/libstdc++.so.5 (0xf7e86000)
	libm.so.6 => /lib32/libm.so.6 (0xf7e61000)
	libgcc_s.so.1 => /usr/lib32/libgcc_s.so.1 (0xf7e55000)
	libc.so.6 => /lib32/libc.so.6 (0xf7d06000)
	/lib/ld-linux.so.2 (0xf7f71000)

```

any help appreciated

---

