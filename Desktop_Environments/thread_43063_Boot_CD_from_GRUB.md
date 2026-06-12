---
title: "Boot CD from GRUB"
date: 2005-06-20
forum: Desktop Environments
---

### Post by Eala on 2005-06-20
How do I get GRUB to boot a CD?  It appears it will boot from a floppy but doesn't read CDs. ](*,)

---

### Post by blind0wl on 2005-06-20
Wont be a grub related issue...just set your BIOS up to boot from CDROM first.

---

### Post by Eala on 2005-06-21
Ok, great...what exactly do I need to do to do that?

---

### Post by aglauser on 2005-06-21
[QUOTE=Eala]Ok, great...what exactly do I need to do to do that?[/QUOTE]

That depends a bit on your system - specifically on what type of BIOS you have.  When you are booting up, there should be a message on the screen saying something like: "Press **DEL** to enter setup".  Different manufacturers use different keys to enter the BIOS.  Delete and F1 are common keys.  If you don't see a message and holding down Delete or F1 while booting doesn't get you into a BIOS or "setup" screen, you will need to refer to the motherboard manual or your computer's manufacturer.

Once you get into the BIOS, look for an option like "boot priority" or "startup options".  It might be buried under another level of menus, don't be afraid to look around, but be careful not to change any of the BIOS options unless you know what you are doing.  Some of them can cause instability if changed.  Once you find the option for choosing your boot priority, follow the onscreen instructions to change the boot order so that CD comes first, then hard drive or floppy (whatever is your preference).

Good luck, and let us know how it goes.

---

### Post by Eala on 2005-06-22
Thanks Adam,

Unfortunately, while I was able to get into the Setup menu I couldn't find any options (even within submenus) that seemed to change boot priorites to include booting from the cd.  

One thing about this being a bios problem; if my bios is not configured to boot from a CD, then how was it able to initially install from the Ubuntu CD?  

All I really want to do now is go back to Red Hat (which at least I know) for the time being but I can't do that since it won't boot from a CD. And I can't download off the net since Ubuntu hasn't configured or recognized my modem.

 :roll: 
Frances

---

### Post by aglauser on 2005-06-22
[QUOTE=Eala]<snip>

One thing about this being a bios problem; if my bios is not configured to boot from a CD, then how was it able to initially install from the Ubuntu CD?  

Frances[/QUOTE]

Mmmm ... good point.  I'd still like to find out what the BIOS settings are, just to be sure.  What BIOS are you using?  It should say at the top of the setup screen.  Maybe we can help you find the option, to make sure that the option is set properly.  Also, can you read CDs when you are in Ubuntu?  Maybe there is a problem with your CD drive (loose cable, incorrect jumper settings, etc.)

Adam

---

### Post by irusun on 2005-06-22
Are you sure the CD is a bootable CD?  If you still have the Ubuntu CD, does it boot?  If other CDs boot, then it's probably the particular CD you're trying to boot.  If no bootable CDs boot, it almost has to be the BIOS or something wrong with the hardware.

---

### Post by keybreckaba on 2005-06-23
try pressing f12 when you turn your computer on i know lots of computers will bring up the boot menu to choose what you want to boot from if you press f12

---

### Post by Eala on 2005-06-23
[QUOTE=irusun]Are you sure the CD is a bootable CD?  If you still have the Ubuntu CD, does it boot?  If other CDs boot, then it's probably the particular CD you're trying to boot.  If no bootable CDs boot, it almost has to be the BIOS or something wrong with the hardware.[/QUOTE]
 D-uh oh!  I will try another CD to see if it boots.

---

### Post by Eala on 2005-06-23
In Ubuntu, it will read the Red Hat CD I am trying to boot.  It didn't start any of the other CD's I have tried - basically Ubuntu seems to have a lot of problems with my hardware.  

Here's the Info from my first message when I boot:
"Intel Book Agent Version 2.2 (0421) Setup Program"

then settings show:

