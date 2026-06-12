---
title: "Successfully Installing Ubuntu 7.10 on a Dell Inspiron 1100 (8.04 was a no go)"
date: 2008-06-08
forum: Dell Ubuntu Support (CLOSED)
---

### Post by steppedup on 2008-06-08
Hi all, 

Here is an "A to Z" installation Ubuntu 7.10 Gutsy Gibbon on a Dell Inspiron 1100 laptop that originally had an A6 BIOS - and still has 256 MB of RAM. Tried 8.04 and it was not a fun experience.

[COLOR="red"][http://docs.google.com/Doc?id=d2frfsz_72ds254kf6](http://docs.google.com/Doc?id=d2frfsz_72ds254kf6)[/COLOR]

Anyway, the original goal was for my non-techie fiancee to use her slagged off XP laptop to flawlessly to access all Ubuntu apps, some Windows Apps like Internet Explorer - all while in a Mac OS X skinning of the laptop's OS.

Covered are: 
[LIST]
[*]All of the multiple fixes for the graphics drivers/ black screen issue have been compiled here - and and logically listed so as to maximize installation efficiency.
[/LIST]
[LIST]
[*]A more complete walk-through of the BIOS fixes needed to upgrade from A6 to A22 to A32.
[/LIST]
[LIST]
[*]Walk-through of how to clean out the laptop so it stops overheating. Very relevant to the Dell Inspiron owner trying to install Ubuntu. If they think their laptop is overheating because of the OS...well, we just lost another customer.
[/LIST]
[LIST]
[*]Brief walk-through of the installation with the alternative CD for i386 that was used - including CD download, burning, checking CD quality - all focused at the lesser experienced user.
[/LIST]

You might argue the following really aren't part of installation, but I disagree. Unless we can get the box set up so that our users can do whatever they can do with a Mac or a Windows box, then the installation is not over. 

[LIST]
[*]How to tweak Ubuntu so it's moving along nicely.
[/LIST]
[LIST]
[*]How to get that magical OSX look. Quickly. Easily.
[/LIST]
[LIST]
[*]How to get the major apps that are needed on the net today.
[/LIST]

So did it pass the test? What's the phrase? Keep the wife happy, keep your life happy? 

My life is very happy....

Hopefully this will help yours be happy too: 
[COLOR="Red"]
[http://docs.google.com/Doc?id=d2frfsz_72ds254kf6](http://docs.google.com/Doc?id=d2frfsz_72ds254kf6)[/COLOR]

Cheers,

Stepped It Up

---

### Post by Aeroangel on 2008-06-15
Thank you so much for this guide. I tried upgrading to 8.04 but that made this computer sooo slow :mad:

But anyway just went to reinstalling 7.10, and I wouldn't have been able to without your guide. :KS

---

### Post by jbrax on 2008-10-20
Ubuntu-8.04 is OK with Dell Inspiron 1100 after these steps:  

1. Upgrade your laptops bios to A32
2. Change the video memory from 1MB to 8MB in BIOS setup
3. Install Ubuntu-8.04 
4. Add sync-lines and resolution to /etc/X11/xorg.conf to get 1024x768 resolution
**5. Change splash to nosplash, line 89 in /boot/grub/menu.lst** 
   This last one fixes the "Blank screen after every other boot" -error. If you have already updated the kernel you have to change splash to nosplash in that kernels line in menu.lts too.

For more detals see my comment at [http://ubuntuforums.org/showthread.php?t=819541](http://ubuntuforums.org/showthread.php?t=819541)

---

### Post by Phosphoric on 2008-11-25
Great howto, worked a treat for me. :KS

Next job is to get my wireless card working properly.:(

---

### Post by sTpny on 2009-02-04
8.04 seems to work fine for me so far also.  Don't let the kernel upgrade though. The new Kernel causes all sorts of trouble for me.  DRDY ERR's and GRUB errors; terrible, so keep the old kernel, which strangely seems to work better.??. 

Anyhow, I upgraded the bios, increased the video memory, and changed splash to nosplash in menu.lst, but then I also added vga=791 to the menu.lst, and that gives me 1024x768 without needing to add the sync lines to xorg,conf. 

Adding the vga=791 works to fix the screen for many distros on this and other laptops, even during the install, so I thought I'd mention it, but most people will want to add sync lines to xorg, because doing it this way, there are no other resolutions. I think what it does is to try forcing a resolution of 1024x786x16, but I'm not really sure. I just found it and found it useful, so I thought I'd mention it. 

Also, is 7.10 noticeably faster? It was a real pain to get a distro on here. is it worth the effort to downgrade to 7.10?

---

