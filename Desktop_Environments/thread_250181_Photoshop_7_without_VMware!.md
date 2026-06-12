---
title: "Photoshop 7 without VMware!"
date: 2006-09-03
forum: Desktop Environments
---

### Post by cypher35 on 2006-09-03
I've finally gotten rid of the only obstacle holding me back to dual-booting/emulating windows...  Photoshop 7 now works almost flawlessly under wine.  (hopefully CS will follow)

I followed [this](http://www.ubuntuforums.org/showthread.php?t=149585) tutorial to set up wine, then proceeded to upgrade using [wine_0.9.19~winehq0~ubuntu~6.06-2_i386.deb](http://wine.budgetdedicated.com/archive/ubuntu/dapper/wine_0.9.19~winehq0~ubuntu~6.06-2_i386.deb). (0.9.20 is the newest, but the compatability list on their website indicates that it works better in 0.9.19)  Luckily dispite having acquired Photoshop CS some time ago, i still had a copy of PS 7 lying around.  I popped the cd in and ran the installer.  It worked like a charm.

After playing around with it for a little while, using photoshop I threw together a quick png with transparency ([photoshop.png](http://www.ninjazombie.net/uploads/cypher35/temp/photoshop.png)) and made an icon shortcut with it.
[img]http://www.ninjazombie.net/uploads/cypher35/temp/photoshop.png[/img]

It is important to note that in order to get some common filters and dialogs to work (such as "Save As For Web") you need to make sure you launch the app with a **c:/** directory path using **back slashes**.  For instance:
```
[font=Courier]wine "c:\Program Files\Adobe\Photoshop 7.0\Photoshop.exe"[/font]
```
as opposed to a direct path such as:
```
[font=Courier]wine "/home/mike/.wine/drive_c/Program Files/Adobe/Photoshop 7.0/Photoshop.exe"[/font]
```
Both will launch the application, but only the first one will allow you to use filters and "save as for web".


Also, if you are running KDE, you may want to diable "global shortcuts" for this application window so that you can use the alt modifier for things such as subtracting selections.

[img]http://www.ninjazombie.net/uploads/cypher35/temp/photoshop.jpg[/img]

---

### Post by Magiczero on 2006-09-03
This is awesome!  I am a student at a school in IL and I am in a wheelchair and i use Photoshop on my laptop at my Highschool!  I love Photoshop!

---

### Post by leveliv on 2006-11-08
> leveliv@leveliv-desktop:~$ wine "c:\Program Files\Adobe\Photoshop 7.0\Photoshop.exe"
fixme:actctx:QueryActCtxW 80000010 0x116283c (nil) 1 0x33fdc4 8 (nil)
X Error of failed request:  BadDevice, invalid or uninitialized input device
  Major opcode of failed request:  148 (XInputExtension)
  Minor opcode of failed request:  3 (X_OpenDevice)
  Serial number of failed request:  35
  Current serial number in output stream:  35

this is what I get, then it closes.

---

### Post by leveliv on 2006-11-09
Bump Bump bUmp

---

### Post by Synikk on 2006-11-09
Bookmarked this thread. After giving both GIMP and Pixel fair tries, it looks like I'll be running PS7 in Wine anyway.

---

### Post by A3sthetix on 2007-06-08
> **leveliv said:**
> this is what I get, then it closes.

I think you might have a problem with a plugin or TWAIN device installing in your Photoshop. I would suggest installing a fresh copy of Photoshop. If you have specific feature in your Windows version you want to retain, install the fresh version into a different directory. Make sure you do not configure anything in the new installation via Windows.

Hope that works!

---

### Post by lazd on 2007-09-17
Thanks! This is exactly what I was looking for as I got photoshop 7.0 and wine playing nicely finally!

---

### Post by Chudilo on 2007-09-18
You might also want to check out Gimpshop.
it's a mod for GIMP to make all the menues to match Photoshop.

---

