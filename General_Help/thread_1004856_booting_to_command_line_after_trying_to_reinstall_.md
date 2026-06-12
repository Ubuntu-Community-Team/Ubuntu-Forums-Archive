---
title: "booting to command line after trying to reinstall alsa"
date: 2008-12-07
forum: General Help
---

### Post by feedmecereal on 2008-12-07
I am having an issue with sound playing at very low volume. So, I read a guide that said to try ```
sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
``` Then, I tried ```
sudo apt-get install gdm ubuntu-desktop
``` but I closed the window when it was trying to download an OpenOffice update. I then rebooted and now I am stuck at the command line. I tried gnome-session but I get an error message.

Please help! How do I get back to GNOME?

Edit:
OK, here is some more info. When I try to boot I get the following error message:
"kinit: no resume image, doing normal boot..."

---

### Post by spiderbatdad on 2008-12-07
```
startx
```

---

### Post by Linux4theWin on 2008-12-08
> **feedmecereal said:**
> I am having an issue with sound playing at very low volume. So, I read a guide that said to try ```
sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
``` Then, I tried ```
sudo apt-get install gdm ubuntu-desktop
``` but I closed the window when it was trying to download an OpenOffice update. I then rebooted and now I am stuck at the command line. I tried gnome-session but I get an error message.

Please help! How do I get back to GNOME?

Edit:
OK, here is some more info. When I try to boot I get the following error message:
"kinit: no resume image, doing normal boot..."

i followed this instructions that unutbu gave me.
[http://ubuntuforums.org/showthread.php?p=6326186#post6326186](http://ubuntuforums.org/showthread.php?p=6326186#post6326186)

And i have the same problem . . :(:( 
As you can see here . . 

[http://ubuntuforums.org/showthread.php?p=6327254#post6327254](http://ubuntuforums.org/showthread.php?p=6327254#post6327254)

---

### Post by lovelyvik293 on 2008-12-08
Use the command
```

sudo apt-get install gdm ubuntu-desktop

```
again.

---

### Post by Linux4theWin on 2008-12-09
> **lovelyvik293 said:**
> Use the command
```

sudo apt-get install gdm ubuntu-desktop

```
again.

[https://bugs.launchpad.net/ubuntu/+bug/103148](https://bugs.launchpad.net/ubuntu/+bug/103148)
I found this and did this .. .

[http://www.thekip.nl/2007/12/18/kini...e-image-fixed/](http://www.thekip.nl/2007/12/18/kini...e-image-fixed/)

and

This

sudo apt-get install ubuntu-desktop


Thank You man

---

