---
title: "x61 tablet features configurations?"
date: 2009-04-25
forum: Desktop Environments
---

### Post by daniele.rosa on 2009-04-25
I have Ubuntu 9.04 the Jaunty Jackalope - released in April 2009

To get the tablet functionality working i followed the thread

[http://ubuntuforums.org/showthread.php?t=604896](http://ubuntuforums.org/showthread.php?t=604896)

(without changing the DRI option in xorg.conf)

I was wondering if anybody knows how to fix these:

- when the laptop is in tablet mode, the cursor goes left and right instead of up and down and viceversa. The xsetwacom list does not find any device.

- touching the screen with the finger the cursor is a little off with respect to the finger position and the problem seems to be symmetrical with respect to the screen center; in the center the error is zero and increase as you move toward the screen sides

- at login, the onboard utility covers the text input field

I saw that the xorg.conf concept has changed a little. In the file xorg.conf there is very little stuff with respect to before but there are more file in the directory /etc/X11.

Here is my lspci:

daniele@daniele-laptop:~$ lspci 
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:19.0 Ethernet controller: Intel Corporation 82566MM Gigabit Network Connection (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HBM (ICH8M-E) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
03:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
05:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ba)
05:00.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 04)
05:00.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 21)

---

### Post by Favux on 2009-04-25
Hi daniele.rosa,

Assuming you are running the "native" Jaunty 0.8.2-2 linuxwacom drivers you should know that they have been specially patched by Timo Aaltonen to work with HAL/.fdi and Xserver 1.6.  So you can't use xorg.conf, you have to use the 10-wacom.fdi.  Unfortunately as you discovered the callout in the .fdi file is returning HAL/D-BUS names that linuxwacom doesn't recognize, hence no xsetwacom (rotation of wacom devices) and no calibration with wacomcpl.  Rec figured this out and wrote a script to translate things so linuxwacom can understand them.  See Jaunty Users here:  [http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949)  There is a link to a HOW TO on installing the script.  Since you have a serial tablet you can ignore the stuff about compiling 0.8.3-2 wacom.ko.  Or as the Jaunty Users says you could compile 0.8.3-2 and probably use xorg.conf.

Also Timo posted a ppa a few days ago for xorg-xserver that I think fixes the names problem.  No telling when that will come out though.

Hope this helps.

---

### Post by daniele.rosa on 2009-04-26
Thank you! It helped.

The "touch" is still off calibration but I'll have to look at it later.

Daniele

---

### Post by SaintDanBert on 2009-09-01
Ms. Danielle,
   I have an X61 but I am still running Hardy.
I'd like to update but have not seen a clear path to success. I would appreciate directions to a clearly marked road. The X61 is a known beast, I would think things would be very clear by now but I don't see it.

1.  I have the Jaunty media burned.
QUESTION: Do I install fresh or upgrade?

2.  Do I need any magic steps or settings during the install itself?

3.  After install but before real use, Do I need any special supporting packages or patches downloaded and installed?

4.  With everything loaded at long last, what special configuration makes things work really well? [For example, I'd like 3D effects and tablet to play nicely, but a clean toggle where 3D works in laptop mode and is off in tablet mode is okay. Also, I'd like to be able to swap an HDD into the ultrabay without reboot.]

Thanks,
~~~ 0;-Dan

---

### Post by SaintDanBert on 2009-09-01
> **SaintDanBert said:**
> 
Ms. Danielle


Sorry that I misspelled your name, Daniele

---

### Post by Favux on 2009-09-02
Hi SaintDanBert,

While you're waiting for Daniele.

1) I don't think you can upgrade directly from Hardy to Jaunty.  I think you have to go to Intrepid first.  You could check that out on the Install and Upgrades forum.

2) I don't know for sure.  Other than possibly Intel video I don't think so.

3) The tablet works out of box except for the linuxwacom names thing.  That's the link to rec's script in Jaunty Users I gave.  That let's you use wacomcpl to calibrate and set up your stylus button.

Some links:

[http://www.thinkwiki.org/wiki/Installing_Ubuntu_9.04_(Jaunty_Jackalope)_on_an_X61_Tablet](http://www.thinkwiki.org/wiki/Installing_Ubuntu_9.04_(Jaunty_Jackalope)_on_an_X61_Tablet)  from here:  [http://www.thinkwiki.org/wiki/Category:X61_Tablet](http://www.thinkwiki.org/wiki/Category:X61_Tablet)

And:  [http://www.geedew.com/x61-tablet-ubuntu/](http://www.geedew.com/x61-tablet-ubuntu/)

Hope this helps you.

---

