---
title: "Dell Optiplex does not boot with Ubuntu 8.10"
date: 2009-03-22
forum: Dell Ubuntu Support (CLOSED)
---

### Post by astade on 2009-03-22
I own a Dell Optiflex and installed Ubuntu 8.10 a few days before.
There is an error in the boot. I get the Ubuntu splash screen and then sometimes a funny "X" cross, which could be a mouse cursor? After that the screen turns black and everything hangs (Ctrl-Alt-Backspace doesn't help ether).

I installed dual boot. If I boot into Windows and select reboot, Ubuntu runs fine! Till the next power off :-(

Any idea what I can do? My guess is a graphic driver problem. After Windows initializes everything, things run fine?
But anyhow. I've no glue how to fix this.

Regards

---

### Post by kestrel1 on 2009-03-22
When you have got into Ubuntu, have you updated it & installed any proprietary drivers?

---

### Post by LiamWilson on 2009-03-22
Not a specifically related question, but what Optiplex are you running?

//Is an Optiplex expert somewhat.

---

### Post by astade on 2009-03-22
I did:

apt-get update

Therefor it's "up do date" in my opinion.

As far as I can see, no propretary drivers.

---

### Post by astade on 2009-03-22
I'm using Optiplex GX260

---

### Post by LiamWilson on 2009-03-22
Go to Sytem > Administration > Hardware Drivers, and see if anything is activated.

---

### Post by astade on 2009-03-22
Yes, I did this.

Administration->Hardwaredrivers

says "No propretery Drivers"

(It says it in German, because I've got installed German language, but it means "no propretary driver")

---

### Post by boof1988 on 2009-03-22
> **astade said:**
> I did:

apt-get update

Therefor it's "up do date" in my opinion.

As far as I can see, so propretary drivers.

I just want to clarify (as best of my knowledge) a little about update vs. upgrade as I think it will be helpful here.

The command...

```
sudo apt-get update
```

...will only update the list of available *upgradable packages* (maybe there's a better word here?).

Either of these commands...

```
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

... will actually download and install the *upgradable packages*.

I know that the man pages can be daunting, but (for reference) more information on apt-get can be found by using...

```
man apt-get
```

...I get intimidated when I try to read it.  There have been threads which (try to) explain the difference between upgrade & dist-upgrade, but I still don't understand.

Hope this helps a bit.

---

### Post by astade on 2009-03-22
For shure you are right, concerning the apt update/upgrade stuff.
But what about my main and initial problem? What shall I do to get my system stabil?

---

### Post by ugm6hr on 2009-03-22
This sounds like a graphics card driver issue.  As for why a reboot would make it work, I'm uncertain.

Can you boot into recovery mode OK from power-on?

The details of your graphics card might help:

```
lspci
lshw -class display
```

PS: apt-get dist-upgrade is generally not recommended in Ubuntu since 6.06 (it is for Debian upgrades).

---

### Post by astade on 2009-03-22
thomas@bob:~$ lspci
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
01:0c.0 Ethernet controller: Intel Corporation 82540EM Gigabit Ethernet Controller (rev 02)
thomas@bob:~$ lshw -class display
WARNING: you should run this program as super-user.
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
thomas@bob:~$

---

### Post by astade on 2009-03-22
Indeed it could have to do with the graphic. If I try to activate "visual effects" on the desktop, I get "Could not be activated".

---

### Post by ugm6hr on 2009-03-22
Does Recovery Mode work?

In any case, I'd suggest removing compiz first to see if that helps:

```
sudo apt-get remove compiz-core
```

---

### Post by astade on 2009-03-22
This seems to help. I'll know exactly, when the system will boot tomorrow without booting Windows first.

What is this Compiz good for, when I can simply remove it without notyfying any negative effects?

---

### Post by ugm6hr on 2009-03-22
> **astade said:**
> What is this Compiz good for, when I can simply remove it without notyfying any negative effects?

It is responsible for those effects that you are unable to enable in any case.

---

### Post by abn91c on 2009-03-22
there is a bug in the ubuntu 8.10 with the i845 video cards, only workaround is to remove compiz, first do ```
sudo apt-get remove compiz[CODE]
```[/CODE] then the other code to remove compiz-core suggested earlier

---

### Post by astade on 2009-03-23
removing compiz seemed to work, yesterday afternoon. but this morning, again the same. System boots into a black screen.

After booting Windows, everything is OK :-(

So compiz alone is not the solution!

---

### Post by ugm6hr on 2009-03-23
Ensure you have updated with apt-get upgrade.

Then check whether RecoverY Mode works flawlessly.  If it does, it is obviously a problem with X / graphics.

If it boots into a black screen again, try Ctrl+Alt+F1 to see whether you can recover to Terminal.

---

### Post by abn91c on 2009-03-23
do not reinstall compiz or you will be back at the same screen. the desktop effects have to be turned off.

---

### Post by ready_to_rule on 2009-04-08
Just a a quick note... maybe side topic but... I have a Dell optiplex gx260, i845 chipset, boot failed from intrepid testing to final. Did the sudo apt-get remove compiz compiz-core thing and everything ok. Got tired of not having desktop effects and other new distro's not booting (mandriva pclinuxos suse dsl to name a few) 
So I found an old Geforce 4 agp 128 mb card and put it in the optiplex, and now [U]everything[U] boots.



]

---

### Post by Hamburgian on 2009-06-22
I've been struggling with this problem for a couple of weeks now and I've tried just about every 'fix' on the black screen subject apart from buying a new video card. But I've noticed a couple of things that may help more experienced Ubuntees sort the problem out.
I've got a DEll Optiplex gx620 with WinXp d/boot.
I get the black screen at a cold boot. But, if I leave the machine running, after about 5 minutes I can click on the keyboard and turn my IBM L170 on and off a few times and the screen will come on switching from the IBM default screen saver. I get the same problem if I leave the machine running but turn the screen off. When I come back I have to go through the same rigmarole - switching the screen on and off and clicking keys until the screen comes back - but everything is running OK in the background.
I'm running 8.04, but the same problems applies with 7.10 and 9.04.
My xorg.conf is the default from the fix option with recovery mode, but I've tried literally 100's of options and none of them seem to make any difference.

---

