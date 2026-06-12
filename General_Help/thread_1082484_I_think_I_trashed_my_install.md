---
title: "I think I trashed my install"
date: 2009-02-27
forum: General Help
---

### Post by Santa Matt on 2009-02-27
OK, I know I did this to myself and there is probably not a fix for it. But before I delete the VM and make a new Ubuntu VM I thought I would ask here. 

I have a couple of devices with inbedded linux. A Nokia 770 Internet Tablet and an RS Media robot. To learn more about linux I installed Sun's VirtualBox and Ubuntu 8. This has worked very well for me for six months. While working with some files from the robot I was typing commands sent to me by another robot user and it wasn't until I couldn't reboot that I took a look at what I had done.

I typed:
cd ~/rsmdump
chmod 755 mount.sh
./mount.sh
Which was supposed to give me an image of the robot's os from some files I had dumped out. I got the error:
Syntax error: Bad fd number
Which was in the documentation with another set of commands to run. So I ran these commands:
rm /bin/sh
ls -s /bin/bash /bin/sh
./mount.sh
Everything worked fine until a reboot. Now when the VM boots I get these two errors:
init: Unable to execute "/bin/sh" for rcS: No such file or directory
init: rcS main process (2450) terminated with status 255
init: Unable to execute "/bin/sh" for rc-default: No such file or directory
init: rc-default main process (2451) terminated with status 255
And then the machine just hangs. You can type and you get an echo of what you are typing but no commands seem to work. I have Ubuntu for Dummies but although most of that line of books are great, this one is worthless. Is there any way to force the directory back in? Or should I just delete the VM and rebuild it?
Thank you for your help,
Santa Matt

---

### Post by justleen on 2009-02-28
you deleted "sh" which is needed by oher programs, that use sh instead of bash. You could get the /bin/sh file from some where else (live boot cd?) and copy it back to /bin/sh. That should give a working system again. make sure the symlink you created ls overwriten (ls -la /bin/sh should noet show "-> /bin/bash" behind the filename.

To get the script working with bash, you could open it, and change the firstline to #!/bin/bash, instead of #!/bin/sh

---

### Post by heindsight on 2009-02-28
/bin/sh is normally symlinked to /bin/dash, to fix it you can boot off a live cd, mount your root partition and restore the /bin/sh symlink. Assuming your root partition is /dev/sda1, do:
```
sudo mount /dev/sda1 /mnt
cd /mnt/bin
sudo ln -s /bin/dash sh
```
and reboot, everything should be fine. Note the correct command to make a symbolic link is ln -s not ls -s

By the way, I'm guessing that this is related to [thread=1082521]this thread[/thread], see the comments there too.

---

