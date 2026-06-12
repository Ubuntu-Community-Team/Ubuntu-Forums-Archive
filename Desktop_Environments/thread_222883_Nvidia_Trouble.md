---
title: "Nvidia Trouble"
date: 2006-07-25
forum: Desktop Environments
---

### Post by Sq322 on 2006-07-25
Here is the output of running the config line in the terminal
> Error: your X configuration has been altered.
This script cannot proceed automatically. If you believe that this
not correct, you can update the md5sum entry executing the following
command:
md5sum /etc/X11/xorg.conf | sudo tee /var/lib/x11/xorg.conf.md5sum
otherwise edit manually /etc/X11/xorg.conf to change the Driver section
from nv to nvidia.

any ideas ?
Thx in advance

---

### Post by endfx on 2006-07-25
I had this happen to me.
When you run config at the terminal, all it really does is add the driver name in the appropriate location to xorg.conf. You probably don't need to run config.

Here is what you should try:
1. backup xorg.conf:
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.working

2. Edit xorg.conf:
Find the line that says: 
'Driver           "nv"'
and replace it with:
'Driver           "nvidia"'

This just tells x to load the nvidia driver (which you just installed, right?) instead of the nv driver.
If x doesn't load the next time you want it to, just copy the xorg.conf.working to xorg.conf and you'll be back to your original working x.

Does this make sense?

---

### Post by endfx on 2006-07-25
On a side note, I'm assuming you are trying to install the Nvidia drivers. You really didn't say what you were trying to do :)

---

### Post by Sq322 on 2006-07-26
Thx. yup i am trying to install the Nvidia drivers. Guess I shoulda clarified

---

### Post by LORD_PoLvO on 2006-07-26
remember to install glx aswell.

---

### Post by Sq322 on 2006-07-26
Will do Thx

---

### Post by SpongeBob SquarePants on 2006-07-26
I had this problem too and simply tried.....

sudo dpkg-reconfigure -phigh xserver-xorg

....then enabled the driver as per usual instructions. Worked for me :)

---

### Post by Sq322 on 2006-07-26
What I shoulda done first was installed Automatix.
That corrected my issues regardless.
Thx for the assitance though

---

