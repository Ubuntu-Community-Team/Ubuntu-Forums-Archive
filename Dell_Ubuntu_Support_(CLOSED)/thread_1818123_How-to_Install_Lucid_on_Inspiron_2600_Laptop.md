---
title: "How-to Install Lucid on Inspiron 2600 Laptop"
date: 2011-08-04
forum: Dell Ubuntu Support (CLOSED)
---

### Post by c4c on 2011-08-04
[COLOR=#3333ff]**Install Ubuntu 10.04.02 LTS**[/COLOR]
 [COLOR=#006600]**on a Dell Inspiron 2600 Laptop**[/COLOR]
 **in three (sort of, fairly) easy steps**

**Things you will need:**

[LIST]
[*]Dell Inspirion 2600 laptop with a working floppy disk and CD drive.
[*]Access to a computer (or friend's) running Windoze for a few minutes.
[*]A Ubuntu 10.04.02 i386 Alternate Install CD and one 1.44MB floppy disk.
[/LIST]
 *Yes, there are ways to get around the things that you need, as well as different (and yes, I'm sure better) ways of doing many of the instructions below. However, I have succesfully installed Ubuntu 10.04.02 on three of these old Dell laptops in a row. So, [COLOR=#3333ff]**I know these instructions work**[/COLOR]. No matter if you are a linux guru, or a complete noob; if you follow along - you too can have Ubuntu Lucid 10.04 running on a Dell Inspiron 2600 laptop.*

**1. FLASH THE BIOS OF THE 2600 TO VERSION A08**
1a.Download the file called "I2600A08" [[ftp://ftp.dell.com/bios/I2600A08.exe]]("ftp://ftp.dell.com/bios/I2600A08.exe%5D") on a Windoze machine.
1b.Execute the file to load directly onto a 1.44MB floppy disk.
1c.Load the floppy disk into the Dell Inspiron 2600's floppy drive.
1d.Press the round silver power key of the 2600 once.
1e.You'll see a notice that this floppy is "Starting Windows 98..." and it will ask if you are sure... Press [Y].
[COLOR=#3333ff]*Watch the bios be flashed - it'll take maybe 2 minutes.*[/COLOR]
1f.The 2600 will restart; eject floppy by pressing eject button.
[COLOR=#006600][B]Keys are in brackets, e.g; [Enter] means press the Enter key, [Space] means press the Space bar.

[/B][/COLOR]**2. USING YOUR NEW BIOS AND INSTALLING UBUNTU 10.04.02**
2a.While booting (or rebooting) press and hold the "F2" key.
2b.Ensure the bios is now A08 on the "Main" tab of the first screen.
2c.Move to the "Boot" tab with the right arrow key.
2d.Move down with the down arrow to select the CD-ROM drive.
2e.Move CD-ROM to the top of the menu by tapping the [F6] key.
2f.Eject the CD drive, insert Ubuntu CD and close the CD drive.
2g.Press [F10] to (save and exit the bios and) boot with the CD.
[COLOR=#3333ff]*You'll notice scary looking horizontal lines - ignore them.*[/COLOR]
2h.Select your language and install Ubuntu.
2i.When told to, remove CD and Reboot while holding [Shift] key.

**3. CONFIGURING THE GRAPHICS WITH XORG**
3b.Keep holding [Shift] to get into the "Boot Screen"
3c.Select "Ubuntu, with Linux 2.X.XX-XX-generic (recovery mode)"[Enter]
3d.Down arrow until you select "Drop to root shell prompt"[Enter]
[COLOR=#3333ff]*Your prompt will likely be half cut-off at the top - worry not. At least the scary horizontal lines are gone.*[/COLOR]
3e.Type: sudo /etc/init.d/gdm3 stop[Enter]
*At this point, if you are adept at messing around with xorg.config files, skip 3f-3j. The working xorg.conf file starts at 3k.* It's also attached at the bottom.
3f.At next prompt type: Xorg -configure[Enter]
[COLOR=#3333ff]*Your prompt will now again be half cut-off, but this time look like a shadow, or ghost, or overlay. Again, worry not.*[/COLOR]
3g.Type: mv[Space]/root/xorg.conf.new[Space]/etc/X11/xorg.conf
3h.At next prompt type: nano[Space]/etc/X11/xorg.conf[Enter]
[COLOR=#3333ff]*Now it's the nano editor that'll look like a shadow.*[/COLOR]
3i.To make it easier to see the file, hit [Enter] once.
3j.What you see on screen is an xorg.conf file. This will not be your xorg.conf file - it is only presented so you can get a feel for the layout and if needed, replace it line-by-line, or section by section. Or, you can (and probably should) erase the whole thing.
[COLOR=#3333ff]*Your xorg.conf file will end up being much, much smaller.*[/COLOR]
3k.Type in everything exactly how you see it here:

```
Section "ServerLayout"
    Identifier    "Layout 1"
    Screen    "Default Screen"
    Option    "BlankTime" "0"
    Option    "StandbyTime" "0"
    Option    "SuspendTime" "0"
    Option    "OffTime" "0"
EndSection

Section "Device"
    Identifier    "Configured Video Device"
    Driver    "intel"
    Option    "SWCursor" "True"
    Option    "HWCursor" "False"
    Option    "monitor-LVDS" "Configured Monitor"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
    Option    "PreferredMode" "1024x768"
    Option    "DPMS"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor    "Configured Monitor"
    Device    "Configured Video Device"
EndSection
```3l.Remember back in 3i we hit [Enter] once to see the first line? Now, arrow back up to blink under the letter "S" in the very first word "Section" and hit [Backspace]
[COLOR=#3333ff]*Again, the prompt is a ghost over the nano editor options. Since it's difficult to see, just blindly follow the next two instructions.*[/COLOR]
3m.Hit [Ctrl]+[X], then [Y], then [Enter]
3n.At next prompt type: **reboot now**

[COLOR=#3333ff]**Congratulations! You've just installed Ubuntu Lucid on a Dell Inspiron 2600!**[/COLOR]

---

