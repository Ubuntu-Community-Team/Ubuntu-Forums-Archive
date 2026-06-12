---
title: "hopefully easy fix (kernel panic)"
date: 2008-12-04
forum: General Help
---

### Post by Siruso on 2008-12-04
hey everybody!

I just downloaded Ubuntu 8.10 with wubi and I must say that it was almost too easy.  I'm very impressed with everything about Ubuntu and will be recommending it to all my friends and family who are sick of Vista.

But of course...

I'm getting that "caps lock light flashy thingy freeze up".  I've looked around for a while and am pretty sure its a "kernel panic".  It doesn't really happen at any set time, sometimes right after start up, sometimes like an hour later.

I've also seen a few fixes ([http://ubuntuforums.org/showthread.php?t=968792](http://ubuntuforums.org/showthread.php?t=968792)) but I'm not quite sure how to implement them.  If it has anything to do with my wireless card mine is a Intel PRO/Wireless 3945ABG.

I would appreciate any help.  

I'm also aware that this is a fairly common problem and if there is a thread that would help me more please redirect me.

Thanks in advance, and I am very thankful for the incredibly active Ubuntu community.

Siruso

---

### Post by Siruso on 2008-12-04
Hate to double post, just trying to keep this within view.

Siruso

---

### Post by Siruso on 2008-12-04
Man there's a lot of posts in this forum.  I'm already on the third page.  I wonder, is there a better place for me to ask this?

Siruso

---

### Post by Siruso on 2008-12-04
Another bump.  I reinstalled Ubuntu and now it starts fine, but I'm still getting the kernel freeze.  I really hope there's some way to fix it because right now its the only thing keeping me from switching to Ubuntu.

Siruso

P.S  I've tried doing the SysRq way to reboot, but I can never get it to work, so I have to hard reboot it which I'm pretty sure is what caused it to not start properly.  So I'll be staying out of Ubuntu until I figure out a decent way to fix the panic

---

### Post by Siruso on 2008-12-04
Alright, I just read that I'm supposed to download and install linux-backports-modules-intrepid, which might fix my problem.  I have no idea how to do this and I don't want to screw anything up so can anyone tell me how to "install linux-backports-modules-intrepid"?

siruso

---

### Post by tvst on 2008-12-04
You can do it in 1 step using the commandline:

sudo apt-get install linux-backports-modules-intrepid



or in 3 steps using the graphical interface:

1) Go to System > Administration > Synaptics Package Manager

2) Then type "backports" on the quick search box. Click on the checkbox next to linux-backports-modules-intrepid and choose "Mark for installation".

3) Then press "Apply" on the toolbar.

---

### Post by Siruso on 2008-12-04
Sweet thanks I'll try that out.

siruso

---

### Post by solipsist on 2009-08-16
Siruso,

You can also try to upgrade your Kernel.
The default kernel installed on Ubuntu 9.04 is the 2.6.28-11 version 
The solution was to install the latest version of Kernel released for 9.04 but it seems it is not yet available on the repositories (Version 2.6.29-3)

Download these packages thru the terminal:-

# wget -c [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29.3/linux-headers-2.6.29-02062903-generic_2.6.29-02062903_i386.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29.3/linux-headers-2.6.29-02062903-generic_2.6.29-02062903_i386.deb)

# wget -c [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29.3/linux-headers-2.6.29-02062903_2.6.29-02062903_all.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29.3/linux-headers-2.6.29-02062903_2.6.29-02062903_all.deb)

# wget -c [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29.3/linux-image-2.6.29-02062903-generic_2.6.29-02062903_i386.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29.3/linux-image-2.6.29-02062903-generic_2.6.29-02062903_i386.deb)

Then install the downloaded packages using dpkg:

# sudo dpkg -i linux-headers-2.6.29-02062903-generic_2.6.29-02062903_i386.deb linux-headers-2.6.29-02062903_2.6.29-02062903_all.deb linux-image-2.6.29-02062903-generic_2.6.29-02062903_i386.deb

After installation restart the system by choosing new kernel.
Hope this works.

---

