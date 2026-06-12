---
title: "how do i get rid the the gui?"
date: 2010-02-24
forum: Desktop Environments
---

### Post by amityak on 2010-02-24
hey there

i just installed linux on an old laptop which will be serving as a ssh server to keep my files while im on the roads, and to make experiment on a lamp server, so basically a fat gui is just eating up resources ... i dont need it, so i apt-get remove gdm gnome gnome-* 'ed everything out, but still when i boot it gets into a graphical resolution and shows an error message , something about the graphics. 
while that, i can acess over ssh from another computer, so i guess i could also leave it this way, but its a little bit retarted, i dont want any graphical or unneccesary process to consume resources.


any tips ?

thank you all, Amit.

---

### Post by MooPi on 2010-02-24
Not so much a way to get rid of the gui but to bypass at boot. I don't use gdm but remember having an option to start an x console session. Another solution is to just install the server edition. If you don't want to do that you can enter into terminal ```
ctrl+alt+F1
``` to leave the gui for command line.

---

### Post by wojox on 2010-02-24
Download the [MinimalCD]("https://help.ubuntu.com/community/Installation/MinimalCD") and at the BOOT: prompt type install and when taskel comes up only choose LAMP Server.

---

### Post by Hero of Time on 2010-02-25
Remove xserver-xorg and all related packages. You could have also just picked the server install ISO and install Ubuntu Server. That doesn't install GUI either.

---

### Post by NefariousNobo on 2010-02-25
Presuming you've already installed Ubuntu, remove Xorg. In addition, you'll probably want to remove Gnome (if you want no GUI, Gnome will waste space, and without Xorg it won't run anyway) and probably even the GDM (Terminal login). It would make more sense to install Debian (in my opinion) for this, as Ubuntu is generally more bloated and slower than Debian, and Debian will allow you more customization, which is perfect for what you are trying to do.

---

