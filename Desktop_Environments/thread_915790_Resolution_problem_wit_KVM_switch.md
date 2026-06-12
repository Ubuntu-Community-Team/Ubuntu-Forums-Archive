---
title: "Resolution problem wit KVM switch"
date: 2008-09-10
forum: Desktop Environments
---

### Post by rajeev1982 on 2008-09-10
Hi,

I have a KVM switch ATEN CS-62U. I have connected a 24 inch display to 2 of my machines having RHEL and Ubuntu using this KVM switch. I am not able to use the full resolution of my display with the KVM switch. My display gives me a resolution of 1900x1200 if I directly connect it to my Ubuntu laptop, but when I connect the same display using KVM switch to same ubuntu laptop, I get a resolution upto 1360x786. Can anybody help me with this. Is there anything wrong with this KVM switch?

Rajeev

---

### Post by johnnyhop on 2009-06-07
I had a similar problem when booting with monitor through my cheap KVM resolution was limited to 800x600.  I'm using a dated Radeon display adapter and upon removing radeontools which is suited for laptops but unnecessary on my tower, its now booting to normal screen resolution through the KVM.

---

### Post by mistofeles on 2009-06-17
Ubuntu **9.04 with Gnome**, **Intel D945GCLF2** mainboard with Atom 270, **SUN CM751U** monitor

I have four **KVM** switches and they all have the same problem.
- If I boot so that my Ubuntu box is active in **KVM**, the resolution is 1152x864_60 as I have set it in System + Display. It gives me a possibility to select 1360x768_60 too, but not higher. My old Sun monitor is able to use 1600x1200_85.
- if I boot so that Ubuntu is inactive in **KVM**, I got 800x600_60 and no possibilities to change it.

I have spent hours with xorg.conf and xrandr (and read manuals)
If i make make any changes to xorg.conf or make anything with xrandr, they are all wiped out, when I boot the PC and I get a lot of messages about wrong screen resolution.

- There got to be a file somewhere, where the default screen resolutions are listed. Where is it ?
- Is there any way to ge rid of this screen resolution automate which tries to be more clever than me ?
- is there any way to make System + Display show all the possible resolutions and refresh rates ?

I could make the configuration myself as I have made about 15 years in varios distros, if only there was not this automate.

---

### Post by johnnyhop on 2009-06-18
Good questions, I wish I had an answer to any one of them. I've considered it to be a stroke of luck when reviewing the installed files in Synaptic using radeon in a search and deleting the package intended for laptops but installed by default to my tower managed to fix the problem but as you pointed out when my tower was active through the KVM while booting, as it usually is. Someone must know how to disable the automated screen resolution, they just haven't stumbled over this thread yet.

---

### Post by tgalati4 on 2009-06-18
Cheap KVM's have limited resolution.  They are designed for monitoring servers.  I've never seen one above 1600x1200.

---

### Post by harmlessdrudge on 2010-03-24
I'm using an ATEN CS1734B KVM with Ubuntu and I've had this problem for a long time. The switch works perfectly with Windows and far beyond the resolution of my main monitor (1920 x 1200) -- it's rated up to 2048 x 1536.

However, it's not just an Ubuntu problem.

See [http://wombatdiet.net/2010/03/19/fedora-12-and-the-aten-cs1734b/](http://wombatdiet.net/2010/03/19/fedora-12-and-the-aten-cs1734b/)

---

### Post by dualbu on 2010-10-29
I've got an ATEN Master View CD-1764 switch.

No resolution problems with 8.04 Ubuntu on an old Dell, nor with 10.4 on an Acer Aspire X3200.

However, while 8.04 on the Dell works great with the switch, Ubuntu 10.4 and 10.10 both show a keyboard problem on the Acer. The switch gets less responsive to computer changes, and the keyboard input generates random repeatssssssssss.

The later problem renders Ubuntu unusable on the switchbox.

I'm waiting to see if ATEN has a solution (maybe the firmware update they have will fix it). But I'm not confident that the problem is that easy to solve.

I haven't seen any good news on this forum either. :(

---

### Post by hamiljf on 2011-11-26
The only workaround I've found is to connect the screen directly during boot.  And boot as seldom as possible.  Using Ubuntu 11.10, BTW.  If anyone has a better idea, I'd love to hear it.  BTW.... install startupmanager and set the boot resolution, otherwise you may never see anything at all.

---

