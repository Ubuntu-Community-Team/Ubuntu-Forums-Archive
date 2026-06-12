---
title: "errors 'no suitable mode' and 'unkown command 'terminal'' after 10.04"
date: 2010-05-23
forum: Dell Ubuntu Support (CLOSED)
---

### Post by JDP91 on 2010-05-23
Hi , my laptop Dell Inspiron 500M was running ubuntu 9.10. I updated it to 10.04. the update never ended (remaining time was always 27mn). At following boot I got the messages:
=============
error: no suitable mode found.
error: unknown command 'terminal' .
=============
The disk continues working a small time then everything stops with a black screen.

I can boot in reduce video mode (maintaining shift during the boot) and everything goes well (except my mysql configuration that seems to have been corrupted during the non-ending update). but next boot in mormal mode the same messages occur.
I saw many threads about similar errors after updating to 10.04, but no solution helped. (I tried to modify screen resolution in grub.cfg,...)
Any suggestion would help

---

### Post by JDP91 on 2010-05-29
> **JDP91 said:**
> Hi , my laptop Dell Inspiron 500M was running ubuntu 9.10. I updated it to 10.04. the update never ended (remaining time was always 27mn). At following boot I got the messages:
=============
error: no suitable mode found.
error: unknown command 'terminal' .
=============
The disk continues working a small time then everything stops with a black screen.

I can boot in reduce video mode (maintaining shift during the boot) and everything goes well (except my mysql configuration that seems to have been corrupted during the non-ending update). but next boot in mormal mode the same messages occur.
I saw many threads about similar errors after updating to 10.04, but no solution helped. (I tried to modify screen resolution in grub.cfg,...)
Any suggestion would help
The problem is partly solved
I modified  /etc/default/grub file by adding i915.modeset=1 in the following line
GRUB_CMDLINE_LINUX_DEFAULT=”quiet splash i915.modeset=1&#8243;

then sudo update-grub

Both grub error messages are still there but boot goes on up to the end and I can now work again :P

---

### Post by maubp on 2010-06-29
Same issue on a Dell D500 latops (upgrade and clean install). :(

---

### Post by maubp on 2010-07-06
> **maubp said:**
> Same issue on a Dell D500 latops (upgrade and clean install). :(
Got there in the end with this:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)

---

### Post by yatsek on 2013-04-17
Just for anyone looking for solving this problem under KVM with cirrus/vmvga (I've got here searching for this) - TLDR: just do grub upgrade

Taken from askubuntu ([http://askubuntu.com/questions/157772/how-do-i-upgrade-to-the-latest-grub-2-00](http://askubuntu.com/questions/157772/how-do-i-upgrade-to-the-latest-grub-2-00))
You may need to install missing packages if ./configure doesn't work (I had to do: apt-get install flex)

sudo apt-get build-dep 

grub2 wget -O- [ftp://ftp.gnu.org/gnu/grub/grub-2.00.tar.xz](ftp://ftp.gnu.org/gnu/grub/grub-2.00.tar.xz) | tar -xJ 

cd grub-2.00 ./configure --prefix=/usr 

make 

sudo make install   

[LIST]
[*]Now, you need to install the new Grub to **where your existing Grub is**. If you don't know where or how to find out, quit now!
[LIST]
[*]If you have a dual-boot system, be especially careful about whether you should install to the *disk* or to the *partition!* 
[*]Replace *sdq* as appropriate: 
sudo grub-install /dev/sdq 
[*]Run sudo update-grub 
[/LIST]
    
[/LIST]

---

### Post by wildmanne39 on 2013-04-19
Thread closed. Please do not post in old threads.

---

