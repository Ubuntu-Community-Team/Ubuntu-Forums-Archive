---
title: "Run memtest from LiveUSB?"
date: 2009-06-08
forum: General Help
---

### Post by MaxRabbit on 2009-06-08
I downloaded and installed the LiveCD for Ubuntu and put it on my thumb drive. However, what I really wanted to do was run memtest. Is there a way to do that from the LiveCD? I don't want to install Ubuntu on my netbook, though I love it to death :)

Thanks for your help!
MaxRabbit

---

### Post by boof1988 on 2009-06-08
You may be able to use one of the USB startup utilities (unetbootin etc.) to install any number of livecd's (which have the memory test included in the boot menu) to a USB-flash-drive.

Here's a couple links (among other sites) that may be helpful...
[http://www.memtest86.com/](http://www.memtest86.com/)
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

Edit:
Doesn't the LiveCD of Ubuntu (the one you already installed on a USB-Flash) have the memtest option?

---

### Post by MaxRabbit on 2009-06-08
> **boof1988 said:**
> 
Edit:
Doesn't the LiveCD of Ubuntu (the one you already installed on a USB-Flash) have the memtest option?

That's what I'm asking! I don't know how to find it!

And unfortunately, memtest won't run after I install it with Unetbootin :(

---

### Post by Yellow Pasque on 2009-06-08
There should be an option on the main LiveCD menu for memtest. Also, some recent systems have an option in the BIOS to run memtest on the next boot.

---

### Post by MaxRabbit on 2009-06-08
> **Temüjin said:**
> There should be an option on the main LiveCD menu for memtest. Also, some recent systems have an option in the BIOS to run memtest on the next boot.

The LiveCD doesn't have a menu! It just goes right into Ubuntu itself.

---

### Post by boof1988 on 2009-06-08
> **MaxRabbit said:**
> And unfortunately, memtest won't run after I install it with Unetbootin :(

Have you tried installing the [GPartEd liveUSB image](http://gparted.sourceforge.net/download.php) on a USB-Flash drive (provided you have one to spare)?  It should have the memtest included.

This might be an option if there aren't any other (better) ideas.

> **MaxRabbit said:**
> The LiveCD doesn't have a menu! It just goes right into Ubuntu itself.

This seems strange...  When I have used unetbootin to make a liveUSB, it has usually given a boot menu to choose which feature to use.  So I don't know why there is no boot menu.

I wish I could help more... but I'm not sure how to trouble-shoot the lack of a boot menu on your liveUSB.

---

### Post by anjilslaire on 2009-06-08
Correct. The LiveCD *does* have a menu.
"Try Ubuntu without installing"
"Install Ubuntu"
Check CD for defects"
"Memtest x86"

If you're getting that upon booting the CD, something is not right.

---

### Post by MaxRabbit on 2009-06-09
> **boof1988 said:**
> Have you tried installing the [GPartEd liveUSB image](http://gparted.sourceforge.net/download.php) on a USB-Flash drive (provided you have one to spare)?  It should have the memtest included.

This might be an option if there aren't any other (better) ideas.
I greatly appreciate the suggestion! I really **only** care about memtest-but the problem is that I can't boot memtest itself from USB, and I can't find a distro that has a working copy (granted, I've only tried a few). I tried your suggestion of Gparted, but I get an error that saids "cannot load a ramdisk with an old kernel image"... I've tried googling that error with no success :(

> **anjilslaire said:**
> Correct. The LiveCD *does* have a menu.
"Try Ubuntu without installing"
"Install Ubuntu"
Check CD for defects"
"Memtest x86"

If you're getting that upon booting the CD, something is not right.
Perhaps Unetbootin removes that menu (even though boof1988 said it shouldn't)? When I boot off my USB, it simply comes up with a menu that has the choice "Default". I click default and it loads up into the LiveUSB instantly...

---

### Post by Yellow Pasque on 2009-06-09
Did you look in the BIOS?

---

### Post by boof1988 on 2009-06-09
> **MaxRabbit said:**
> I greatly appreciate the suggestion! I really **only** care about memtest-but the problem is that I can't boot memtest itself from USB, and I can't find a distro that has a working copy (granted, I've only tried a few). I tried your suggestion of Gparted, but I get an error that saids "cannot load a ramdisk with an old kernel image"... I've tried googling that error with no success :(

Yeah... Sorry about that... After some messing about, I tried my GPartEd LiveUSB and (it seems) I get the same error when I try to use the memtest.


> **MaxRabbit said:**
> Perhaps Unetbootin removes that menu (even though boof1988 said it shouldn't)? When I boot off my USB, it simply comes up with a menu that has the choice "Default". I click default and it loads up into the LiveUSB instantly...

Sorry I can't help any further with this.

Tell me which Ubuntu you downloaded and I'll (download it) and load it on a USB (using unetbootin) and see if I can duplicate your problem of *no boot menu*.

---

### Post by MaxRabbit on 2009-06-09
> **Temüjin said:**
> Did you look in the BIOS?
I'm afraid memtest isn't built-in, no - but thanks for the suggestion!
> **boof1988 said:**
> Yeah... Sorry about that... After some messing about, I tried my GPartEd LiveUSB and (it seems) I get the same error when I try to use the memtest.
Okay, that at least narrows it down a little bit. Still, great suggestion :)
> **boof1988 said:**
> Tell me which Ubuntu you downloaded and I'll (download it) and load it on a USB (using unetbootin) and see if I can duplicate your problem of *no boot menu*.
If you're sure that you don't mind doing this much work for little ol' me, [this is the release.](http://mirrors.portafixe.com/ubuntu/releases/jaunty/ubuntu-9.04-desktop-i386.iso) It's just a normal mirror that I found from the "Download Ubuntu" website for the x86 PC desktop 9.04 desktop version.

---

### Post by boof1988 on 2009-06-09
> **MaxRabbit said:**
> If you're sure that you don't mind doing this much work for little ol' me, [this is the release.](http://mirrors.portafixe.com/ubuntu/releases/jaunty/ubuntu-9.04-desktop-i386.iso) It's just a normal mirror that I found from the "Download Ubuntu" website for the x86 PC desktop 9.04 desktop version.

I already have *ubuntu-9.04-desktop-i386.iso* downloaded so I'll try to get working on this later on today.

Did you check the md5sum of the file *ubuntu-9.04-desktop-i386.iso* after you downloaded it?  If the md5sum does not match, that could potentially cause some problems.

The md5sum of your *ubuntu-9.04-desktop-i386.iso* should match...
```
66fa77789c7b8ff63130e5d5a272d67b *ubuntu-9.04-desktop-i386.iso
```

If you are using Windows, and you need a program to hash the md5sum, try [WinMD5Sum](http://www.nullriver.com/products/winmd5sum).  There are other md5sum options listed in first reference link below.

References:
[https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM on Windows](https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM on Windows)
[http://www.nullriver.com/products/winmd5sum](http://www.nullriver.com/products/winmd5sum)

---

### Post by MaxRabbit on 2009-06-09
Yep, they're the same!

---

### Post by MaxRabbit on 2009-06-10
Any more help?

---

### Post by misiu_mp on 2009-09-06
Ive noticed this too.

You cant start memtest from the usb stick created with unetbootin.
It says "cannot load a ramdisk with an old kernel image". 

I tried with several images - with linux mint and fedora.
And yes - all of the images I tried are 100% correct.

The memtest image seems to be on the stick when the contents of it is examined.

This is an issue with unetbootin, isolinux or memtest, not specific to ubuntu, so this discussion should be moved to a different forum, unless someone have the solution.

---

### Post by misiu_mp on 2009-09-06
Ok, ive found the cause:

When booting to memtest, no initrd image should be loaded.

To try it out, when the unetbootin menu pops out, edit the memtest entry (press tab) by removing "initrd=/ubninit".

To permanently fix your usb stick edit syslinux.cfg in the root of the drive and remove the line 
"append initrd=/ubninit" 
from the memtest entry.

Apropos, parted magic's livecd installs correctly with unetbootin with no changes required. 
I suspect it is because it already has a syslinux directory in it, which unetbootin recognizes and copies its config.

Hope that helps.

---

### Post by MaxRabbit on 2009-09-08
> **misiu_mp said:**
> Ok, ive found the cause:

When booting to memtest, no initrd image should be loaded.

To try it out, when the unetbootin menu pops out, edit the memtest entry (press tab) by removing "initrd=/ubninit".

To permanently fix your usb stick edit syslinux.cfg in the root of the drive and remove the line 
"append initrd=/ubninit" 
from the memtest entry.

Apropos, parted magic's livecd installs correctly with unetbootin with no changes required. 
I suspect it is because it already has a syslinux directory in it, which unetbootin recognizes and copies its config.

Hope that helps.
Finally, a fix, all these months later! :guitar:

---

