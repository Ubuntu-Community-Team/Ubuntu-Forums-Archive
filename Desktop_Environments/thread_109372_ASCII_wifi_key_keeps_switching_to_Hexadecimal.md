---
title: "ASCII wifi key keeps switching to Hexadecimal"
date: 2005-12-28
forum: Desktop Environments
---

### Post by faddat on 2005-12-28
I have a wifi connection to the Internet which doesn't have a super-strong signal strength.  Sometimes, when the signal strength takes a dip, my "Key Type" setting for my connection gets switched from ASCII (which it should be) to Hexadecimal (which it should not be).  This then makes the Internet connection appear to be connected but not function, and I have to go to the menu and change the setting back and it will work again.  Is this a documented bug?  Does anyone know if there's anything I can do to fix this?

Thanks!

-Jake

---

### Post by ubuntuguru on 2005-12-28
I dont know how to fix it

---

### Post by Lambert on 2005-12-28
are you setting it from the gui? there are some small known bugs/annoyances that happen there. NOt sure if a bug has been reported on this though.

open this file

```
sudo gedit /etc/network/interfaces
``` 
you should see something like this but it might not have ath0, it will have what ever interface name is given for your device.

iface ath0 inet dhcp
wireless-essid xxxxx
wireless-key xxxxxxxx

where you see wireless-key yours should look like this

wireless-key s:xxxxxxxxxxx

the s: designating the key as ascii.

If you see xxxx-xxxx-xx as your key it's ok as some keys are put in that format.

---

