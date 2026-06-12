---
title: "Blank/Black screen with cursor after logon"
date: 2009-04-27
forum: General Help
---

### Post by Xzinum on 2009-04-27
Hi there,

I recently upgraded to Jaunty. I was having the same exact errors when i upgraded from Intrepid. Today, i made a fresh install and i'm still getting suck at the same spot. 

Since the upgrade I haven't been able to get past the log in screen.

I get to the login screen, i can hear the little sound, enter my credentials, and then nothing. I get a cursor and a black screen and that's it.

I've run the recovery to fix possible graphics problems, no solution found.
I've set my xorg.conf to load the vesa driver (i'm using an old graphics card, GeForce 5200FX) and lowered my screen resolution to 1024x768 as the highest resolution possible and still get nothing.

Looking at the syslog, i get the two folling gdm warnings:

gdm[3225]: Warning: using default salt value (undefined in ~/.ecryptsrc)
and
console-kit-daemon[2909]: WARNING: Couldn't read /proc/2908/environ: Failed to open file '/proc/2908/environ': No such file or directory

Can anybody help?

---

### Post by sv1cdn on 2009-04-27
Simple idea, while you start your computer, why don't you select a kernel with recovery option? You can try Fix X server option or others from the menu that pops up!

---

### Post by Xzinum on 2009-04-27
> **sv1cdn said:**
> Simple idea, while you start your computer, why don't you select a kernel with recovery option? You can try Fix X server option or others from the menu that pops up!

As stated in the OP, it does nothing to solve the problem.

I've also tried the dpkg option and yet nothing seems to have fixed anything.

---

### Post by Xzinum on 2009-04-28
Anybody?

---

### Post by Som1else on 2009-04-28
I am having the same problem. I will try the other Kernels

---

### Post by errigalmarten on 2009-04-28
I had the same issue with my laptop on a fresh install of Ubuntu 8.10. I removed the compiz core and package through the command line, and that let me get in.

You've got to boot into the command line interface or something.. I can't remember all the details. If I can pull anything else up, I'll edit this post.

---

### Post by vegetarianshrimp on 2009-04-28
at the login screen, press Ctrl+Alt+F1. login via the terminal. then do this command: It will reconfigure X automatically
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Then run
```
sudo reboot
```
try to login the regular graphical way, and if it still doesn't work, try this: It will take you through a manual process of reconfiguring X.
```
sudo dpkg-reconfigure xserver-xorg
```

then run sudo reboot.

If neither of them works, try them again. When this happened to me, I had to repeat the second one multiple times.

---

### Post by Xzinum on 2009-04-29
> **errigalmarten said:**
> I had the same issue with my laptop on a fresh install of Ubuntu 8.10. I removed the compiz core and package through the command line, and that let me get in.

You've got to boot into the command line interface or something.. I can't remember all the details. If I can pull anything else up, I'll edit this post.

The more i was playing with it, the more i thought it had something to do with my old install since i kept my home folder. I purged everything related to compiz.



> **vegetarianshrimp said:**
> at the login screen, press Ctrl+Alt+F1. login via the terminal. then do this command: It will reconfigure X automatically
```
sudo dpkg-reconfigure -phigh xserver-xorg
```Then run
```
sudo reboot
```try to login the regular graphical way, and if it still doesn't work, try this: It will take you through a manual process of reconfiguring X.
```
sudo dpkg-reconfigure xserver-xorg
```then run sudo reboot.

If neither of them works, try them again. When this happened to me, I had to repeat the second one multiple times.

I'll keep trying this, although my xorg.conf was default to start with.

I'll post if something happens.

---

### Post by Xzinum on 2009-04-29
Well, seems like nothing helps so far. 

Compiz is gone. I swapped out the video card. I've reconfigured xserver-xorg with and without framebuffer. With framebuffer it gives me some errors about my screen not having a useable configuration before i actually get to the log on screen.

SO, the only way to be able to get to the desktop is by selecting the Gnome Failsafe session. That works fine, so i figure it has something to do with user scripts. Trouble is, i don't know where to start to look.

---

### Post by prestonFromMaine on 2009-04-30
I'm having the same problem. I'm using 8.10 . My screen is black after the ubuntu loadbar but I can move the cursor. I tried adding the vesa driver, fixing any broken packages, trying in every kernel from the boot menu. My computer was running fine so I'm confused. I'm a noob so any help would be apprietiated.

---

### Post by abjt on 2009-05-03
Same problem here... on Jaunty. Can log in via recovery mode but otherwise gets to blank screen and hangs. Sometimes I can hear sound and move the mouse cursor.

Also, although my terminal doesn't work, I can connect to the server via samba or mail etc.

quite frustrated.

---

