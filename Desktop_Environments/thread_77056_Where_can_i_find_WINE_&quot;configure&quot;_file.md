---
title: "Where can i find WINE &quot;configure&quot; file"
date: 2005-10-16
forum: Desktop Environments
---

### Post by janko on 2005-10-16
Hi all, I've installed wine using the official repositories but no .exe programs works. I thought i had to configure WINE but i can't find the myhome/.wine/config
Actually the hidden .wine directory exists but there's no config file, and i can't find it even online to download.
Please someone help me!

thank you,

Janko

ps. I heve a windows installation already on another partition if it can halp.

---

### Post by stoffe on 2005-10-16
Try to remove it and reinstall, it should "just work".

Also, you might want to try the wine in Breezys repositories, I think it is as recent as the one on the wine dl site, since noone there has built any new debs in a while.

---

### Post by yage on 2005-10-16
And remebmer to use
```
winecfg
```
since thats the new configuration app for wine. 
If you still can't find you wine config file try
```
sudo updatedb && locate wine | grep config |more
```
Best of luck

---

### Post by janko on 2005-10-16
I've tried winecfg and works but still there's no windows application that runs, using the code yage posted it doesn't find any config file. My question is, does it really needs a config file? (i think yes) but i really don't understand why installing wine trough ubuntu repositories I don't have the config file in the right place (~/.wine/config) and last but not least, can someone post here a config file so i can try to put it in the right place?
thank you all,

Janko

---

### Post by JurB on 2005-10-16
Same problem here, i installed wine trough the breezy repo.
Winecfg works, but no config file in .wine.
tried "sudo updatedb && locate wine | grep config |more" but it doesn't seem to do anything.

---

