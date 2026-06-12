---
title: "Burg + Plymouth splash problem"
date: 2010-10-17
forum: Desktop Environments
---

### Post by iaiajo on 2010-10-17
Hi, this is my first post here, hope i can explain the best i could about this little problem i'm having right now. :P

Well the problem is this, when i try to change the plymouth i do all that is wrote in this link: [http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml](http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml) ... and when my pc is in the restart/shutdown process i can see the new plymouth working but after my pc restart and load the burg theme all i get after that is again an ugly "ubuntu 10.10" and the dots loading (not even the default plymouth). So in resume, i don't know if the burg is changing the settings every time the pc restart after the changes i make. (just in case, before i had burg the plymouth was working as usually) and i was using the open source ati drivers, now im using the fgrlx one.  Thanks for any info and sorry about my english, it's not my native language :P

---

### Post by stinkeye on 2010-10-17
If your using burg you should be using
gksu gedit /etc/default/**burg**
not
gksu gedit /etc/default/**grub**

and when finished use
sudo update-**burg**

---

### Post by iaiajo on 2010-10-17
> **stinkeye said:**
> If your using burg you should be using
gksu gedit /etc/default/**burg**
not
gksu gedit /etc/default/**grub**

and when finished use
sudo update-**burg**
hey thanks!, going to give it a try :)

---

### Post by iaiajo on 2010-10-17
yeah!! i can confirm that is working as you suggest me to do it, thanks alot man.

---

### Post by crazups on 2011-03-16
What did you change in Burg to solve this.  I have the same problem and pointed theme to my plymouth theme directory and got the ugly default grub theme (black/white text only)

Grub_Theme "/lib/plymouth/themes/spinfinity" didn't work

---

### Post by elnetotaca on 2011-05-30
did you fixed it?


its really simple, just type on your terminal;

gksu gedit /etc/default/burg

look for this line;
GRUB_CMDLINE_LINUX_DEFAULT

and make it look like;

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset video=uvesafb:mode_option=1280x1024-24,mtrr=3,scroll=ywrap"

then look for;
#GRUB_GFXMODE=640x480


change it to;
GRUB_GFXMODE=1280x1024

save it

then in your terminal;
echo FRAMEBUFFER=y | sudo tee /etc/initramfs-tools/conf.d/splash
sudo update-burg
sudo update-initramfs -u

restart
and you are donde!



Note: before you do anything with your screen resolution, go to menu>>system>>preferences>>Monitors
and you use that resolution for your /etc/default/burg file.

---

### Post by Pilch1989 on 2011-06-07
> **elnetotaca said:**
> did you fixed it?


its really simple, just type on your terminal;

gksu gedit /etc/default/burg

look for this line;
GRUB_CMDLINE_LINUX_DEFAULT

and make it look like;

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset video=uvesafb:mode_option=1280x1024-24,mtrr=3,scroll=ywrap"

then look for;
#GRUB_GFXMODE=640x480


change it to;
GRUB_GFXMODE=1280x1024

save it

then in your terminal;
echo FRAMEBUFFER=y | sudo tee /etc/initramfs-tools/conf.d/splash
sudo update-burg
sudo update-initramfs -u

restart
and you are donde!



Note: before you do anything with your screen resolution, go to menu>>system>>preferences>>Monitors
and you use that resolution for your /etc/default/burg file.

I just followed these instructions to try and get my splash screen working with burg. When my computer loaded up burg worked and so did the splash screen, however my computer would not let me log in to unity. It said that my hardware did not meet the specifications, and so I used 'Boot-repair' to restore grub and now I can boot into unity again. 

Does any one know what the problem is here, and how I can get burg working with the ubuntu splash screen?

---

### Post by mihai_n on 2011-07-03
hello elnetotaca, it's working for me thanks

---

### Post by elnetotaca on 2011-07-06
> **Pilch1989 said:**
> I just followed these instructions to try and get my splash screen working with burg. When my computer loaded up burg worked and so did the splash screen, however my computer would not let me log in to unity. It said that my hardware did not meet the specifications, and so I used 'Boot-repair' to restore grub and now I can boot into unity again. 

Does any one know what the problem is here, and how I can get burg working with the ubuntu splash screen?

well, if you have Ubuntu 11.04 burg will not work well.
that is the only one thing I can't get to work.

maybe in the next couple month someone will come up with a workaround.

---

### Post by elnetotaca on 2011-07-06
NICE! good job TEAM! pass it on!

---

