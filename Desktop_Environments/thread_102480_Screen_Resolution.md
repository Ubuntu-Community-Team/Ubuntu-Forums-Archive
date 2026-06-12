---
title: "Screen Resolution"
date: 2005-12-12
forum: Desktop Environments
---

### Post by camspiers on 2005-12-12
Hey I'm new to linux. My problem is that i have a LCD moniter that is able to display 1280 x 1024 but i can't get this option when going **System >Preferences > Screen Resolution** i can only get 1024 x 768. I have looked in other threads and tried running in terminal "sudo dpkg-reconfigre xserver-xfree86" or something similar and it tells me that it isn't installed. can you please help me??
Cheers Cam.

---

### Post by gosh on 2005-12-12
You can edit the different resolution settings in:

sudo gedit /etc/X11/xorg.conf

Does this help?

---

### Post by camspiers on 2005-12-12
Yes it will do if i could find out what i need to change can you help me?

---

### Post by Gustav on 2005-12-12
Look at this: [http://www.ubuntuforums.org/showthread.php?t=83973](http://www.ubuntuforums.org/showthread.php?t=83973)

---

### Post by camspiers on 2005-12-12
Cheers Guys that worked wonders!!!!
just another question while i was using the configuator it asked about refresh rates and i didn't know them can i use 
sudo gedit /etc/X11/xorg.conf
to edit them now??

---

### Post by Gustav on 2005-12-12
[QUOTE=camspiers]Cheers Guys that worked wonders!!!!
just another question while i was using the configuator it asked about refresh rates and i didn't know them can i use 
sudo gedit /etc/X11/xorg.conf
to edit them now??[/QUOTE]
Sure, but be sure to make a backup

---