Boot Protocol:                     PXE (IRPL)
PNP/BEV Boot:                    Disable (Enable)
Default Boot:                       Local (Network)
Local Boot:                          Enable (Disable)
Prompt Time:                       2
Setup Message:                  Enable (Disable)
Power Management:           ACPI

then there's a Configuration Setup Utility when I escape the "Boot Agent"  and hit Ctrl-S

It has lots of options with submenus (no nothing under "StartUP options to choose cd) such as:

System Summary
Product Data
Devices & I/O Port
Start Options
Date & Time
System Security
Advanced Setup
ISA Legacy Resources
Power Management
Save Settings
Load Default Settings
Restore Default Settings

---

### Post by dkitty on 2005-06-23
You can always create a boot floppy. The Ubuntu Hoary install disc has instructions and files for doing such a thing. I used it on a Dell that wouldn't let me alter boot options in the bios.

I created a boot floppy, slipped it into the floppy drive, and when the computer booted I was given a selections of drives to choose from. I chose the CD-rom drive containing the Ubuntu Hoary install CD. All was well from then on.

I'm not sure exactly which folder of the install CD the boot floppy files and instructions are within... perhaps a folder named install? I can look when I get home tonight if you think that would help.

---

### Post by Eala on 2005-06-23
[QUOTE=dkitty]You can always create a boot floppy. The Ubuntu Hoary install disc has instructions and files for doing such a thing. I used it on a Dell that wouldn't let me alter boot options in the bios.

I created a boot floppy, slipped it into the floppy drive, and when the computer booted I was given a selections of drives to choose from. I chose the CD-rom drive containing the Ubuntu Hoary install CD. All was well from then on.

I'm not sure exactly which folder of the install CD the boot floppy files and instructions are within... perhaps a folder named install? I can look when I get home tonight if you think that would help.[/QUOTE]
 That would be perfect if I could use the same method to create a boot floppy for my Red Hat Cd.

---

### Post by dkitty on 2005-06-23
I don't see why it wouldn't work. What processor architecture does the computer in question use? i386?

I'll write more from home (I'm at work) in about an hour or so and post the necessary files if needed.

---

### Post by dkitty on 2005-06-23
In the install directory of the Ubuntu Hoary 5.04 install cd is a file called README.sbm:

> About the Smart Boot Manager image
----------------------------------

  The file `sbm.bin' that is available in this directory may be useful
  to you if you are not able to directly boot the first CD because your
  BIOS may be too old and may not support ISOLINUX.

  Then, instead of booting on the CD directly, you create a Smart Boot
  Manager floppy image by using the sbm.bin disk image. You can create this
  floppy with rawrite (under DOS) or with dd (under Linux). Now you can
  boot on this floppy disk and it will detect your CDROM and let you boot
  on it bypassing any BIOS limitation.

What is SBM ?

  Smart Boot Manager or briefly SmartBtmgr (SBM), is an OS independent
  Boot Manager - a program that is loaded by the bios before any
  operating system and allows you to choose which operating system to
  boot.

  SBM is included in Debian in two ways, the package bmconf allows us to
  install and configure an old version of SBM and sbm wich is the latest
  version of SBM with an installer.

What's the use of SBM on the CD then ?

  SBM includes an IDE driver that allows us to boot the cds even on
  machines with a BIOS that wouldn't support booting from CD, provided our
  CDROM is an IDE one, that is, so you can make a SBM floppy and boot from
  it and then tell it to boot from your CDROM.

  Also, there are some cases where the BIOS would allow booting from the CD
  but isolinux fails to boot from there, in this case you can either boot
  using a CD other than the first, as the others don't use isolinux, or you
  can make a SBM floppy and boot from this floppy and then tell SBM to boot
  your CDROM.

How do you make a SBM floppy ?

  If you have SBM installed on a box you can run sbminst. Otherwise you can
  put the sbm.bin floppy image that we provide with our cds onto a floppy
  just like you would do with a rescue image.



I've attached sbm.bin in a zip file titled sbm-bin.zip.

---

