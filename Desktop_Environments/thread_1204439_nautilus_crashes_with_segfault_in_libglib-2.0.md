---
title: "nautilus crashes with segfault in libglib-2.0"
date: 2009-07-04
forum: Desktop Environments
---

### Post by solitaire on 2009-07-04
I'm having a strange problem with Nautilus crashing when i click on the "computer" icon in places menu... I also loose desktop icons as well.

I get the following entry in my log file:
```
Jul  4 22:43:34 Europa kernel: [43289.282786] nautilus[4715]: segfault at 0 ip b79083d7 sp bfc47954 error 4 in libglib-2.0.so.0.2000.1[b78ab000+b6000]

```i've reinstalled libglib-2.0.2000 just going to try a log out and back in to see if that fixes this...

else anyone got a suggestion?

*update*
Still getting a segfault.

Thinking of doing a reinstall anyway but would like to sort this out in case it happens again...

---

### Post by jrutila on 2009-07-07
I'm (actually my sister is) experiencing same kind of segfaults.

I have only remote connection to the machine, but before she logs in with gdm everything seems calm. When she logs in and starts fro example gimp or pidgin following errors come to /var/log/messages.

```

Jul  7 12:05:23 vete kernel: [ 1924.692584] gconftool-2[4375] general protection ip:b803f9a2 sp:bfc89574 error:0 in libxml2.so.2.6.32[b7f1f000+135000]
Jul  7 12:06:02 vete kernel: [ 1964.362624] pidgin[3858]: segfault at 18 ip 080e8eab sp bfc969f0 error 4 in pidgin[8048000+c6000]
Jul  7 12:06:59 vete kernel: [ 2021.500997] nautilus[4388]: segfault at ffe1ead5 ip b4dab830 sp b4ddff40 error 4 in libjpeg.so.62.0.0[b4d9b000+1f000

```

These same kind of segfaults (error in libc, libjpeg, libglib, pidgin) also come from gimp-2.6 and firefox and other programs she tries to run.

System is fresh Ubuntu Jaunty 9.04. It is an older computer where I added more RAM recently so it could be memory issue.
I put her to run memtest to see if it is a memory issue.

Do you have any other ideas what might cause this kind of behavior?

---

### Post by wetmonkey on 2009-07-07
Check out and if applicable, add a comment here: 
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/396672](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/396672)

Looks like it's something recently happening.  Did you just do an update or install UbuntuOne?  Those were the 'new' things for me before it started.

---

### Post by freakalad on 2009-07-08
I'm getting this bug on one of my Jaunty-64 systems, but not on my laptop running 64-bit Jaunty. Both run KVM & libvirt, as well as UbuntuOne

Will check bug reports too

---

### Post by BennyLZ on 2009-07-08
I'm having this bug on jaunty.
I get this:
```
Jul  8 12:44:57 polimeni kernel: [  120.116250] nautilus[3444]: segfault at 0 ip b798c3d7 sp bf9c34e4 error 4 in libglib-2.0.so.0.2000.1[b792f000+b6000]
```
if I click on "computer" or "network".
But... yesterday evening it worked, then this morning it doesn't work anymore!!
Is someone getting a solution?

EDIT: it works after uninstalling ubuntu one...

---

### Post by tpischke on 2009-07-08
Ditto here, just installed Ubuntu One

---

### Post by razius on 2009-07-08
same problem , uninstalled ubuntuone and it works just fine now.

---

### Post by potam on 2009-07-08
> **razius said:**
> same problem , uninstalled ubuntuone and it works just fine now.

Same solution for me, thanks!

---

### Post by Light-kun on 2010-12-28
Have no UbuntuOne installed but experiencing Nautilus segfaults.
[PHP]# sudo apt-cache pkgnames|grep ubuntu|grep one
#

Linux local 2.6.29-1-netbook #0array1 SMP Mon Feb 23 15:02:03 MST 2009 i686 GNU/Linux

Dec 29 05:27:47 local kernel: [80650.622824] nautilus[4740]: segfault at 1 ip b7989bcb sp bf9c6420 error 4 in libglib-2.0.so.0.2000.1[b7931000+b6000][/PHP]

---

### Post by maatthc on 2011-02-19
Same with me: a lot of entries like:
[  727.235758] nautilus[3682]: segfault at 0 ip b6f246f7 sp bfb4d6c4 error 4 in libglib-2.0.so.0.2600.0[b6ec3000+cd000]

on dmesg output. Couldnt open the "Places"  menu. When I login I could see dozens of Nautilus windows crashing. So I killed :

/usr/bin/python /usr/lib/ubuntuone-client/ubuntuone-syncdaemon

And everything works well.

I was using Ubuntu One to sync some files from work to home.

I'm using 10.10 and home and at work, both systems are updated. 

Any ideas?

Regards,

MaaT

---

