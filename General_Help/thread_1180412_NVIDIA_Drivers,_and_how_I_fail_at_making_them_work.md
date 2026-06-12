---
title: "NVIDIA Drivers, and how I fail at making them work"
date: 2009-06-06
forum: General Help
---

### Post by DnDer on 2009-06-06
I'm just going to cross-post in the hopes that more people are looking here than the specific topic boards I've been to.

[Original Thread](http://ubuntuforums.org/showthread.php?t=1177058) where I try to get the drivers working

[Steelmourne's excellent thread](http://ubuntuforums.org/showthread.php?t=1177942) that still doesn't offer me any help, but it works for some people.

And, finally, NPL posted an [alternative method](http://ubuntuforums.org/showthread.php?t=1036788), but I fail to even manage to install his script file, so I can't get past step 3.

Here's my terminal section, showing where I followed the instructions best as I could.
```
eric@Rosencrantz:~$ sudo apt-get remove nvidia-glx-180 nvidia-180-kernel-source nvidia-xconfig nvidia-settings
[sudo] password for eric: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package nvidia-glx-180 is not installed, so not removed
Package nvidia-180-kernel-source is not installed, so not removed
E: Couldn't find package nvidia-xconfig
eric@Rosencrantz:~$ sudo gedit /etc/default/linux-restricted-modules-common
eric@Rosencrantz:~$ sudo apt-get install dkms build-essential make
Reading package lists... Done
Building dependency tree       
Reading state information... Done
dkms is already the newest version.
build-essential is already the newest version.
make is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
eric@Rosencrantz:~$ sudo apt-get install linux-headers-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
eric@Rosencrantz:~$ sh ./installdkms.sh 185.18.14
sh: Can't open ./installdkms.sh
eric@Rosencrantz:~$ cd Desktop
eric@Rosencrantz:~/Desktop$ sh ./installdkms.sh 185.18.14
Checking for kernel-sources for the running kernel
Kernel-sources seem to be installed
Important: You should install the correct Packages
for ALL kernels you are using

Must be root to continue
eric@Rosencrantz:~/Desktop$ su -
Password: 
root@Rosencrantz:~# cd Desktop
-su: cd: Desktop: No such file or directory
root@Rosencrantz:~# sh ./installdkms.sh 185.18.14
sh: Can't open ./installdkms.sh
root@Rosencrantz:~# 

```

(I don't even know how to change the colors o my terminal to make that readable. >_<)

I don't get what I'm doing wrong... and there doesn't seem to be a textbook for Linux (I asked, and got a cop-out answer that Linux is changing all the time. Surely the fundamentals of navigating and operating the system stay the same, despite having new things added all the time). Maybe I'm just too full of fail to even use something as Human-friendly as Ubuntu.

To think, I had a friend who suggested I use something (that I understand to be rated) as advanced as Slack...

Anyone have a few minutes to help the perpetually helpless?

---

### Post by SuperSonic4 on 2009-06-06
```
root@Rosencrantz:~# cd Desktop
-su: cd: Desktop: No such file or directory
```

Since you're using the root account that code will point to /root/Desktop which does not exist. Either

1) cd to /home/eric/Desktop and run the script

2) preface sudo to "eric@Rosencrantz:~/Desktop$ sh ./installdkms.sh 185.18.14" making it ```
sudo sh ./installdkms.sh 185.18.14
```

---

### Post by colau on 2009-06-06
To DnDer.
You are root user now.
Being a regular user cd Desktop.
Can you find your file?

---

### Post by DnDer on 2009-06-06
Supersonic is my hero! Almost home, now. I never understood (till your code explained that dichotomy) that working in terminal as root is the same as having logged off and then logged in as root. I thought because I was running terminal under eric, then I could find the desktop in eric. 

**NEW QUESTION:** npl now recommends to edit the xorg.conf file manually, and to do so using the line "vim /etc/X11/xorg.conf" before rebooting.

I'm still at the prompt before rebooting (after finishing the driver's install), and I get the following error:
```
root@Rosencrantz:~# vim /etc/x11/xorg.conf
The program 'vim' can be found in the following packages:
* vim
* vim-gnome
* vim-tiny
* vim-gtk
* vim-nox
Try: apt-get install <selected package>
bash: vim: command not found
root@Rosencrantz:~# apt-get install vim
[editorial snip]
After this opreation, 26.8MB of additional disk spae will be used.
Do you want to continue [Y/n]? y
Err http://us.archive.ubuntu.com jaunty/main vim-runtime 2:7.2.079-1ubuntu5
  Could not resolve 'us.archive.ubuntu.com'
[editorial snip, 2 more .deb files are mentioned with the same 'resolve' error]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
root@Rosencrantz:~#
```

If I reboot to get those packages... what sort of errors am I looking forward to encountering? I... obviously did not have everything I needed before I booted to the command prompt. 

What should I do? Run the scripts in the next steps from the command line I'm at? Reboot and get-apt those things, and edit my xorg.conf file while in the GUI? I'm bothered about trying something especially while I'm root... That's about the only thing I understand about *nix: "root=dangerous, use only under controlled and specifically instructed circumstances."

---

### Post by colau on 2009-06-06
> **DnDer said:**
> Supersonic is my hero! Almost home, now. I never understood (till your code explained that dichotomy) that working in terminal as root is the same as having logged off and then logged in as root. I thought because I was running terminal under eric, then I could find the desktop in eric. 

**NEW QUESTION:** npl now recommends to edit the xorg.conf file manually, and to do so using the line "vim /etc/X11/xorg.conf" before rebooting.

I'm still at the prompt before rebooting (after finishing the driver's install), and I get the following error:
```
root@Rosencrantz:~# vim /etc/x11/xorg.conf
The program 'vim' can be found in the following packages:
* vim
* vim-gnome
* vim-tiny
* vim-gtk
* vim-nox
Try: apt-get install <selected package>
bash: vim: command not found
root@Rosencrantz:~# apt-get install vim
[editorial snip]
After this opreation, 26.8MB of additional disk spae will be used.
Do you want to continue [Y/n]? y
Err http://us.archive.ubuntu.com jaunty/main vim-runtime 2:7.2.079-1ubuntu5
  Could not resolve 'us.archive.ubuntu.com'
[editorial snip, 2 more .deb files are mentioned with the same 'resolve' error]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
root@Rosencrantz:~#
```

