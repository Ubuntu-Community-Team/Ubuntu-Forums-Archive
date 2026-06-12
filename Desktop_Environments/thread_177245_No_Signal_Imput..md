---
title: "No Signal Imput."
date: 2006-05-16
forum: Desktop Environments
---

### Post by vectorl33t on 2006-05-16
I recently followed some instructions on how to install nvidia drivers. It went smoothly, but now when i restarted it and it went through all of the loading part, my monitor told me No Signal Imput. Obviously the cable did not come lose as I rebooted into windows fine. The commands I ended up using were:

sudo apt-get install nvidia-glx
sudo apt-get install nvidia-settings
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo nvidia-glx-config enable
sudo gedit /usr/share/applications/NVIDIA-Settings.desktop

I was wondering...Should I do:
 sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf to restore it. Otherwise  
I don't know how to get back into ubuntu without reformatting it, which I would rather not do as I just got my wireless card working great with it. Also, just another quick question, when you hit ctrl+alt+f1 to reboot gnome, it drops you into a terminal without a GUI. How do you get back into gnome.

---

### Post by Dr. Nick on 2006-05-16
[quote=vectorl33t]I recently followed some instructions on how to install nvidia drivers. It went smoothly, but now when i restarted it and it went through all of the loading part, my monitor told me No Signal Imput. Obviously the cable did not come lose as I rebooted into windows fine. The commands I ended up using were:

sudo apt-get install nvidia-glx
sudo apt-get install nvidia-settings
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo nvidia-glx-config enable
sudo gedit /usr/share/applications/NVIDIA-Settings.desktop

I was wondering...Should I do:
 sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf to restore it. Otherwise  
I don't know how to get back into ubuntu without reformatting it, which I would rather not do as I just got my wireless card working great with it. Also, just another quick question, when you hit ctrl+alt+f1 to reboot gnome, it drops you into a terminal without a GUI. How do you get back into gnome.[/quote] 
ctrl+alt+backspace restarts gnome to get back after f1 do ctrl+alt+f7

Never seen your video problem, I would restore the backup xorg using the recover option in grub. And dont use glx-enable, just manually change nv to nvidia in xorg. If i were to bet I would say you may have problems with the refresh settings in xorg.

If that doenst work run _**sudo dpkg --reconfigere xserver-xorg **_and set it up again, at the monitor section dont use the "simple" choice, pick the middle one and set the monitor to the closest match

---

### Post by vectorl33t on 2006-05-16
Nvm, maybe I should just try things instead of posting. I got it to work again. And the solution was, if anyone ever needs it:
sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf

And thats it, booted back into. Trying to figure out what went wrong in the first place. Please let me know if you know what went wrong as I have no clue. I added this to this file /usr/share/applications/NVIDIA-Settings.desktop:

[Desktop Entry]
Name=NVIDIA Settings
Comment=NVIDIA Settings
Exec=nvidia-settings
Icon=
Terminal=false
Type=Application
Categories=Application;System;

---

### Post by Dr. Nick on 2006-05-16
[quote=vectorl33t]Nvm, maybe I should just try things instead of posting. I got it to work again. And the solution was, if anyone ever needs it:
sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf

And thats it, booted back into. Trying to figure out what went wrong in the first place. Please let me know if you know what went wrong as I have no clue. I added this to this file /usr/share/applications/NVIDIA-Settings.desktop:

[Desktop Entry]
Name=NVIDIA Settings
Comment=NVIDIA Settings
Exec=nvidia-settings
Icon=
Terminal=false
Type=Application
Categories=Application;System;[/quote] 
Your back in X but do you have 3d acceleration? Anyway glad you atleast got back to a gui

---

### Post by vectorl33t on 2006-05-16
Well if I have to of had set that up myself then know I haven't gotten around to that yet. Can you give me a link on that. Also if it helps I have a 6600gt. Which is an Nvidia Card.

---

### Post by Dr. Nick on 2006-05-16
[quote=vectorl33t]Well if I have to of had set that up myself then know I haven't gotten around to that yet. Can you give me a link on that. Also if it helps I have a 6600gt. Which is an Nvidia Card.[/quote] 
Instaling the nvidia drivers will get you 3d acceeration
Try this link
[http://ubuntuforums.org/showthread.php?t=75074&highlight=nvidia+howto]("http://ubuntuforums.org/showthread.php?t=75074&highlight=nvidia+howto")

You were going the right direction to achieve this but I am a little confused on your solution. When you copied the backup file back to restore your old settings you cancled out most everything done by installing the drivers so you really ended up where you started from, which was with no 3d acceleration.

The nvidia-glx enable will change your xorg.conf file for you, but I always found it best to edit it myself per the instrctions in the link above.

---

