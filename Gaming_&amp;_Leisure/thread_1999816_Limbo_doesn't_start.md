---
title: "Limbo doesn't start"
date: 2012-06-08
forum: Gaming &amp; Leisure
---

### Post by BcRich on 2012-06-08
Hi 
I installed Limbo by downloading x64 deb from HIB site. everything went along fine during installation, and download (checked the md5sum so the file is not corrupt).  However, when I try to launch the game:
```
\/opt/limbo/bin/wine --bottle default --workdir 'C:\Program Files\limbo' --wait-children --cx-app limbo.exe
```
I get this 
```
p11-kit: couldn't load module: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: cannot open shared object file: No such file or directory
wine: Unhandled page fault on write access to 0x7d734000 at address 0xf746e671 (thread 0030), starting debugger...
s\limbo\limbo.exe: malloc.c:2451: sYSMALLOc: Assertion `(old_top == (((mbinptr) (((char *) &((av)->bins[((1) - 1) * 2])) - __builtin_offsetof (struct malloc_chunk, fd)))) && old_size == 0) || ((unsigned long) (old_size) >= (unsigned long)((((__builtin_offsetof (struct malloc_chunk, fd_nextsize))+((2 * (sizeof(size_t))) - 1)) & ~((2 * (sizeof(size_t))) - 1))) && ((old_top)->size & 0x1) && ((unsigned long)old_end & pagemask) == 0)' failed.
```
when I looked for /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so it is actually located at /usr/lib/x86_64-linux-gnu/pkcs11/gnome-keyring-pkcs11.so 
Is this a multiarch problem as pointed out in this bug report [https://bugs.launchpad.net/ubuntu/+source/p11-kit/+bug/888199](https://bugs.launchpad.net/ubuntu/+source/p11-kit/+bug/888199)
I guess I cold try copying the file to the location that limbo expects it to be at but I was wondering if some one could tell me of how to simlink to this file so that limbo can find it if that's possible? Thanks :)

---

### Post by doorknob60 on 2012-06-08
You need the 32 bit version of the lib. I can't confirm whether this will work, but I think it should:
```
sudo apt-get install gnome-keyring:i386
```


But if that doesn't work:
> Found a 100% working fix:

"1) Install getlibs

wget [https://launchpad.net/~jcollins/+archive/jaminppa/+build/1482994/+files/getlibs_2.06-0ubuntu1%7Eppa2_all.deb](https://launchpad.net/~jcollins/+archive/jaminppa/+build/1482994/+files/getlibs_2.06-0ubuntu1%7Eppa2_all.deb)

sudo dpkg -i getlibs_2.06-0ubuntu1~ppa2_all.deb

2) Install the 32bit lib

getlibs -p gnome-keyring:i386

3) Make the symbolic link

sudo ln -s /usr/lib32/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so

Now run your Crossover/Wine app and the error is gone."

From this bug: [https://bugs.launchpad.net/ubuntu/+source/gnome-keyring/+bug/885492](https://bugs.launchpad.net/ubuntu/+source/gnome-keyring/+bug/885492)

---

### Post by BcRich on 2012-06-08
> **doorknob60 said:**
> You need the 32 bit version of the lib. I can't confirm whether this will work, but I think it should:
```
sudo apt-get install gnome-keyring:i386
```
But if that doesn't work:


From this bug: [https://bugs.launchpad.net/ubuntu/+source/gnome-keyring/+bug/885492](https://bugs.launchpad.net/ubuntu/+source/gnome-keyring/+bug/885492)
Hi doorknob60
Thanks for the reply, I tried your 1st suggestion but i get this 
```
The following packages have unmet dependencies:
 gnome-keyring:i386 : Depends: libgck-1-0:i386 (>= 2.91.1) but it is not going to be installed
                      Depends: libgcr-3-1:i386 (>= 3.2.2) but it is not going to be installed
```
and the second suggestion seems to work but when attempting to launch limbo I get this
```
wine: Unhandled page fault on write access to 0x7c716000 at address 0xf7523671 (thread 0038), starting debugger...
s\limbo\limbo.exe: malloc.c:2451: sYSMALLOc: Assertion `(old_top == (((mbinptr) (((char *) &((av)->bins[((1) - 1) * 2])) - __builtin_offsetof (struct malloc_chunk, fd)))) && old_size == 0) || ((unsigned long) (old_size) >= (unsigned long)((((__builtin_offsetof (struct malloc_chunk, fd_nextsize))+((2 * (sizeof(size_t))) - 1)) & ~((2 * (sizeof(size_t))) - 1))) && ((old_top)->size & 0x1) && ((unsigned long)old_end & pagemask) == 0)' failed.
```
so atleast it's managed to fix the multiarch issue :) thanks
any suggestions as to whats going on here? I'm stumped...

---

### Post by BcRich on 2012-06-10
[http://askubuntu.com/questions/145528/how-to-run-humble-bundle-v-games-on-a-system-with-nvidia-twinview](http://askubuntu.com/questions/145528/how-to-run-humble-bundle-v-games-on-a-system-with-nvidia-twinview)
Something else I found, it didn't work for me but maybe it'll work for some else??

---

### Post by nll on 2012-07-22
I have the same problem here. Any news?

---

### Post by BcRich on 2012-07-22
hi nll
I downloaded the latest version, re-installed and it worked fine. except the sound would occasionally fail to start. in which case i had to open up the configure wine utility, test the sound from there, then restart limbo a few times till the sound worked again.

---

### Post by nll on 2012-07-27
I got a message from Humble Bundle and CodeWeavers with some workarounds. First, install libncurses (sudo apt-get install libncurses5:i386). Then, follow [this]("http://www.codeweavers.com/support/wiki/linux/faq/ubuntu_keyring"), [this]("http://www.codeweavers.com/support/wiki/linux/faq/ubuntu1204"), and [this]("http://www.codeweavers.com/support/wiki/linux/faq/ubuntu1206jpeg") link. If you're trying to run it with an Intel card, you need to launch it by forcing S3TC in the command (force_s3tc_enable=true /opt/limbo/bin/wine --cx-app limbo.exe). If you tried this steps and it did not work, fetch Limbo's debug (/opt/limbo/bin/cxdiag  --debug) and contact CodeWeavers.

---

