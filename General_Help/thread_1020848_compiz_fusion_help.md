---
title: "compiz fusion help"
date: 2008-12-24
forum: General Help
---

### Post by boblettoj99 on 2008-12-24
Hi i am trying to get compiz working to no avail.
so far i have installed xgl, compiz + everything that comes with it, emerald and compiz kde

when i type compiz --replace i get this error:
Checking for Xgl: not present.
Detected PCI ID for VGA: 01:00.0 0300: 1002:9490 (prog-if 00 [VGA])
Checking for texture_from_pixmap: present.
Checking for non power of two support: present.
Checking for Composite extension: present.
Comparing resolution (1280x1024) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present.
Checking for FBConfig: present.
Checking for Xgl: not present.
Starting emerald
/usr/bin/compiz.real (core) - Fatal: No GLXFBConfig for default depth, this isn't going to work.
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0
exec: 378: /usr/bin/metacity: not found

this leads to no window borders and me having to replace kwin.
my graphics card is an ATI HD4670 and the graphics driver is vesa according to system settings.

can anyone help with this error, what do i need to do?
thanks

---

### Post by JECHO on 2008-12-24
> **boblettoj99 said:**
> Hi i am trying to get compiz working to no avail.
so far i have installed xgl, compiz + everything that comes with it, emerald and compiz kde

when i type compiz --replace i get this error:
Checking for Xgl: not present.
Detected PCI ID for VGA: 01:00.0 0300: 1002:9490 (prog-if 00 [VGA])
Checking for texture_from_pixmap: present.
Checking for non power of two support: present.
Checking for Composite extension: present.
Comparing resolution (1280x1024) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present.
Checking for FBConfig: present.
Checking for Xgl: not present.
Starting emerald
/usr/bin/compiz.real (core) - Fatal: No GLXFBConfig for default depth, this isn't going to work.
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0
exec: 378: /usr/bin/metacity: not found

this leads to no window borders and me having to replace kwin.
my graphics card is an ATI HD4670 and the graphics driver is vesa according to system settings.

can anyone help with this error, what do i need to do?
thanks

looks like you need to install the restricted drivers... have you done that yet?

---

### Post by boblettoj99 on 2008-12-24
when i go on restricted drivers it says i don't need any!

---

### Post by Therion on 2008-12-24
> **boblettoj99 said:**
> when i go on restricted drivers it says i don't need any!
Go back to your restricted driver manager and install the restricted driver for your ATI card.  
Simply put, if you want Compiz-Fusion to run, you'll need to install the restricted driver.

---

### Post by boblettoj99 on 2008-12-24
how do i do that?
the restricted driver manager shows no drivers to be installed

---

### Post by Therion on 2008-12-24
Your video card may not be being recognized then.  
Open a Terminal and enter:```
lspci
```
Paste the output here.

---

### Post by boblettoj99 on 2008-12-24
aha this could be something to do with it:

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Unknown device 9490
01:00.1 Audio device: ATI Technologies Inc Unknown device aa38
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)

unknown device eh? how do i make it known?

---

### Post by Therion on 2008-12-24
This thread should get you up and running.  

Roll up your sleeve's and read on...

[http://ubuntuforums.org/showthread.php?t=878709](http://ubuntuforums.org/showthread.php?t=878709)

---

### Post by boblettoj99 on 2008-12-24
that's the 4870, mine is a 4670!
appreciate the effort though :D

---

