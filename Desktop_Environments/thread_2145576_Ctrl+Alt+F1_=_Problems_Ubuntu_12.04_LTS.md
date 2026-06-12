---
title: "Ctrl+Alt+F1 = Problems Ubuntu 12.04 LTS"
date: 2013-05-15
forum: Desktop Environments
---

### Post by Purple Narwhal on 2013-05-15
Hey all! I've been using Ubuntu 12.04 LTS for almost a month now and I love it! I wanted to start playing some old Steam games on it, but I have out of date drivers, so I get an error message at Steam's launch. I am using a GeForce 6200. To update my drivers, I went to the nVidia website and got the latest drivers for my system. The only way I could get them was as a .run file. I executed them in terminal as described on the Ubuntu website and got error messages about the X environment and such. I learned that I had to use Ctrl + Alt + F1 to go to a command line and exit the GUI. When I pressed those keys, the screen flickered and had lines all over it. I couldn't do anything except Ctrl + Alt + F7. That took me back to the desktop GUI, but the background had the same lines from the "command line" screen. It stayed like that until I did a reboot. I tried updating everything, no help. I had no programs running. I also tried the terminal command "sudo service lightdm stop" didn't help, same lines on the screen.

So, any ides on how to fix it? Thanks!

---

### Post by papibe on 2013-05-15
Hi Purple Narwhal. Welcome to the forums ):P

I'd recommend uninstalling that driver, and following these [instructions]("https://wiki.ubuntu.com/Valve") to install the proper Nvidia driver (310-experimental).

Regards.

---

### Post by Purple Narwhal on 2013-05-16
Thanks for replying. Unfortunately, my system says it it not using any proprietary drivers when I go to additional drivers.

What can I do to fix this? Thanks!

---

### Post by papibe on 2013-05-16
Let's do it manually then.

Make sure you removed the one you installed from the site:
```
sudo NVIDIA-Linux-xxx-xxx.xx.run --uninstall
```
Replace "NVIDIA-Linux-xxx-xxx.xx.run" with the actual name of the script you downloaded.

Clean the house:
```
sudo apt-get purge nvidia-*

sudo rm -rf /etc/X11/xorg.conf
```
Then restart your machine.

Once you get into the desktop again, install the Steam driver:
```
sudo apt-get install nvidia-experimental-310
```
Create the X config file:
```
sudo nvidia-xconfig
```
Restart. Now you should be using the proper Nvidia driver for Steam.

Let us know how it goes.
Regards.

---

### Post by Purple Narwhal on 2013-05-16
When I did exactly what you said and rebooted after installing the experimental drivers, Ubuntu couldn't startup. I get a black screen. I can go into the recovery console by holding shift if there is a way to fix this problem.

Thanks!

---

### Post by papibe on 2013-05-16
Sorry to hear that.

Let's try the current stable version then:

Boot until you get the black screen, wait a minute or so, and go to text-mode console by pressing Ctrl+Alt+F1

Login and uninstall the previous driver:
```
sudo apt-get purge nvidia-*

sudo rm -rf /etc/X11/xorg.conf
```
Then restart your machine.

Once you get into the desktop again, install the normal driver:
```
sudo apt-get install nvidia-current
```
Create the X config file:
```
sudo nvidia-xconfig
```
Restart:
```
sudo reboot
```

Let us know how it goes.
Regards.

---

### Post by Purple Narwhal on 2013-05-16
Thanks for helping, but I cannot get to the command line using Ctrl + Alt + F1. It has no response on the black screen. What should I try now?

---

### Post by papibe on 2013-05-16
Boot into recovery mode. You can't install anything, but at least you can remove packages:
```
sudo apt-get purge nvidia-*

sudo rm -rf /etc/X11/xorg.conf

sudo reboot
```
Let us know if that helps.
Regards.

---

### Post by Purple Narwhal on 2013-05-16
Well, uninstalling the old drivers in recovery mode and then re installing the current normal drivers through terminal worked! I can run steam and it shows up in additional drivers! I still can't use Ctrl Alt F1. This is what it looks like (See attachment) 
[ATTACH=CONFIG]242656[/ATTACH]
Thanks for helping!

---

### Post by papibe on 2013-05-16
Glad you got Steam working ;)

At this moment, I don't know why it does not go to text mode. I can suggest trying Ctrl+Alt-F2 through Ctrl+Alt-F6.

If that doesn't get you there, you may want to try the boot option called 'nomodeset':
```
gksudo gedit /etc/defualt/grub
```
Look for a like that looks like this:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```
Add nomodeset to it so it looks like this:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"
```
Save the file, and reboot.

Let us know if that fixes the text mode problem.
Regards.

---

