---
title: "HELP! GNOME Error (SettingsDaemon)"
date: 2007-11-21
forum: Desktop Environments
---

### Post by eager2know on 2007-11-21
Hello everyone.

This morning I received the following error from GNOME:
> There was an error starting the GNOME Settings Daemon.
 ...
The last error message was:

The name org.gnome.SettingsDaemon was not provided by any .service files

I know what I did to cause this, but I have no clue how it can be fixed. 

Here is what I did:
I have a second hdd on my system namely *sdb1*. I changed */etc/fstab* so that the drive would automount to */home/myname/storage *folder each time I start my computer. After adding a line to fstab I did>  sudo mount -a and everyhing was peachy. I was able to see the content of my disk inside the storage folder. 

Then I decided to reboot and when it did I was quite shocked to see that instead of my second disk contents the system had mounted my first disk with system root directory. The entire contents of my *'/' *directory was inside the my *~/storage* folder. I could recursively go in and there I would find my home and storage dirs againg. 

Turned out that *sdb1 *somehow became *sda1*. I don't know how it happened, but it did, and I saw it in *fdisk -l.* 

I removed a line from fstab. And then deleted the *~/storage*. 

On the next reboot I saw the GNOME desktop no more. :( 

All files are intact, my LAMP server is live and kicking, only the desktop is gone.

How can I fix this error without having to reinstall Ubuntu????

Please help. Anyone.

Thanks in advance.

---

### Post by Thyme on 2007-11-21
This happened to me when I rebooted after upgrading to Gusty. To say the least, everything was broken. No X,  reinstalled the kernel, gtk, glib, changed sessions etc .. I can't remember what I did but I was't able to fix it.I'm sure though that someone with sufficient knowledge will be able to help you out.

What do you get when you type in:

```

sudo ldd /usr/libexec/gnome-settings-daemon

```

---

### Post by eager2know on 2007-11-21
I'm at work now. Will check and post it later when I get back. Thanks.

---

