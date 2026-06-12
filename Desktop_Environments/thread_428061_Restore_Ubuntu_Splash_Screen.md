---
title: "Restore Ubuntu Splash Screen"
date: 2007-04-29
forum: Desktop Environments
---

### Post by Neuralgia on 2007-04-29
I decided to install KDE and Xfce.

Even though I chose to use gdm as default, my boot screnn now uses Kubuntu (blue) logo.

I tried this first:

> $sudo update-alternatives --config usplash-artwork.so

but I get this mssg, after choosing #1

> $sudo update-alternatives --config usplash-artwork.so

There are 3 alternatives which provide `usplash-artwork.so'.

  Selection    Alternative
-----------------------------------------------
*         1    /usr/lib/usplash/usplash-theme-ubuntu.so
 +        2    /usr/lib/usplash/usplash-theme-kubuntu.so
          3    /usr/lib/usplash/usplash-theme-xubuntu.so

Press enter to keep the default[*], or type selection number: 1
Using `/usr/lib/usplash/usplash-theme-ubuntu.so' to provide `usplash-artwork.so'.
update-alternatives: unable to make /etc/alternatives/usplash-artwork.so.dpkg-tmp a symlink to /usr/lib/usplash/usplash-theme-ubuntu.so: Permission denied
danielcifuentes@danielcifuentes:~$ 


Then googled a little more, and tried this:

> $  sudo update-alternatives --config usplash-artwork.so

There are 3 alternatives which provide `usplash-artwork.so'.

  Selection    Alternative
-----------------------------------------------
*         1    /usr/lib/usplash/usplash-theme-ubuntu.so
 +        2    /usr/lib/usplash/usplash-theme-kubuntu.so
          3    /usr/lib/usplash/usplash-theme-xubuntu.so

Press enter to keep the default[*], or type selection number: 1
Using `/usr/lib/usplash/usplash-theme-ubuntu.so' to provide `usplash-artwork.so'.


The same page told me to do this:

> ~$  sudo dpkg-reconfigure linux-image-`uname -r`Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.20-15-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.20-15.27 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.20-15.27 was configured last, according to dpkg)
Running postinst hook script /sbin/update-grub.
Your /etc/kernel-img.conf needs to be updated. Read grub's NEWS.Debian[1]
file and follow its instructions.

 1. /usr/share/doc/grub/NEWS.Debian.gz


You shouldn't call /sbin/update-grub. Please call /usr/sbin/update-grub instead!

Searching for GRUB installation directory ... found: /boot/grub
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.20-15-generic
Found kernel: /boot/vmlinuz-2.6.17-11-generic
Found kernel: /boot/vmlinuz-2.6.17-10-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done


No errors, but didn't help... In fact, now I DON'T HAVE A SCREEN AT ALL.

Then, looking a little more, I tried this:

> $ sudo ln -sf /usr/lib/usplash/usplash-default.so /usr/lib/usplash/usplash-artwork.so
              $ sudo dpkg-reconfigure linux-image-$(uname -r)

And nothing happened.

Any ideas?

---

### Post by Kaptain Chaos on 2007-04-30
[B]Hello,
Try this:

Open up a terminal and type the following code:
[/B]
$ sudo update-alternatives --config usplash-artwork.so

**You'll get something like:**

There are 2 alternatives which provide `usplash-artwork.so'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/lib/usplash/usplash-theme-ubuntu.so
*+        2    /usr/lib/usplash/usplash-theme-kubuntu.so

Press enter to keep the default[*], or type selection number: 1
Using `/usr/lib/usplash/usplash-theme-ubuntu.so' to provide `usplash-artwork.so'


**choose the ubuntu usplash and then type the following code:**

$ sudo dpkg-reconfigure linux-image-`uname -r`

[B]Of course you can just copy and paste to make sure your spelling and syntax is correct.

Taken from another thread contribution by Zappe - it works for me.[/B]

---

### Post by Neuralgia on 2007-04-30
that was option #2 on my post.

