---
title: "extended desktop/multiple monitors"
date: 2010-10-01
forum: Desktop Environments
---

### Post by Vinger on 2010-10-01
Hello,

I use Kubuntu 10.04. 

I want to use multiple monitors in an extended way.
When i connect a monitor to my laptop, i get the same desktop view on both monitors.

When i go to system settings - display - multiple monitors, i see the message: "This module is only for configuring systems with a single desktop spread across multiple monitors. You do not appear to have this configuration".

What configuration do i need?

Allready thanks.

---

### Post by mrhhug on 2010-10-01
this has been well documented here: [http://ubuntuforums.org/showthread.php?t=221174](http://ubuntuforums.org/showthread.php?t=221174)

---

### Post by Vinger on 2010-10-01
ok, tx!

But xinerama is installed on my system, and shows me that message.
How can i see what videocard i have?

grz.

---

### Post by mrhhug on 2010-10-01
ya, thats ```
lspci
``` then jsut look for VGA compatible controller, there prolly an easy grep for this.... or you can check the model number for you system on whoever made it - if they have a website, i hope you patronized a local shop, usually if you call them they're more than happy to help you

---

### Post by Vinger on 2010-10-01
> koen@Koenh-Kubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile GME965/GLE960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GME965/GLE960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GME965/GLE960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03)
10:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
30:00.0 Ethernet controller: Marvell Technology Group Ltd. Device 4357 (rev 10)


Does this mean that i have an intel gpu?
What can i do for that one?

allready tx.
grz

---

### Post by mrhhug on 2010-10-01
yes you have a Intel Corporation Mobile GME965/GLE960 Integrated Graphics Controller, what are you trying to do exaclty? you have a laptop (right?) why would you want to carry arround an extra monitor?

---

### Post by mister_playboy on 2010-10-01
> **mrhhug said:**
> yes you have a Intel Corporation Mobile GME965/GLE960 Integrated Graphics Controller, what are you trying to do exaclty? you have a laptop (right?) why would you want to carry arround an extra monitor?

My laptop is my only computer and I hook it to my TV for home use... OP may be similar.

I also have a 965 chip and I have no problem with the multiple monitors... may I what connection you are using?  (VGA, HDMI, etc.)

---

### Post by Vinger on 2010-10-02
Hello,

I have multiple copies to do, while i want to inventory everything in sheets.
With en extra monitor, i can put every program next to each other, so i can move everything around very easily.

My connection is a VGA connection, i'm trying to use...
What have you done to make it work?

tx.

---

### Post by Vinger on 2010-10-08
No one an idea?

---

### Post by mrhhug on 2010-10-08
i was surprised to find that an intel mobile chipset does dual monitors AND has intel written instructions(for linux)! - usually only nvidia is that cool.

[http://edc.intel.com/Software/Downloads/IEGD/](http://edc.intel.com/Software/Downloads/IEGD/)

view the PDF on "dual Monitors" - linux instructions are on page 14 (or just search the pdf for linx)

basically it says to use Xinerama


- your Mobile GME965 is on the compatible hardware list!

go for it.

---

### Post by Vinger on 2010-10-08
tx for the reply...
The only problem is that i don't find a pdf on that site about dual monitors.

How did you reached it?

Allready thanks!
grz

---

### Post by mrhhug on 2010-10-08
i mainly linked to the PDF page so you could see that intel supported the multi displays, here is a direct link to the pdf - the intel page where the pdf is found lists your Mobile GME965 as hardware related to that PDF.

[http://download.intel.com/design/intarch/papers/323214.pdf](http://download.intel.com/design/intarch/papers/323214.pdf)

but it basically just tells you to install drivers (ubuntu ships with the driver)and run Xinerama.

so have you tried Xinerama?

see this post, the last relpy (on 23 July 2008 ) suggests that you the to reconfigure your xorg.conf

[http://wwww.ubuntuforums.org/showthread.php?p=5444902](http://wwww.ubuntuforums.org/showthread.php?p=5444902)

---