If I reboot to get those packages... what sort of errors am I looking forward to encountering? I... obviously did not have everything I needed before I booted to the command prompt. 

What should I do? Run the scripts in the next steps from the command line I'm at? Reboot and get-apt those things, and edit my xorg.conf file while in the GUI? I'm bothered about trying something especially while I'm root... That's about the only thing I understand about *nix: "root=dangerous, use only under controlled and specifically instructed circumstances."

What happens?;)
```

aptitude update
aptitude install vim-full

```

---

### Post by DnDer on 2009-06-06
The first aptitude command worked. Here's the second:

```
Need to get 9690kB of archives. After unpacking 37.2MB will be used.
Do you want to countinue [Y/n/?]y
Writing extended state information... Done
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main [multiple files to be listed]
  Could not resolve 'us.archive.ubuntu.com'
[repeat 5 more times]
E: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/r/ruby1.8/libruby1.8_1.8.7.72-3+i386.deb:](http://us.archive.ubuntu.com/ubuntu/pool/main/r/ruby1.8/libruby1.8_1.8.7.72-3+i386.deb:) Could not resolve 'us.archive.ubuntu.com'
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Writing extended state information... Done
```

The following were the files that were listed after the jaunty/main prompt (except the 6th one, which was jaunty/universe):

libruby1.8 1.8.7.72-3
tcl8.4 8.4.19-2
vim-gui-common 2:7.2.079-1ubuntu5
vim-runtime 2:7.2.079-1ubuntu5
vim-gnome 2:7.2.079-1ubuntu5
vim-full 2:7.2.079-1ubuntu5

So... it didn't work?

---

### Post by colau on 2009-06-06
> **DnDer said:**
> The first aptitude command worked. Here's the second:

