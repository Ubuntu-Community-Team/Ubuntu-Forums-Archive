---
title: "Ubuntu 7.10 take too much to start in my Dell Inspiron 1501"
date: 2007-10-21
forum: Dell  Ubuntu Support
---

### Post by Samanozuke on 2007-10-21
OK, the problem is that I installed Ubuntu 7.10 and when I turn on my pc it take too much to boot. I don't know but I didn't have that problem with ubuntu 7.04.
I heard that the problem is because of the kernel, it's that true?
and, how can i fix that?

---

### Post by Razzoo on 2007-10-22
Hi there. Might be worth checking /etc/usplash.conf and making sure it has the right numbers for xres and yres -- and, if not, changing them.  
Cheers..

---

### Post by hades_6_6_6 on 2007-10-22
I also have the same problem: 
- 3 minutes from GRUB to Session Manager
- no splash-screen during boot
> **Razzoo said:**
> Hi there.  making sure it has the right numbers for xres and yres.
I'm absolute beginner. What this values should be like?

---

### Post by Razzoo on 2007-10-22
I think they should be the same as your normal screen resolution -- e.g. if it's 1440x900, then manually edit /etc/usplash.conf so that yres=900 and xres=1440.
In Ubuntu do that by typing into a Terminal
```
gksudo gedit /etc/usplash.conf
```
Replace any incorrect numbers, SAVE the changed file, then REBOOT.
This is one of several well known bugs.
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/150930]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/150930")
Good luck.

---

### Post by Razzoo on 2007-10-22
I don't want to lead anyone astray -- considering how little I actually know. :)

I installed  xubuntu-7.10-rc-desktop-i386  on both my laptops, and the OS seemed to assign wrong splash screen resolutions both times.

But only the Thinkpad (1024x768 with ATI graphics) suffered prolonged boot-up times without any splash screen -- and that was easily rectified by just editing the /etc/usplash.conf file, and setting
xres=1024
yres=768

The Bug #150930 thread I linked to, has apparent solutions for various machines -- but the problem looks more complicated than I thought it was. :confused:

Wish I could help you more.

---

### Post by Samanozuke on 2007-10-22
OK, I found a solution:

- editing /etc/usplash.conf to 1024x768
- running sudo update-initramfs -u -k `uname -r`

in [https://bugs.launchpad.net/ubuntu/+bug/152643](https://bugs.launchpad.net/ubuntu/+bug/152643)

:-)

---

### Post by hades_6_6_6 on 2007-10-24
> **Samanozuke said:**
> 
- editing /etc/usplash.conf to 1024x768
- running sudo update-initramfs -u -k `uname -r`

My hero:)
worked for me (editing usplash.conf alone didn't the trik)
I need 35'' now to boot (instead of 3'05'') :guitar:

---

### Post by swisscow on 2007-10-24
> **Samanozuke said:**
> OK, I found a solution:

- editing /etc/usplash.conf to 1024x768
- running sudo update-initramfs -u -k `uname -r`

in [https://bugs.launchpad.net/ubuntu/+bug/152643](https://bugs.launchpad.net/ubuntu/+bug/152643)

:-)

What a star - solved my 5 minute black screen boot up.

Many thanks!

---

