---
title: "GNOME Desktop Icons"
date: 2010-01-09
forum: Desktop Environments
---

### Post by Jasonx86 on 2010-01-09
Hi,

Can anyone tell me a good graphics program to create GNOME desktop icons? 

Are they PNGs or some vector based format. Also where are the icons stored?

Thanks.

---

### Post by TyrantWave on 2010-01-09
Anything I make is first drafted in GIMP, then I turn it into an SVG Vector in Inkscape.

SVGs are good as they are scalable to any size without loss of quality.

After making the SVG file, I'll import into GIMP in specific file sizes:
18x18, 22x22, 24x24, 32x32, and 48x48 IIRC are the standard icon sizes.
Save these as PNGs for the transparency.

This will give you 6 folders in the icon set (The 5 different sizes using PNGs, and a Scalable folder for the SVGs).

For places to save icons, put them in your home .icons folder:
username/.icons/

You can put them in a folder for different icon sets, obviously.

---

### Post by MooPi on 2010-01-09
> **Jasonx86 said:**
> Hi,

Can anyone tell me a good graphics program to create GNOME desktop icons? 

Are they PNGs or some vector based format. Also where are the icons stored?

Thanks.
I believe Inkscape can create .svg icons. Your standard icons are stored in /usr/share/icons. I'm not sure if your asking for a launcher or icon builder? If you just want an application launcher just right click on your desktop and choose create launcher.

---

### Post by Jasonx86 on 2010-01-09
Thanks Guys.

Very helpful indeed.

---

