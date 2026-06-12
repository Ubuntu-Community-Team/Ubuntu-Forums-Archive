---
title: "Screen Resolution"
date: 2005-12-15
forum: General Help
---

### Post by Gary Lambert on 2005-12-15
I only have Resolution selection for 640X480.  Ther are no other selections in the pull down menu for screen resolution.  How do I get more selections?

---

### Post by frodon on 2005-12-15
Post here your xorg.conf file and give us the full name of your screen or your laptop.

---

### Post by Gary Lambert on 2005-12-15
AS a new user I am not sure what you are asking.  How do I get my xorg.conf

---

### Post by frodon on 2005-12-15
Sorry, i was a little bit too quick in my answer.
Open your xorg.conf, it's the file which contain your graphical configuration. Use this command in a terminal to open the file : ```
sudo gedit /etc/X11/xorg.conf
```

---

### Post by thalliwell on 2005-12-15
If your Graphics card is a Nvidia try:

Install the nvidia-glx and nvidia-settings packages with Synaptic 

Miscellaneous - Graphical (restricted) > nvidia-glx
Miscellaneous - Graphical (restricted) > nvidia-settings



sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup 
sudo nvidia-glx-config enable 
sudo gedit /usr/share/applications/NVIDIA-Settings.desktop

Insert the following lines into the new file 

[Desktop Entry]
Name=NVIDIA Settings
Comment=NVIDIA Settings
Exec=nvidia-settings
Icon=
Terminal=false
Type=Application
Categories=Application;System;

This worked well for me.

---