```
Need to get 9690kB of archives. After unpacking 37.2MB will be used.
Do you want to countinue [Y/n/?]y
Writing extended state information... Done
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main [multiple files to be listed]
  Could not resolve 'us.archive.ubuntu.com'
[repeat 5 more times]
E: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/r/ruby1.8/libruby1.8_1.8.7.72-3+i386.deb:](http://us.archive.ubuntu.com/ubuntu/pool/main/r/ruby1.8/libruby1.8_1.8.7.72-3+i386.deb:) Could not resolve 'us.archive.ubuntu.com'
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Writing extended state information... Done
```

The following were the files that were listed after the jaunty/main prompt (except the 6th one, which was jaunty/universe):

libruby1.8 1.8.7.72-3
tcl8.4 8.4.19-2
vim-gui-common 2:7.2.079-1ubuntu5
vim-runtime 2:7.2.079-1ubuntu5
vim-gnome 2:7.2.079-1ubuntu5
vim-full 2:7.2.079-1ubuntu5

So... it didn't work?

Can you post 
```

cat /etc/apt/sources.list

```

---

### Post by DnDer on 2009-06-06
I'm going to assume you don't want the commented section... 

```
deb http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb-src http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb http://security.ubuntu.com/ubuntu jaunty-security universe
deb-src http://security.ubuntu.com/ubuntu jaunty-security universe
deb http://security.ubuntu.com/ubuntu jaunty-security multiverse
deb-src http://security.ubuntu.com/ubuntu jaunty-security multiverse
root@Rosencrantz:~#
```

Sorry that took so long. I went out for food.

This is all still in the "safe mode, command prompt" (I need to re-read the post for his exact words) that I was originally told not to reboot from till my xorg file was edited. Or do I need to be doing this in terminal, under the GUI?

---

### Post by SuperSonic4 on 2009-06-07
Vim is a cli text editor, it's fully featured but for editing xorg.conf it would be easier to use nano imo which is less feature-rich but easier to understand (plus it's installed already). Assuming you're logged in as root (if you're not preface each command with sudo) - if you're editing xorg.conf then it's better to use a virtual console with no GUI. You can press ctrl+alt+F2 to get a terminal.

Kill gdm so there is no GUI
```
/etc/init.d/gdm stop
```

Back up xorg.conf in case anything goes wrong - if it does you can restore the backup
```
cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

Edit xorg.conf with nano (Press ctrl+X to exit and y to save)
```
nano /etc/xorg.conf
```

Should anything go wrong then you can use your backup to replace it
```
mv /etc/X11/xorg.conf.bak /etc/X11/xorg.conf
```

-------------------------------------

However it seems like you're jumping through hoops. What nvidia card do you have? Use ```
lspci | grep VGA
``` and post the output.

If necessary you can always get drivers from the nvidia site which seems much easier

---

### Post by DnDer on 2009-06-07
**Output:**
02:00.0 VGA compatible controller: nVidia Corporation GeForce 8300 (rev a2)

And nano worked wonderfully! Now, I can reboot and continue with the directions. I'll continue to post progress here, and let you know how it went.

**UPDATE**
```
root@Rosencrantz:/home/eric/Desktop# dkms status
nvidia, 173.14.16, 2.6.28-11-generic, i686: built (original_module exists)
nvidia, 185.18.14, 2.6.28-11-generic, i686: installed (original_module exists)
root@Rosencrantz:/home/eric/Desktop# shutdown -r 0
```

And I'm still stuck on the crap resolution. And I'm still getting the error about not using the NVIDIA X driver. Which instruction did I fail to follow properly? =(

---

### Post by DnDer on 2009-06-08
A question for Steelmourn, npl and anyone else who has attempted to help me this last week.

Other people seem to have followed the instructions and met with success. Something I didn't pay attention to, until someone brought it to my attention, is that widescreen monitors, despite being prolific, are still not the standard.

Could the problem be not my graphics driver, but rather my monitor that the driver is trying to fill? Or is there still something wrong with the drivers that I get these errors?

---

