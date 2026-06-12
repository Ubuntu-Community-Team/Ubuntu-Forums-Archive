---
title: "NVIDIA: Failed to load the NVIDIA kernel module"
date: 2010-08-31
forum: Desktop Environments
---

### Post by ncpokrt on 2010-08-31
I spent quite a lot of time jumping from one thread to another trying to fix a problem with my NVIDIA drivers in Lucid.  I was getting the error message on startup:  NVIDIA: Failed to load the NVIDIA kernel module ...Failed to load module "nvidia" (module-specific error, 0) No drivers available".

After a lot of trial and error, this is what worked for me (I have updated this thread following [http://ubuntuforums.org/showthread.php?t=1467074):](http://ubuntuforums.org/showthread.php?t=1467074):)

- Download the latest NVIDIA driver from [www.nvidia.com/page/drivers.html](www.nvidia.com/page/drivers.html)

- In the terminal cd to the directory where you downloaded the driver package (e.g., $ cd Downloads)and make it executable (e.g., $ sudo chmod +x ./NVIDIA-Linux-x86_64-256.53.run)

- Edit blacklist.conf
  $ gksu gedit /etc/modprobe.d/blacklist.conf
and add the following lines to the end of the file:

#recommended by [http://ubuntuforums.org/showthread.php?t=1467074](http://ubuntuforums.org/showthread.php?t=1467074)
blacklist vga16fb
blacklist nouveau
blacklist rivafb
blacklist nvidiafb
blacklist nvatv

Then save and quit

In the terminal
$ sudo apt-get --purge remove nvidia-*
$ sudo reboot

When you restart you will get an error message.  Choose console login from the menu.
- cd to the directory where the driver is located and
- Run the driver installer
    e.g., $ sudo sh NVIDIA-Linux-x86_64-256.53.run

Note: When I ran this I got an error message "Unable to find kernel source tree", so I ran:
    $ sudo apt-get install linux-headers -`uname -r' 
(for which I am grateful to hdog at this thread [http://ubuntuforums.org/showthread.php?t=843914](http://ubuntuforums.org/showthread.php?t=843914)) and then reran the installer.

-  Start X
    $ sudo service gdm start

I hope I remembered all of the steps correctly.  Corrections are welcome.

---

### Post by lecneri on 2010-09-08
hi,

your post didnt worked for me. The solution I've found that worked out was in [http://ubuntuforums.org/showthread.php?t=1467074](http://ubuntuforums.org/showthread.php?t=1467074)

---

### Post by ncpokrt on 2010-09-12
Thank you for posting that.  I wish I had found that thread before I went through my ordeal.  Just to document my problem for others who might have a similar one...

I thought I solved my problem with the solution that I originally posted.  I was able to use Blender for hours without a crash and it was fast.  The problem came when I went on the internet.  The system would freeze completely.  I had to shut down the computer power and restart.  I thought it was a problem with Chrome so I switched to Firefox.  Same thing.  I had to shut down the power.

I went back to this thread (using another computer) and I followed the instructions in [http://ubuntuforums.org/showthread.php?t=1467074](http://ubuntuforums.org/showthread.php?t=1467074).  Now Blender is working and I am on the internet!!

I have updated my original post with the better procedure.

---

