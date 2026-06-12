---
title: "Multiple questions: Setting permissions, Synergy, NTFS-3G"
date: 2006-07-31
forum: Desktop Environments
---

### Post by Panserbjorn on 2006-07-31
I've got a few questions. Any help on any of them is much appreciated.

1. When I try to create folders or files in /usr/ or /etc/, gedit or archive manager tell me I don't have the permissions to do so. I'm new to Linux, so I'm sure there's a simple solution for this. Any ideas?

2. I installed Hamachi to create a network with my Windows laptop. I'm using QuickSynergy to try to share my mouse and keyboard, using this machine as the server. However, when I try and connect with my laptop, the Linux machine refuses the connection. How can I solve this?

3. I tried installing/configuring NTFS-3G, as most of my files are on an external 320GB HDD. Plain and simple, I just couldn't get it to work. I used [this]("http://lunapark6.com/?p=1710") tutorial, but a few of the vagueities, like "mount point" threw me off. I'm brand new to this, and I'm good at following directions, but sometimes I can't figure out exactly what I need if they don't tell me what to type.

Thanks for any and all help!

Panserbjorn

---

### Post by jasutton on 2006-07-31
1. You can't write to those locations with those applications because they are running as you (your username) and you don't have permissions to write to those locations.  You can run your application as 'root' if you know you'll be writing to those locations (Use Alt+F2 to bring up the Run Command dialog, then type 'sudo [application]' to run that [application] as root).  So, for example, 'sudo gedit' would run 'gedit' as root, which could then write to anywhere on the filesystem.

2. I have never played with Synergy, so I can't help you there...

3. Well, a mountpoint is simply a folder on the filesystem (sometimes it's a folder in /mnt or /media) where you mount devices so that you can access their files.  Think of them as 'drive letters' if you're from the Window$ world (only mountpoints are _so_ much more flexible :) ).  I did get NTFS-3G working when I first read about it, so here are the things I think I did to get it working (some info borrowed from one of the comments on the link you posted).  When I did the compiling, I also rolled a quick DEB of the result so that I could easily remove it if needed, so the link to download it is listed :)

```
sudo apt-get install libfuse2 libfuse-dev fuse-utils
wget http://jaredsutton.com/downloads/ntfs-3g_20060714-1_i386.deb
dpkg -i ntfs-3g_20060714-1_i386.deb

```

Then add it to your fstab
```
[your-device] [your-mount-point] ntfs-3g silent,umask=0 0 0
```

Check to see if you have write permissions
```
sudo modprobe fuse && sudo umount -a && sudo mount -a
```

Now to make fuse load at bootup
```
echo fuse | sudo tee -a /etc/modules
```

---

### Post by Panserbjorn on 2006-07-31
First of all, thank you very much. I knew the first solution would be simple. As for NTFS-3G, I'm still having problems. I did everything you listed. When I rebooted, Nautilus said it couldn't mount my external. 
```
mount: only root can mount /dev/sdc1 on /mnt/windows
```
I tried manually mounting it as in the article and got this from the terminal:

```
fusermount: failed to access mountpoint /mnt/windows: No such file or directory
fuse_mount failed.
Unmounting /dev/sdc1 (WD External)
```

When I checked to see if I had write permissions, I got this:

```
umount: /dev: device is busy
umount: /var/run: device is busy
umount: /: device is busy
```

---

### Post by jasutton on 2006-08-14
If you ever get messages about 'access denied' or 'only root can do that' you can just do 'sudo -s' on the terminal to open a root terminal.  Then, anything you do from there on out, in that terminal, will be done as root.  

So, the first thing you'll need to do is create that mount point (as 'No such file or directory' suggests it doesn't exist yet).

```

sudo -s
<type-your-password-when-prompted>
mkdir /mnt/windows

```

Second, I'd like to verify that the proper mounting info was inserted into /etc/fstab.  Can you post the output of this command?

```
cat /etc/fstab
```

---

### Post by givré on 2006-08-15
The tutorial about ntfs-3g you follow was outdated, please follow the ubuntu howto [http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009)
 you save you a lot of time, and it will be a lot more safe.

---

