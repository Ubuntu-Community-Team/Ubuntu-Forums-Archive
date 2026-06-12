---
title: "hdparm"
date: 2006-01-09
forum: General Help
---

### Post by BrokeBody on 2006-01-09
OK, this is the current situation:
```
stefan@stefan:~$ sudo hdparm /dev/hda
Password:

/dev/hda:
 multcount    =  16 (on)
 IO_support   =  1 (32-bit)
 unmaskirq    =  1 (on)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 65535/16/63, sectors = 78177792, start = 0
stefan@stefan:~$ sudo hdparm /dev/hdc

/dev/hdc:
 IO_support   =  1 (32-bit)
 unmaskirq    =  1 (on)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Invalid argument
stefan@stefan:~$ sudo hdparm /dev/hdd

/dev/hdd:
 IO_support   =  1 (32-bit)
 unmaskirq    =  1 (on)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Invalid argument
stefan@stefan:~$
```

When I restart my computer, this is what happens:
```
stefan@stefan:~$ sudo hdparm /dev/hda
Password:

/dev/hda:
 multcount    =  0 (off)
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 65535/16/63, sectors = 78177792, start = 0
stefan@stefan:~$ sudo hdparm /dev/hdc

/dev/hdc:
 IO_support   =  1 (32-bit)
 unmaskirq    =  1 (on)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Invalid argument
stefan@stefan:~$ sudo hdparm /dev/hdd

/dev/hdd:
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  0 (off)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Invalid argument
stefan@stefan:~$
```

I know that I must edit /etc/hdparm.conf script so this could take effect, but I don't know what to type in that script? Can someone help me with this?

---

### Post by bored2k on 2006-01-09
[CENTER]**[https://wiki.ubuntu.com/DMA](https://wiki.ubuntu.com/DMA)**[/CENTER]

However, in order for the settings to be automatically applied at boot there you need to edit the /etc/hdparm.conf} script. To do this use this command: ```
sudo gedit /etc/hdparm.conf
```

Add the following to the end of your hdparm.conf
```

/dev/hdc {
dma = on
}
```
         
[/list]
**Troubleshooting**

If your drives are configured in [Cable Select] mode and while running hdparm commands you receive errors related to timeouts or drive not ready, try changing the drive to be a master or slave device depending on your system configuration. This does require opening the case and as far as I know most drives are set to Cable Select from the manufacturer.

Sometimes step 3 above can fail with a "operation not permitted" message. You can fix this by editing the file /etc/modules: For an intel cpu put the lines

```
piix

ide-core

above the line

ide-cd

```
For an amd cpu put the line
```

amd74xx

above

ide-cd

```
For a VIA Chipset put
```

via82cxxx

above

ide-cd
```

Then reboot and try steps 3-4 again....

---

### Post by BrokeBody on 2006-01-09
DOOh! I already read that from the documentation. And do you even read?!? You just copy/paste-d the example for hdc and hdc is just fine after the reboot. hda and hdd aren't! [IMG]http://www.linuxo.org/modules/Forums/images/smiles/icon_rolleyes.gif[/IMG]

---

### Post by dcstar on 2006-01-09
[QUOTE=BrokeBody]DOOh! I already read that from the documentation. And do you even read?!? You just copy/paste-d the example for hdc and hdc is just fine after the reboot. hda and hdd aren't! [IMG]http://www.linuxo.org/modules/Forums/images/smiles/icon_rolleyes.gif[/IMG][/QUOTE]
"HDIO_GETGEO failed: Invalid argument" means there is no CD/DVD in the drive to get any geometry - don't try and use invalid default hdparm commands for removable drives.

---

### Post by cosimo on 2006-01-19
Hello all
 i have a client that I switched from xp to ubuntu, everything is going well except for one thing.
 When he trys to burn a cd, using gnomebaker, the system freezes. 
I then asked him, over the phone to go to terminal and type hdparm /dev/hdc.
 My hdparm is;

/dev/hdc:
 IO_support   =  1 (32-bit)
 unmaskirq    =  1 (on)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Invalid argument

His hdparm, same identical install as mine is;
IO_support = 0 (16-bit)
unmaskirq = 0 (off)
using _dma = 1 (on) 
keepsetting = 0 (off)
readahead = 256 (on)
HDIA_GETGEO failed: Invalid argument
Ineed to knew several things;
First the cd burner worked fine in Ubuntu at first, but then we are not sure because he simply copied the files he wanted recorded, and left ther oom for several hours so we have no idea what was going on. hementioned that the cd burner was making noise lately. That worried me because it could be the cd burner. I need some input here for both opinions on the possible cause for the hdparm /dev/hdc changing from what it was in mine to what it is now in his and second can a dieing cdr do similar things including taking up all system resources so that not even the mouse will respond.?
 Third, are therea ny urls that cn be viewed that migiht help with this situation?
 i have looked nad even printed out the man hdparm .
Any suggestions woul be well appreciated, even though I was comitted to uninstall ing ubuntu for all of my clients this one refused the switch abck to XP
 thanks ahead of time.
 Coz

---

