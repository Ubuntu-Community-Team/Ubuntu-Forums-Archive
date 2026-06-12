---
title: "nVidia Dual cards/sli problems"
date: 2008-12-12
forum: General Help
---

### Post by mr_finn on 2008-12-12
Hi guys :)

I'm having some trouble installing my graphics drivers here and need a bit of advice please.

I have had a forced abstinance from Ubuntu for the past 4 months or so due to not having a proper internet line and not being able to figure out how to connect using my nokia n95 as a modem, which I could do easily in windows.

Anyway, during that time I added another graphics card so am currently running 2x MSI NX8600 GTS's in SLI.

I have thrice now installed Ubuntu Ultimate Edition v2 on this machine and everything works flawlessly until I install the nvidia driver(1.77). The driver downloads and installs fine but when I reboot I get the linux equivalent of the blue screen of death.

It tells me that the xorg file cant load and the error is along the lines of 'No screens present'.

I have already installed Ultimate Edition v2 and the graphics drivers on this machine with only one card in it with no problems at all so I guess it has to be something to do with having 2 cards in there.

Is there anything I need to know/do in order to get this working?

I have Ultimate Edition freshly installed now and don't really want to screw it up again by installing the drivers.

Any insights will be greatly appreciated.

Thank you for taking the time to read this.

:)

Also, I cant get Envy working, I can install it using the packege manager and there it is in the System Tools menu but when I click on it, nothing happens.

Also, I am running Ultimate Edition v2 x64.

---

### Post by pedro_orange on 2008-12-12
What do you xorg.conf files say?

There should be something say something like:

```
Option "SLi" "yes"
```

And what do you mean Blue screen of death? You should be able to boot in low graphics mode to check config files etc.

The README that comes with the drivers from the nVidia website have some valuable information within them if you would care to read them.

---

### Post by mr_finn on 2008-12-12
My hardware is as follows:

Motherboard: Gigabyte GA-M57SLI-S4 (2 PCI, 3 PCI-E x1, 2 PCI-E x16, 4 DDR2 DIMM, Audio, Gigabit LAN, IEEE-1394)
Processor: DualCore AMD Athlon 64 X2, 2800 MHz (14 x 200) 5600+
Motherboard Chipset : nVIDIA nForce 570 SLI, AMD Hammer
Memory: Corsair 4GB (2x2GB) DDR2 800MHz/PC2-6400 XMS2 Memory
Display: 2x MSI GeForce nx8600 GTS Overclocked Edition (256 MB)
Monitor: Samsung SyncMaster 205BW/MagicSyncMaster CX203BW (Analog) [20" LCD] (HS8LA04989)
Audio Adapter: (onbaord) Realtek ALC883 @ nVIDIA nForce 570 SLI (MCP55P) - High Definition Audio
Disk Drive: ST316081 1AS SCSI Disk Device (160 GB, 7200 RPM, SATA-II)
Disk Drive: WD 5000AAK External USB Device (465 GB, USB)
Disk Drive: WDC WD25 00KS-00MJB0 SCSI Disk Device (232 GB)
Optical Drive: HL-DT-ST DVD-RAM GSA-H55N ATA Device
Optical Drive: Optiarc DVD RW AD-7170S SCSI CdRom Device (DVD+R9:8x, DVD-R9:8x, DVD+RW:18x/8x, DVD-RW:18x/6x, DVD-RAM:12x, DVD-ROM:16x, CD:48x/32x/48x DVD+RW/DVD-RW/DVD-RAM)

I was able to boot and install Ultimate Edition from the live disk no problem. While running the live disk the screen res was correct at 1680x1050.
However once I booted to the installed OS the res was greatly reduced.

I updated the system which was 212 updates and restarted the machine. All good so far.

Then I installed the nvidia graphics drivers using the System/Admin/Hardware/Activate Recomended method.

After the required reboot I get this:

[http://tinypic.com/view.php?pic=28v6iqc&s=4]("http://tinypic.com/view.php?pic=28v6iqc&s=4")

Followed by this:

[http://tinypic.com/view.php?pic=2dl6u0l&s=4](http://tinypic.com/view.php?pic=2dl6u0l&s=4)

I managed to boot from the live disk once and opened the xorg.conf file but did not get copy of it. It had very little in it though and looked nothing like it should do from previous memory.

Now when I try to boot from the live disk in standard boot or graphics safe boot methods I get and endlesss scroll of this:

[http://tinypic.com/view.php?pic=wlrjoh&s=4](http://tinypic.com/view.php?pic=wlrjoh&s=4)

I know that removing one of the cards would fix this but I am reluctant to do so.

Can anyone help please? 

:)

---

### Post by mr_finn on 2009-02-20
I found a fix for this issue, sorry about the double post but I wanted others to see it.

This is a real solution. and it is as follows. When you boot and it tells you fatal error no screens found that means you are most likely using an SLi setup and the Intrepid OS doesnt know which card to chose by default, so it chooses none.(stupid i agree) anyway the fix is as follows. You need to figure out which bus the card is on and insert it into the xorg.



basically load up your ubuntu from grub into rescue/recovery mode. then choose the root shell option. Once there type the following command



Code: Select all

    sudo lspci | grep VGA







the output should look similar to mine



03:00.0 VGA compatible controller: nVidia Corporation GeForce 8800 GT (rev a2)

04:00.0 VGA compatible controller: nVidia Corporation GeForce 8800 GT (rev a2)



now those numbers in the front are bus ID's so you need to insert them into your xorg.conf under the device section. to do so type ine



Code: Select all

    nano /etc/X11/xorg.conf







Section "Device"

Identifier "Configured Video Device"

[COLOR="Red"]Busid "PCI:3:0:0"[/COLOR]

Driver "nvidia"

EndSection



the part in red is what you need to insert. your numbers will probably be different. (if the first one doesnt work try the 2nd) then just "ctrl+x" to exit and hit "Y" to save.

then type



Code: Select all

    sudo reboot



and you are done. worked for me pretty straight fwd. Hope you have success also. :)

All credit to the original unknown (to me) poster.

---

### Post by spliffeh on 2009-02-23
> **mr_finn said:**
> (stupid i agree) anyway the fix is as follows. 

_Extremely stupid_. The fix has not worked for me, and shouldn't be needed in the first place. I am switching to an SLI friendly linux distro, smell you later Ubuntu 8.10....

---

