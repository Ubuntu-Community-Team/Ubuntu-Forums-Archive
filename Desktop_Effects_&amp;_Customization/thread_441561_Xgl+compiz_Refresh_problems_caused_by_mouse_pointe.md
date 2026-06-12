---
title: "Xgl+compiz: Refresh problems caused by mouse pointer"
date: 2007-05-12
forum: Desktop Effects &amp; Customization
---

### Post by Terendul on 2007-05-12
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/xserver-xgl/+bug/114127](https://bugs.launchpad.net/ubuntu/+source/xserver-xgl/+bug/114127) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Hi everybody !

I have Feisty with a Geforce 1.

Since I started using Xgl+compiz, I've been having refresh problems around the mouse pointer (like a box around it):
when there is a change in display around that box (for example: highlighting a text or using the ubuntu menu), it isn't properly managed.
Sometimes other parts of the screen appear around the pointer, sometimes the pointer disappears until I move the mouse again...

[IMG]http://librarian.launchpad.net/7607608/screenshot.jpg[/IMG]

Here is my xorg.conf : [http://librarian.launchpad.net/7607616/xorg.conf]("http://librarian.launchpad.net/7607616/xorg.conf")

Thanks for your help ! If you have any idea, there are most welcome...
Have a nice day.

Terendul

---

### Post by Terendul on 2007-05-13
up!

---

### Post by hlewies on 2007-08-29
HI Terendul,

I'm also getting the exact same problem. Please let me know if/ when you get a solution for the problem. It is annoying as hell.

Thanks

---

### Post by biochip2k on 2007-10-20
I have the same problem!

I have  a intel i810 chipset with AIGLX. same in Feisty and Gutsy.

This do not happen with a XGL-server installed.

Regards

---

### Post by ChupaMe on 2007-11-18
I have the same problem! 

Ubuntu 7.10 Gutsy Gibbon
GeForce 256 DDR.
Installed packages: xserver-xgl, compiz, nvidia-glx-legacz

Kind regards

---

### Post by drink on 2007-11-23
I hve the problem too, 7.10 with nvidia quadro fx1500. just updated...

---

### Post by westbywest on 2007-12-27
I see this problem in compiz *without* using xserver-xgl, but rather with GLX capabilities in the open source ATI video driver, so the bug may lie elsewhere. Indeed, I see the problem even when I just enable System->Preferences->Appearance->Visual Effects->Normal (i.e. no compiz at all).

The artifacts are especially bad when slowly dragging windows up or down. I'm attaching a screenshot.

My specs:
HP NW8240 Laptop
ATI Technologies Inc Radeon Mobility X700 (PCIE)
Ubuntu v7.10
compiz 0.6.0+git20071008-0ubuntu1.1
libgl1-mesa-glx v7.0.1-1ubuntu3
libgl1-mesa-dri v7.0.1-1ubuntu3
linux-image v2.6.22-14-pentm+suspend2 (tuxonice patch, compiled for Pentium M)
xserver-xorg-video-ati v6.7.197-1ubuntu1~tormod (patched to fix problem with LCD display sync)
xserver-xorg v7.2-5ubuntu13

---

### Post by westbywest on 2007-12-28
Here is a related (or duplicate)  bug report.
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/175075](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/175075)

---

### Post by mempman on 2008-02-17
any solution to this problem yet.....I am desperately waiting!!

---

### Post by koda on 2008-02-17
i use gentoo here, but i had the same problem as in the picture!
however by putting

Option "SWCursor" "off"

it actually resolved all my problem!
try modifying the xorg.conf accoring to this guide: [http://gentoo-wiki.com/HOWTO_AIGLX](http://gentoo-wiki.com/HOWTO_AIGLX)

i have a ATI Radeon Mobility M6 (chip rv100) -- my first and last ati btw


bye
Koda

---

### Post by mempman on 2008-02-17
It's funny that you should say that because I had to delete those lines in order to get my problem fixed.

---

