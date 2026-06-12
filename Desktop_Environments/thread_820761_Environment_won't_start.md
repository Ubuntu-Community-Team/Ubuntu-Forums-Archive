---
title: "Environment won't start"
date: 2008-06-06
forum: Desktop Environments
---

### Post by beanie0610 on 2008-06-06
I had problems with my desktop effects not working, so i tried enabling restricted drivers, nothing worked though. After all this I used some sudo gedit command to change a file to say something like "option intel-snd-card=1" instead of the one being auto. Now whenever I boot my computer, it stops before the login screen and has a black background with grey font asking me my username and password. After those are entered it just gives me a command line. Is there anyway for me to get back to my desktop environment or boot in a safe mode to fix all this?

ps.
I'm running on an Intel Graphics Media Accelerator 900 GM Graphics card.

Help Please!!!

---

### Post by beanie0610 on 2008-06-06
Also, when my computer does start up, while going through the checklist where it will say [OK] to the right, by timidity it says [fail] in red so that might be a starting point...

---

### Post by ajgreeny on 2008-06-06
If you used gedit to change a system file there will be an automatically produced backup of the original so I hope you can remember the name of the file you edited.
Assuming you can, login, and in the console (dos-like screen you see) navigate to the folder where the file was with ```
cd /path/to/foldername
```Now use ```
ls -a
```to see all the files, including hidden and backup files, in that folder and you should see list of all the folders, if there are any, and files in that folder.  With luck there will be a file with the name of the old file, but ending in ~, eg file.conf~ instead of file.conf

If this is so, just check the date of the ~ file to ensure it was the date you made the change, rename the new file.conf with ```
sudo mv /path/to/file.conf /path/to/file.confbak
``` and reinstate the original with ```
sudo mv /path/to/file.conf~ /path/to/file.conf
```
This should get you back to where you were before changing the file that you mention, and hopefully a reboot, or even ```
sudo /etc/init.d/gdm start
```will start the gui again.  Then you can deal with the graphics drivers if you want to try again

---

### Post by beanie0610 on 2008-06-06
I tried that and it didn't work, but is there a way to start in safe graphics mode.

ps. the file I edited with gedit was /etc/modprobe.d/alsa-base

---

### Post by jualin on 2008-06-06
how about booting into Failsafe mode (from the grub menu when you turn on the PC) and when you are in the command line screen log in and enter your password (All is command line) and then type > sudo dpkg-reconfigure xorg-xserver and just follow the instructions after it. Hope this helps!

---

### Post by beanie0610 on 2008-06-06
It gives me an error saying "/usr/sbin/dpkg-reconfigure: xorg-xserver is not installed"

---

### Post by beanie0610 on 2008-06-06
Is there any way to install it via maybe usb or live cd?

---

### Post by jualin on 2008-06-06
are u using ubuntu or another desktop environment?

---

### Post by beanie0610 on 2008-06-06
Ubuntu, Gutsy gibbon.

---

### Post by jualin on 2008-06-06
i think the command is > sudo dpkg-reconfigure xserver-xorg 

---

### Post by beanie0610 on 2008-06-06
I reconfiguring it twice and I still have the same problem. Could it be a problem unrelated to the xserver?

---

