---
title: "Photoshop 4 linux?"
date: 2006-05-15
forum: Desktop Environments
---

### Post by rootmaster23 on 2006-05-15
Hi!

Can you tell me if there is any chance embedding my old win-photoshop 7.0 into my ubuntu?
Or is there a special photoshop 4 linux?

(need to be photoshop because of compatibility)

Thnx
Markus

---

### Post by Scunizi on 2006-05-15
Look in Synaptic for Gimp. Or visit them at [http://www.gimp.org/](http://www.gimp.org/).  I've read that there is a plug in available called Gimp-shop that will make the controls mirror Photoshop.  It's a great program.  Maybe not totally up to Photoshop pro's speed but more than capable for most user's needs.

---

### Post by K.Mandla on 2006-05-15
Ditto that. GIMPshop makes everything easy for the Photoshop-inclined. We use it at work so the graphic artist doesn't freak out because he can't find the filter he wants. (And because it's thousands of dollars cheaper than the actual Photoshop program, but that goes without saying. ...)

---

### Post by NeghVar on 2006-05-15
Photoshop 7 is 'certified' by wine to work with wine. There is some discussion that CS2 will work with the latest wine but I've never had any luck.

Also for all of you lovers of gimp and gimp shop, until gimp creates a single window environment I won't even consider it, its ridiculous that I have to use a completely seperate workstation to do any type of editing.

---

### Post by rootmaster23 on 2006-05-16
Thank you thank you thank you!

Some nice hints!

Greez!
Markus

---

### Post by Scunizi on 2006-05-16
If you're going to attempt to use wine and load Photoshop 7.  Come back for wine help or do a referance on the forum.

---

### Post by ComplexNumber on 2006-05-16
**rootmaster23**
you can get photoshop plugins for GIMP.

---

### Post by DarkStarDeity on 2006-05-16
Does GIMPshop do the automated batch tasks that photshop does - specifically, does it do the one that automatically generates a html photo album?

---

### Post by stealth_gsx1300r on 2006-05-17
I think you can download scripts for gimp that will do batch tasks for you.  I am not sure, but there are other tools that will generate html galleries for you.  I believe gthumb or f-photo can do it for you.

---

### Post by DarkStarDeity on 2006-05-20
Where can I get the GIMP-shop plugin? I can't find anything like it in Synaptic.

---

### Post by jreyst on 2006-05-21
Personally, coming from an amateur Photoshop user, Gimp is a major pain in the *** to use. No offense or anything, but its just a major pain. Everything I am comfortable doing easily in PS just plain doesn't work in Gimp. I'd recommend installing Crossover Office and then install PS that way.

---

### Post by Aggienator on 2006-07-06
I've never been a huge photoshop user, (couldn't afford it) and tried The Gimp back at v 1. - but gave up. Recntly I've started using 2.2 on Ubuntu and am finding that with the help of the many available on-line tutorials it is quite easy and effective.
I would definitely recommend a look at 2.2 if you haven't tried it for a while.

---

### Post by Regenerate on 2006-07-07
Hi,

when trying to install photoshop cs2 with wine it fails. After giving the wine setup.exe command I get the following:```
fixme:ole:OleCreate
        {8856f961-340a-11d0-a96b-00c04fd705a2}
        {00000112-0000-0000-c000-000000000046} semi-stub!
err:x11drv:X11DRV_CreateWindow invalid window width 1764732
err:x11drv:X11DRV_CreateWindow invalid window height -2111801805
err:ole:CoGetClassObject class {4955dd33-b159-11d0-8fcf-00aa006bcc59} not regist
ered
err:ole:CoGetClassObject no class object {4955dd33-b159-11d0-8fcf-00aa006bcc59}
could be created for for context 0x1
fixme:ole:CoCreateInstance no classfactory created for CLSID {4955dd33-b159-11d0
-8fcf-00aa006bcc59}, hres is 0x80040154
regenerate@ubuntu:/media/cdrom$ fixme:msi:MsiGetProductInfoW L"{236BB7C4-4419-42
FD-0409-1E257A25E34D}" L"PackageCode" 0x7fd4ab10 0x7fb9d864
fixme:msi:MsiInstallProductW L"Z:\\media\\cdrom0\\Adobe(R) Photoshop(R) CS2\\Ado
be Photoshop CS2.msi" L" SETUPEXEDIR=\"Z:\\media\\cdrom0\\Adobe(R) Photoshop(R)
CS2\""
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"ValidateProduc                                                              tID"
fixme:keyboard:X11DRV_GetKeyboardLayout couldn't return keyboard layout for thre                                                              ad 0012
fixme:keyboard:X11DRV_ActivateKeyboardLayout 0x4130413, 0000: stub!
fixme:ole:OleCreate
        {8856f961-340a-11d0-a96b-00c04fd705a2}
        {00000112-0000-0000-c000-000000000046} semi-stub!
err:x11drv:X11DRV_CreateWindow invalid window width -2587516
err:x11drv:X11DRV_CreateWindow invalid window height -2108393933
err:ole:CoGetClassObject class {4955dd33-b159-11d0-8fcf-00aa006bcc59} not regist                                                              ered
err:ole:CoGetClassObject no class object {4955dd33-b159-11d0-8fcf-00aa006bcc59}                                                               could be created for for context 0x1
fixme:ole:CoCreateInstance no classfactory created for CLSID {4955dd33-b159-11d0                                                              -8fcf-00aa006bcc59}, hres is 0x80040154
err:msi:msi_dialog_bitmap_control Failed to load bitmap (null)
err:msi:msi_dialog_bitmap_control Failed to load bitmap (null)
err:msi:msi_dialog_bitmap_control Failed to load bitmap (null)
err:msi:ITERATE_Actions Execution halted, action L"AMT_WriteRemoveFileEntry" ret                                                              urned 1603
err:msi:ITERATE_Actions Execution halted, action L"ExecuteAction" returned 1603
fixme:msi:msi_dialog_set_control_condition Unhandled action L"Default"

```

Any ideas on solving the problem? Thanks in advanced!

---

### Post by dyssident on 2006-07-08
> **Regenerate said:**
> when trying to install photoshop cs2 with wine it fails.

Unfortunately, install on Ubuntu doesnt currently work. [See this thread.](http://appdb.winehq.org/appview.php?iVersionId=2631)

But if you have a Windows install handy, you can apparently copy the installed files and get it to work on Linux. Ive just now started trying to get it going, so I will report back on progress.

---

