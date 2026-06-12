---
title: "Last ditch effort to get Ubuntu to work [resolution issues]"
date: 2007-05-07
forum: Desktop Environments
---

### Post by scaphist on 2007-05-07
I installed my Nvidia 5200 driver.

I then did alt+ctrl+f4 to exit xorg windows

I then did a sudo dpkg-reconfigure -phigh xserver-xorg to try to get a decent resolution. 

I want 1280 x 720 (thats what i used to run on windows. i have a generic monitor that is a 16:9 aspect ratio. ran fine under Windows XP. i dont see why ubuntu cant handle that)

Also, it should be noted that I cannot do anything when I stop gdm manually by doing a "sudo /etc/init.d/gdm stop" command.

I've spent hours trying different things after researching.  Thanks.

---

### Post by shae on 2007-05-07
Try configuring the resolution in /etc/X11/xorg.conf

---

### Post by scaphist on 2007-05-07
I tried to do that using the mode line tool. I kept just getting errors.

Now when I do a alt+ctrl+f4 to get out of Gnome, I get a "hdd drive not ready for command " error, repeatedly...and it happens if i do nothing but let it sit there.

---

### Post by scaphist on 2007-05-07
PLEASE!

I dont want to be a slave to Windows...

---

### Post by tajreed on 2007-05-07
I assume you have tried system/preferences/screen resolution.

Or sudo dpkg-reconfigure xserver-xorg. Then select the appropriate resolution and hit the space bar. Do that from the command line after closing the xserver

---

### Post by scaphist on 2007-05-07
Yes sir, I tried both.

However, like I said, if I do a sudo /etc/init.d/gdm stop command, it takes me to a blank black screen that tells me if some processes are running OK. No command works from that screen.

---

