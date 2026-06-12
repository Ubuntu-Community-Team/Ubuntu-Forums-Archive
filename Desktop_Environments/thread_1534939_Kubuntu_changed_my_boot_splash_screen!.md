---
title: "Kubuntu changed my boot splash screen!"
date: 2010-07-20
forum: Desktop Environments
---

### Post by NewtoLinux13 on 2010-07-20
Hi Everybody.

I recently installed my first distro, Gnome Ubuntu Linux 10.04 via WUBI  dual-booting alongside my Windows.

I decided to try the other desktop environments. So I installed  Kubuntu-Desktop (KDE) and Xubuntu-Desktop (XFCE) using Synaptic Package  Manager.

However, Kubuntu KDE changed the boot splash screen into a from the  default Ubuntu one, to the Kubuntu one.
Also Xubuntu XFCE changed the log-in screen to the Xubuntu one.

I DO NOT want these changes. I just wanted Normal Ubuntu-branded Ubuntu  Linux with the option of logging in into the desktop environment of my  choice.

Can anyone help me?

Please note: I am completely new to Linux.

PS. I am willing to reinstall Ubuntu if I have to.

---

### Post by MadCookie on 2010-07-20
When you install in example, kubuntu-desktop, you install the whole kubuntu system, which means that it will also change your boot splash, as well as it may have changed your login screen (but I guess it asks before it does that).

Try to run the command below in the terminal (you can just copy and paste), and reboot. This will set the plymouth (boot animation) theme to the default one in Ubuntu. If you want to change the plyamouth theme to kubuntu's or xubunt's, just replace "ubuntu-logo" with "kubuntu-logo" or "xubuntu-logo".

```
sudo plymouth-set-default-theme ubuntu-logo --rebuild-initrd
```

If you get any errors, or if the plymouth theme doesn't change please tell what happens :P

---

### Post by NewtoLinux13 on 2010-07-21
Thank for your help.
I tried writing in the terminal (I copied and pasted your command) 
Code:
sudo plymouth-set-default-theme ubuntu-logo --rebuild-initrd
But I then I got an error message:

sudo: plymouth-set-default-theme: command not found

Where did I go wrong?

---

### Post by NewtoLinux13 on 2010-07-21
Hello.

I searched around about plymouth and found this post ([http://ubuntuforums.org/showthread.php?t=1440223](http://ubuntuforums.org/showthread.php?t=1440223)) that says that the plymouth command changed or something.
Anyway I wrote a command I found in the post in the terminal:

sudo update-alternatives --config default.plymouth

It put up a list which enabled me to choose a theme. I chose the Ubuntu default, restarted and... it worked!

Thanks for all your help.

Though I still have a Xubuntu logon screen, but I don't really care since I might uninstall Xubuntu since I don't think I really need XFCE.

Thanks again.

---

### Post by NewtoLinux13 on 2010-07-21
I searched around and found the solution to uninstalling the Xubuntu display manager logon screen that automatically came with my Xubuntu installation.
I simply uninstalled xubuntu-gdm-theme using Synaptic Package Manager.
So I guess I fixed all my problems, and am keeping KDE and XFCE.
So now I have Ubuntu with the ability to login in to the desktop of my choice. :)

---

### Post by NewtoLinux13 on 2010-07-21
Also, Thanks again MadCookie, I couldn't have done it without you. :)

---

