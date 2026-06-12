---
title: "Help installing new soundcard"
date: 2005-06-15
forum: Desktop Environments
---

### Post by Jonathan2007 on 2005-06-15
Hey. I had a SB Live sound card in my pc when I installed Kubuntu. Now I have put in a card identified as a Rockwell International PCI Audio Controller by KInfoCenter. But if I goto Sound in KInfoCenter it says no info is available about the Soundcard.

Now when I try to play stuff using Beep Media Player it gives me an error about the sound not being configured correctly.

My question is how do I get this device installed? I have heard that Ubuntu (Gnome) has a Device Manager but does Kubuntu (KDE)? And I wouldn't really call KInfoCenter one because it doesn't let you setup drivers for the stuff (that I can tell of).

If anyone can help me get sound working I would much appreciate it.

---

### Post by GTvulse on 2005-06-15
This has to do with modules loaded into the kernel at boot up time. Reading through the output of ```
dmesg | less
``` will let you know if the kernel is finding the right modules for your sound card. If it is so, do a ```
lsmod | less
``` and check /etc/modules to see if hotplug is force-loading the modules for the old SB-Live. If so, you may have a conflict you can solve editing /etc/modules to remove the SB-Live drivers, rebooting and running ```
sudo update-modules
``` afterwards. Else, you need to find out if there are linux drivers for your new sound card and load them manually by adding them to /etc/modules by hand.

---

### Post by Jonathan2007 on 2005-06-15
Ok well I tried the first 2 commands you gave me and they spit out a very long list of stuff. I tried searching for sound and nothing came up.

Then I opened up /etc/modules and here is what was in it
```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

ide-cd
ide-disk
ide-generic
lp
mousedev
psmouse
```
I don't see anything in there about my old SB Live card.

I have searched google and found out about the sndconfig tool on RedHat Linux. Does (K)Ubuntu have a tool like this?

If not can someone help me find a Linux driver for my new Rockwell soundcard (I have searched google quite a bit and haven't found anything). Thanks.

---

### Post by GTvulse on 2005-06-16
Hmmm... This is puzzling, because Conexant (formerly known as Rockwell) doesn't produce sound cards, in fact it doesn't produce consumer electronics at all. Instead it specializes in communication chipsets that are used by other manufacturers mostly of OEM computer parts. What does the output of "lspci" say? OK, you could have an old Rockwell Riptide Modem/Sound card[1], or something else, that you might be able to identify looking at the etchings on the chip[2]. But be warned, Rockwell chipsets are mostly useless under Linux due to vendor unfriendliness. If it were a winmodem, you could *buy* the drivers at [http://www.linuxant.com/](http://www.linuxant.com/). BTW, I just checked the sound drivers available in the Linux kernel 2.6.11.11 and Rockwell doesn't show up anywhere.  You may be better off reinstalling your old SB-Live...

[1] [http://www.mepis.org/node/6848](http://www.mepis.org/node/6848)
[2] [http://www.plasma-online.de/english/identify/picture/rockwell.html](http://www.plasma-online.de/english/identify/picture/rockwell.html)

---

### Post by Jonathan2007 on 2005-06-16
Hey thanks for the info. Well my dad kinda stole my SB Live card because it had digital output which he wanted for surround sound so I may just have to buy a new card.

The card is multipurpose and looks semi old (at least I know it isn't brand new). It also has a gameport/midi and a modem all along with the sound part.

The output of lspci is 
```
0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133] (rev 02)
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133 AGP]
0000:00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 22)
0000:00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 10)
0000:00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 10)
0000:00:07.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 10)
0000:00:07.4 SMBus: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 30)
0000:00:09.0 Multimedia audio controller: Rockwell International Riptide PCI Audio Controller
0000:00:09.1 Communication controller: Rockwell International Riptide HCF 56k PCI Modem
0000:00:09.2 Input device controller: Rockwell International Riptide PCI Game Controhttp://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=215588#ller
0000:00:0c.0 Ethernet controller: Lite-On Communications Inc LNE100TX [Linksys EtherFast 10/100] (rev 25)
0000:00:0d.0 Communication controller: PCTel Inc HSP MicroModem 56 (rev 01)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)
```
I am going out of town today so I may search for a newer soundcard if I can find one cheap enough.

---

### Post by GTvulse on 2005-06-16
Yup, a Riptide Sound/modem card:

```

    .
    .
    .
0000:00:09.0 Multimedia audio controller: Rockwell International Riptide PCI Audio Controller
0000:00:09.1 Communication controller: Rockwell International Riptide HCF 56k PCI Modem
0000:00:09.2 Input device controller: Rockwell International Riptide PCI Game Controller
    .
    .
    .

```

I think you'll be better off with a new card...

---

