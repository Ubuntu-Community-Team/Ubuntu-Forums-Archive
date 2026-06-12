---
title: "[SOLVED] Dual layer capability?"
date: 2008-12-25
forum: General Help
---

### Post by Vadi on 2008-12-25
Hi,

How can I find out if my dvd burner supports dual layer capability? The labels are worn, and k3b is not an option.

Thanks!

---

### Post by mc4man on 2008-12-25
sudo lshw -C disk should give you the model number, then search on internet.

Otherwise ImgBurn running in wine will give you complete listing of read, write capabilities, see ex.

---

### Post by Vadi on 2008-12-25
I have a feeling that it is not working, I couldn't find the option to check capabilities. Also got this in the log:

---

### Post by cariboo on 2008-12-25
Just as a point of interest, there is a gui version of lshw available in the repositories. Once installed it shows up as System-->Prefences-->Hardware Lister. The launcher should be edited to run as root. To do this right-click Applications and select Edit Menus, then click Preferecers. Next right-click Hardware Lister and select properties. In the command box add gksu in front of lshw-gtk.

Jim

---

### Post by mc4man on 2008-12-25
> I couldn't find the option to check capabilities. Also got this in the log:

> No devices detected
In winecfg you need to click the drives tab, 'autodetect' or ...

 Wine seems to have some issues with 'keeping' drives listed, if you have blank or an audio cd inserted it may 'lose' the drive.

I mainly use wine for ImgBurn, to bypass any wine drive settings and or issues I change the io in Imgburn from the default to ASPI-Winaspi32 (tools -> settings -> I/O (screenshot

To ck. capabilities, switch mode in upper task panel to 'write', then Tools -> drives -> capabilities

I also hate the 'easy'picker' mode, switch in tools -> settings -> events -> on start up, to the 'most recently used' (screen ( also choice to create iso to 'device' or 'image file' To device means 'burn on the fly', no seperate .iso created.


Though not much interest here Imgburn is vastly superior to any other iso/creator burning app or prog. (I have a 99% success rate, only fails on the occasional 'bad' blank.


Note: will gladly help anyone interested in using ImgBurn
As far as dual layers it's not even close


Edit:
> gui version of lshw available

Interesting, have to ck. There's also a gui 'sysinfo' in repo

---

### Post by Vadi on 2008-12-25
I tried that, however option is still disabled: [http://www.ubuntu-pics.de/bild/7585/screenshot_100_104__OBxLPj.png](http://www.ubuntu-pics.de/bild/7585/screenshot_100_104__OBxLPj.png)

---

### Post by mc4man on 2008-12-26
> I tried that, however option is still disabled

You have to get out of the 'easy picker mode'

Click on 'mode', choose 'write' and then the option will be there

I'll edit in screen if needed

---

### Post by Vadi on 2008-12-26
Thanks, found it. I guess my drive does support it.

So would ImgBurn work for burning a dual layer DVD then? Even via Wine?

---

### Post by mc4man on 2008-12-26
> So would ImgBurn work for burning a dual layer DVD then? Even via Wine? 

Works great.

You can use an existing .iso but better to let ImgBurn build the iso from a video_ts and then burn.

Refer to earlier screenshoot about the 'burn on the fly" (output to device) or the 'output to image file (.iso) setting.

I prefer to build an iso and then burn.
When you build a dual layer .iso a .mds file is created along with the .iso
That's what you load when burning (write mode) Though if you load the .iso Imgburn will correct for you.

When doing a dual layer you have to choose the layer break position, Imgburn will list all possible positions, rate them, and you can preview the layer break if wished

Some good reading

[http://forum.imgburn.com/index.php?showforum=4](http://forum.imgburn.com/index.php?showforum=4)

At first Imgburn seems complicated, actually very easy once you've tried.

---

### Post by Vadi on 2008-12-26
Thanks for your help.

---

