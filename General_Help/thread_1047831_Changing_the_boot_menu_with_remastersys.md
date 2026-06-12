---
title: "Changing the boot menu with remastersys"
date: 2009-01-22
forum: General Help
---

### Post by cschaaf on 2009-01-22
Hi all

I was able to create a LiveCD of my custom Ubuntu installation and I have a question. Can I change the boot menu?

Currently, when my LiveCD boots, you have to enter 'live' or press enter to boot into LiveCD mode. Is there a way to force it into Live mode every time?

Also, my iso was very large even though I didn't add much of anything to the original install. I added the remastersys, put 3 bookmarks in Firefox, and installed Flash. Left like that, the iso was too large for a CD.

I had to uninstall just about every application that it would let me uninstall for it to fit. I was hoping to add some troubleshooting tools (virus, adware, etc), but I won't have room. Is there something I am missing?

Thanks!

---

### Post by grndslm on 2009-01-22
You don't have to hit enter... if you let it sit there for 20~30 seconds, it automatically boots into livecd mode.

I'm assuming you used 8.10, which is already at almost 700 MB, which is the size of a regular CD, and I'm sure flash isn't small since it's not open source.

You're not missing anything other than realizing you can install a lot more packages, upgrade all the packages that are on the cd, take all your desktop customizations like .gnome .mozilla .compiz or whatever and copy them to /etc/skel and then the livecd user will use those settings as well.  Use fusion-icon and make sure to set it to metacity before copying to /etc/skel otherwise the livedvd won't work with compiz.

... then you can install that huge ISO on a DVD.

---

### Post by cschaaf on 2009-01-23
Thanks for the reply, grndslm.

The timeout is nice. Is there a way to change the timeout length to 1 second or something?

Yes, I am using 8.10.

The DVD would be great, but it won't work for my needs.

---

### Post by grndslm on 2009-01-23
Yes, seems like you're still using isolinux, so edit the end of the file...
/etc/remastersys/isolinux/isolinux.cfg.hardyandlater

Change the 300 to 10 (it counts in tenths of a second).  And hopefully you're already familiar with sudo!

---

### Post by cschaaf on 2009-01-23
Unfortunately, I am not familiar with sudo. I tried to read up on it, but am not having much luck.

I only have 1 user 'Tech'. Here are some results I get:
tech@tech-desktop:~$ visudo
visudo: /etc/sudoers: Permission denied


tech@tech-desktop:~$ sudo /etc/remastersys/isolinux/isolinux.cfg.hardyandlater
[sudo] password for tech: 
/etc/remastersys/isolinux/isolinux.cfg.hardyandlater: 1: DEFAULT: not found
/etc/remastersys/isolinux/isolinux.cfg.hardyandlater: 2: LABEL: not found
....
/etc/remastersys/isolinux/isolinux.cfg.hardyandlater: 24: TIMEOUT: not found
/etc/remastersys/isolinux/isolinux.cfg.hardyandlater: 25: PROMPT: not found

Can you point me in the right direction?

Thanks

---

### Post by grndslm on 2009-01-25
Sorry it took me so long to reply...

In the terminal, type this:

sudo nano /etc/remastersys/isolinux/isolinux.cfg.hardyandlater 

CHANGE: Timeout variable from 300 to 10 or 20

SAVE (Ctrl + X)

Look all around the /etc/remastsys/ folder (using the commands cd, ls, less, & finally "sudo nano" when you discover something you need/want to edit) and check out settings and how the script works.  There's a guide somewhere (easy to find if you search) that explains everything the script does.

---

### Post by cschaaf on 2009-01-27
Awesome, that worked!

Thanks so much for your help, grndslm!

Arrrgh, it is JUST too big to fit on a CD. It is 725,896KB. 

Is there anything I can delete to get it under? Text files? Can I uninstall Remastersys on the new image before I burn it?

---

