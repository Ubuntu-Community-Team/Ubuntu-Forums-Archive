---
title: "Disable Reboot and Shutdown Options"
date: 2010-02-15
forum: Desktop Environments
---

### Post by ajoywatkins on 2010-02-15
[FONT=Verdana]I want to disable Reboot and Shutdown options from the drop down menu in Ubuntu 9.10. 

I tried this:

[http://wiki.soslug.org/wiki/disabling_shutdown_and_reboot_in_ubuntu](http://wiki.soslug.org/wiki/disabling_shutdown_and_reboot_in_ubuntu) (The options were not available)

I also tried to modify the [/FONT][FONT=Verdana]gdm.conf file, but the changes I made, made no difference.  

I am a student trying to set up these machines for our Linux Lab.  This is a learning experience for me, so any advice on which direction to go now would be appreciated.  

Thank you[/FONT].

---

### Post by Satoru-san on 2010-02-15
I did this on my server so I wouldnt accidently shutdown via ssh.

you need to create a shutdown and reboot script in the folder /usr/local/sbin that will just echo "dont shut me down!".

Then you need to change your $PATH using your .bashrc to put /usr/local/sbin before EVERY other thing in PATH.

If you actually do want to shutdown or reboot just type the full path /sbin/halt /sbin/reboot


Cheers :)

---

### Post by ArielEnter on 2011-08-03
I followed the instructions from this thread and it worked great:
 

 [http://ubuntuforums.org/showthread.php?t=1670897&page=2](http://ubuntuforums.org/showthread.php?t=1670897&page=2)
 

 Is the same thing that prevents you to power off your computer if another user session is running.

---