Nothing is working. :(

---

### Post by linuxeiro on 2007-04-30
I have the same problem with usplash every time I install kubuntu-desktop in ubuntu.

I solved it by completely unistalling every usplash package (both kubuntu and ubuntu) with synaptic. Once it's done, I install ubuntu usplash with synaptic. It works just fine. No need to configure anything. It has only one minor problem, which is that synaptic will consider that you no longer have the kubuntu-desktop metapackage (no kde program but usplash will be uninstalled, though).

---

### Post by Neuralgia on 2007-04-30
didn't work :(

but I have a "new clue"

when I see text when loading and rebooting, I get a messg saying something like this

> usplash: no 1280x1024 image

that might be the problem... the question is, how do I solve that?

---

### Post by Kaptain Chaos on 2007-04-30
Hello again,
You may want to look into this page:
[https://help.ubuntu.com/community/USplashCustomizationHowto]("https://help.ubuntu.com/community/USplashCustomizationHowto")

Not sure if this will help.
I know it talks about Edgy and Dapper but customising the size of the usplash screen is towards the end of the page and requires hand coding grub. I remember doing this with Dapper but haven't needed to since.


One other thing you may want to try is to use aptitude to reinstall ubuntu:

> sudo aptitude update
then
> sudo aptitude install ubuntu-desktop
Using aptitude ensures all dependencies are checked and installed and should update your grub settings as part of the process.

Failing that, take a look at [http://www.psychocats.net/ubuntu/index]("http://www.psychocats.net/ubuntu/index") or [http://ubuntuguide.org/wiki/Ubuntu:Feisty]("http://ubuntuguide.org/wiki/Ubuntu:Feisty"), there's a lot of useful information  on both sites.

As a **last** resort, if you have enough hard drive space, you could create a separate /home partition following Psychocats instructions (just make sure that if other people use the pc their /home folders are copied to the new partition first and that everything works). Then use the live Feisty CD to format your your / (root) partition and do a fresh reinstall of ubuntu telling it where your new /home partition is - but not formating it obviously!

I'm sure you've already thought of this.

Sorry I can't be of more help.

---

### Post by Neuralgia on 2007-05-01
you what&#347; weird?

**it worked perfectlly on my desktop (which I also upgraded from edgy to feisty, and is also a Dell).**

On my laptop is just impossible.

I decided to remove my ubuntu OS, and reinstall it.

Obviously not because of this, but becasue after the upgrade I lost somethings, and I wonder if with a FULL brand new install I'll solve this (for example, Beryl worked like a charm, and now I jus see the white screen everyone complaints about).

Neu

---

### Post by jaybirdone on 2007-05-15
I had the problem with boot splash screen and restart splash screen.

open terminal
sudo nautilus
go to /usr/lib/usplash/

find file usplash-artwork.so        and see if the link is broken.
if the link is broken, delete file.

right click on the file usplash-theme-ubuntu.so   and make link.

rename the new link    usplash-artwork.so 

reboot and see if that works for you.  It did for me.

---

### Post by samstar on 2007-05-18
Hi,

Maybe this'll help.  There's a file called /etc/usplash.conf or somesuch.  Just look for a usplash file in your /etc directory.  Change the resolution in the file to something that usplash may support, like 1024x768, or 800x600.  Then rebuild the initrd.  This will only affect your bootsplash, not your desktop.

Hope this helps,
Sam

---

### Post by razeshkale on 2007-06-29
I was trying to change Ubuntu Usplash to Blue,
That mess my Festy 7.04 
Now i m getting some checking files for  booting....etc script running on one ubuntu

is there any way to change it back to normal one?
Cheers

---

### Post by munchy on 2008-01-23
The *buntu usplash screens packages are called:
[B]
usplash-theme-ubuntu
xubuntu-artwork-usplash
kubuntu-artwork-usplash[/B]

you get the idea...just search synaptic for **usplash**

Remove the ones you don't want to use and reinstall the one you want to keep.

I had installed then removed KDE but was still left with the Kubuntu usplash. Removing **kubuntu-artwork-usplash** got me back to the Ubuntu usplash.

You could also try installing **startupmanager** if you want to manually change your usplash screen.

---

