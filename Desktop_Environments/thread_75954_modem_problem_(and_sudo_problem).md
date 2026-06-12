---
title: "modem problem (and sudo problem)"
date: 2005-10-14
forum: Desktop Environments
---

### Post by jagilbert on 2005-10-14
HI.  I'm new to Linux and Unbuntu.   I installed yesterday on a IBM T23 and my home desktop and everything worked like a charm, until I tried to get my modem in my desktop to work (Diamond SupraMax PCI Pro - 56K Modem).  I tried both the networking GUI and terminal (sudo pppconfig).  I finally got the modem to "activate" using the networking GUI.  I wasn't sure if it was really working so I decided to reboot.  When I logged in I got a dialog box that said; "Could not look up internet address for .  This will prevent GNOME from operating correctly.  It may be possible to correct the problem by adding to the file /etc/hosts".  There were two buttons, 'try again' and 'log in anyway'.  'Try again' didn't do anything so I 'logged in anyway'.  Now almost all of the administration apps don't work.  The windows try to start up then never appear.  I tried to use a terminal but when I try sudo anything I get this response - 

sudo: unable to look up via gethostname ().

I must have done something wrong, but I don't know what and I don't seem to have any admin rights to find out.  HELP!!!:confused:

---

### Post by Alexander Kirillov on 2005-10-14
[QUOTE=jagilbert]HI.  I'm new to Linux and Unbuntu.   I installed yesterday on a IBM T23 and my home desktop and everything worked like a charm, until I tried to get my modem in my desktop to work (Diamond SupraMax PCI Pro - 56K Modem).  I tried both the networking GUI and terminal (sudo pppconfig).  I finally got the modem to "activate" using the networking GUI.  I wasn't sure if it was really working so I decided to reboot.  When I logged in I got a dialog box that said; "Could not look up internet address for .  This will prevent GNOME from operating correctly.  It may be possible to correct the problem by adding to the file /etc/hosts".  There were two buttons, 'try again' and 'log in anyway'.  'Try again' didn't do anything so I 'logged in anyway'.  Now almost all of the administration apps don't work.  The windows try to start up then never appear.  I tried to use a terminal but when I try sudo anything I get this response - 

sudo: unable to look up via gethostname ().

I must have done something wrong, but I don't know what and I don't seem to have any admin rights to find out.  HELP!!!:confused:[/QUOTE]

apparently you messed up the file /etc/hosts, so GNOME is having difficulties figuring out where to find your machine:)

If you could use sudo, the way to fix it would be to make sure that /etc/hosts  contains the line 

127.0.0.1 localhost.localdomain localhost <yourmachinename>
 
If sudo doesn't work, you could try rebooting the machine in failsafe (=single user mode), by selecting pressing "e" in GRUB menu and adding the word "single" to the end of boot command.

---

### Post by jagilbert on 2005-10-14
Thanks.  I'll give it a try when I get home from work.

---

