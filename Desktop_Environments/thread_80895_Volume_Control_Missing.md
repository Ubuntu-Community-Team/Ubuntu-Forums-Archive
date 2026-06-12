---
title: "Volume Control Missing"
date: 2005-10-23
forum: Desktop Environments
---

### Post by rianquinn on 2005-10-23
I am new to Ubuntu, but not new to linux (Being a previous Gentoo and Fedora user). I installed Unbuntu because I have heard amazing things, and so far I am more than impressed. However, (as usual with linux) I have a problem. My volumn control is missing from my GNOME panel.

1. I tried adding the item to the panel, when I select volumn control nothing happends.

2. If I go to the volumn control settings (Sound & Video -> Volumn Control), The volumn control APP knows I have a 

       CA0106 

module installed (Creative 24b), however all I get is Line In and Mic options.

3. If I want to changed the volumn I have to go into alsamixer, (meaning GUI don't seem to work).

I would like to be able to control my volumn via the gnome panels.



Finally I have one other question. How do you log into root. I can sudo commands all day, however I don't seem to be able to change, or even set my root password.

Here is my lspci
0000:00:00.0 Host bridge: Intel Corp. 925X Memory Controller Hub (rev 04)
0000:00:01.0 PCI bridge: Intel Corp. 925X PCI Express Root Port (rev 04)
0000:00:1d.0 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
0000:00:1d.1 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
0000:00:1d.2 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
0000:00:1d.3 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
0000:00:1d.7 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev d3)
0000:00:1f.0 ISA bridge: Intel Corp. 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
0000:00:1f.1 IDE interface: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
0000:00:1f.2 IDE interface: Intel Corp. 82801FR/FRW (ICH6R/ICH6RW) SATA Controller (rev 03)
0000:00:1f.3 SMBus: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
0000:01:00.0 VGA compatible controller: nVidia Corporation: Unknown device 0140 (rev a2)
0000:02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)
0000:02:02.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
0000:02:05.0 Network controller: RaLink Ralink RT2500 802.11 Cardbus Reference Card (rev 01)
[COLOR="Green"]0000:02:06.0 Multimedia audio controller: Creative Labs SB Audigy LS[/COLOR]



Thanks,
Rian

---

### Post by heart_reaver on 2005-10-23
Well for your root password ::

You have to set your root password. follow following for that


1. Open terminal
2. write **sudo passwd root**
3. Then enter your root password.

Rember that root is not allowed to login in as GDM user by default. For that do

System>>Adminstration>>Login Screen Setup>>Security

Check on check box : **Allow user to login as root**
:D 


For your sound problem try

Right click on panel >>Add to panel>> Volume control 


or u can drag n drop your volume control form 

**application menu>>sound.... >>**

---

### Post by taj on 2005-11-13
For your sound problem try
Right click on panel >>Add to panel>> Volume control
or u can drag n drop your volume control form
application menu>>sound.... >>


This is exactly what I did, but the volume control is the (only) button that refuses to appear in the panel.

---

### Post by emperor on 2005-11-13
[quote=rianquinn]
1. I tried adding the item to the panel, when I select volumn control nothing happends.

2. If I go to the volumn control settings (Sound & Video -> Volumn Control), The volumn control APP knows I have a 
       CA0106 module installed (Creative 24b), however all I get is Line In and Mic options.

Thanks,
Rian[/quote] 

1. The volume control should be added via the right click on the top panel method but does not get added to the panel from the existing menu entry as you have experienced. 

2, To expand the Controls in the Volume Control, select "Edit" then "Preferences", and then enable the desired "tracks to be visible".

---

### Post by mazg on 2005-12-02
I have the exact same problem with my volume control since I upgraded from hoary to breezy. When I upgraded, my volume control just dissappeared. I have tried doing the add to panel thing but nothing happens. I can add any other item I want except the volume control.
The interesting thing is that I have the exact same sound card as you.

---

### Post by dcstar on 2005-12-02
[QUOTE=rianquinn]I am new to Ubuntu, but not new to linux (Being a previous Gentoo and Fedora user). I installed Unbuntu because I have heard amazing things, and so far I am more than impressed. However, (as usual with linux) I have a problem. My volumn control is missing from my GNOME panel.
........
Thanks,
Rian[/QUOTE]
There is a known problem with some of the Themes in 5.10 where the Volume Control Panel icon becomes 1x1 pixels in size!

If you have changed from the default Theme, you may find reverting back to that theme will make you Volume Control icon(s) appear.

---

### Post by mazg on 2005-12-03
[QUOTE=dcstar]There is a known problem with some of the Themes in 5.10 where the Volume Control Panel icon becomes 1x1 pixels in size!

If you have changed from the default Theme, you may find reverting back to that theme will make you Volume Control icon(s) appear.[/QUOTE]

Thank you! This turned out to be the problem in my case. when I changed the theme, ten volume control icons popped up on my panel :D

---

