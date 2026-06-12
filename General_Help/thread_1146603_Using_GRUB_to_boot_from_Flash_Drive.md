---
title: "Using GRUB to boot from Flash Drive"
date: 2009-05-02
forum: General Help
---

### Post by papasmurf6768 on 2009-05-02
Hey yall.  I recently installed Kubuntu 9.04 on my Mimobot Memory stick, 2GB.  I was having trouble booting from it on my computer, and I know it's not the flash drive or the computer, because I booted it on a different computer, and I can boot from other flash drives.  But that's not the point. 
I'm currently dual-booting Ubuntu 9.04 and Windows XP.  When I plugged in my flash drive and booted up the comp., I was greeted by a blank screen.  So what I was trying to do was start the computer so I can see GRUB, plug in the flash drive, and then choose the correct option.  (In this case, Kubuntu 9.04.)  I've tried many things I just can't seem to get the settings right in my /boot/grub/menu.lst .  I thought I got it, but when I tried to boot, I got, "Cannot mount the partition."  What I need are the correct settings to put in the list. 
Some extra info.-  My flash drive has 1 partition, and in my GParted it's sdb.

Here's my current setting I have:

title           Kubuntu 9.04
  root            (hd0,0)
  kernel          /boot/isolinux/linux24 root=/dev/sdb1 ro lang=us toram noeject frugal
  initrd          /boot/isolinux/minirt24.gz
  boot
  EOF

No idea if that's right.  I copy and pasted something, and edited it a little.  If you need any more info, please ask for it, and I'll give it.  Thamks in advance, and sorry for the long post.

---

### Post by papasmurf6768 on 2009-05-02
Nevermind guys, I got it.  I'll tell what I did so people no.  I did it the easy way, and the noob way, but it worked.  : )

1) Boot Windows, and put in your Kubuntu Live CD, or Flash Drive.
*If you put in your flash drive, open it up and run wubi.exe
2)Click Install Kubuntu, or whatever it says.  Click the Help Me Install Kubuntu Button, and then next.
3)Install the software

4)Reboot the computer, this time booting Ubuntu.
5)Open up a terminal, and type

sudo gedit /boot/grub.menu.lst

Go to the bottom of the page, where it says Windows XP...
6)Delete what it says next to title, and type:
Windows XP/Kubuntu x.xx      (x represents the version you have.  I have 9.04 so mine says Windows XP/Kubuntu 9.04).

7)Save the file by clicking save, and your all done!

Now when you boot your computer, it'll say Windows XP/Kubuntu x.xx

Select that, and you'll get the option Windows or Kubuntu?  Choose which one you want.

I know this isn't the real way to do it, but it works and I'm happy with it for now.  I'd still appreciate an alternate method to get both Kubuntu and Windows on the first menu, so if you have some spare time, go for it.  Thanks people, and good luck.

---

