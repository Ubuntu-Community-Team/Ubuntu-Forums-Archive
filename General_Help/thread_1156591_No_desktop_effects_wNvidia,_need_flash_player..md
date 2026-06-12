---
title: "No desktop effects w/Nvidia, need flash player."
date: 2009-05-11
forum: General Help
---

### Post by Yomny on 2009-05-11
No desktop effects with Nvidia 260 gtx, what can i do.  Also i cant seem to be able to install Flash player to watch videos on youtube.  Thanks for any help you could assist me with.

---

### Post by collinp on 2009-05-11
This command should solve both of your problems:
```
sudo apt-get install flashplugin-nonfree nvidia-glx-180 && nvidia-xconfig
```

"sudo" runs the command as root (the administrator account of the computer), "apt-get install" is the command to install the files you need, "flashplugin-nonfree" & "nvidia-glx-180" is the names of the packages that contains the files you need. "nvidia-xconfig" configures your display configuration file to use the drivers you just installed.

---

### Post by Yomny on 2009-05-11
wow.. thats all i have to say... im not sure its working but i typed it in the terminal and its installing about 209MB's worth of junk..its that easy huh..
Thanks a mil..
Im a complete noob when it comes to linux Os's but i would like to learn some commands and things like the one you just taught me.. Anything i could do, anywhere i could go and read something.. Classes @ college?  Thanks

---

### Post by Yomny on 2009-05-11
Using X configuration file: "/etc/X11/xorg.conf".

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  Device section "Configured Video Device" must have a Driver
                  line.


ERROR: Unable to write to directory '/etc/X11'.


This is what i get..

---

### Post by collinp on 2009-05-11
> **Yomny said:**
> 
Im a complete noob when it comes to linux Os's but i would like to learn some commands and things like the one you just taught me.. Anything i could do, anywhere i could go and read something.. Classes @ college?  Thanks

Heh, no need for collage courses, you can find enough information online :). Some good resources on Linux commands, Linux in general, and Ubuntu:

[Basic Linux Commands](http://www.reallylinux.com/docs/basic.shtml)
[The Ubuntu Guide](http://ubuntuguide.org/wiki/Ubuntu:Jaunty)
[Ubuntu Documentation](http://help.ubuntu.com/)

---

### Post by Yomny on 2009-05-11
im still stunned.. well even with that error i rebooted and everything is working great.. again.. thanks a lot, i could now go to sleep at ease.

---

### Post by collinp on 2009-05-11
Disregard this post.

---

### Post by Yomny on 2009-05-11
quick question.. i cant seem to find my partition manager or Gparted.. i know it was under system>administration but is not there

---

### Post by collinp on 2009-05-11
> **Yomny said:**
> quick question.. i cant seem to find my partition manager or Gparted.. i know it was under system>administration but is not there

To edit partitions, you have to boot back into a LiveCD (the Ubuntu CD) and edit them there. Sorry, but you cannot edit partitions when you are using them :).

---

### Post by Yomny on 2009-05-11
i got it to work, not to work i just went to add/remove and installed it again.. i think the janitor cleaning guy erased it.  Now i can use Gnome partition editor..

---

### Post by Yomny on 2009-05-11
why is it that why i enter "sudo" only it asks for a password and when i do enter the only password i have set it says "auth failure"?

---

