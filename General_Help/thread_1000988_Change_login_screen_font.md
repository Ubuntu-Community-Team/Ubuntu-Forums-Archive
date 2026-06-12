---
title: "Change login screen font"
date: 2008-12-03
forum: General Help
---

### Post by s_raiguel on 2008-12-03
Where is the file or script that controls the appearance of the login window? After manually installing a new graphics driver, the font on the login screens for name and password are almost microscopic, though everything else seems to work fine now. The login window preferences app offers nothing relevant in this regard. Although I've been around computers since CP/M days, I've only recently begun using Ubuntu, and the most difficult part of learning to use it has been finding what controls what and where in the file system to find it, of which this is a good example.

---

### Post by Wartender on 2008-12-03
perhaps if you install a different GDM (there are some nice ones at [www.gnome-look.org](www.gnome-look.org)) the font will be a regular size. I prefer them to the standard one anyway

---

### Post by s_raiguel on 2008-12-03
Sounds worth a try, I'll give it a look. Thanks for your response

---

### Post by s_raiguel on 2008-12-04
Found the answer, should anybody else have this issue. There are actually two solutions (sorry, but installing a different GDM isn't one of them). The first is 
---------------------
sudo gedit /etc/gdm/gdm.conf

Search for, &#8220;command=/usr/bin/X -br -audit 0&#8221;

Add &#8220; -dpi 96&#8221; to each line that has only what is specified
above.
-----------------
And the second method - the one I used with success -  is 

sudo nano /etc/X11/xorg.conf
  
Add line:

Option "DPI" "96 x 96" 

to the Device section where the 
graphics card driver and other information is defined.

---

