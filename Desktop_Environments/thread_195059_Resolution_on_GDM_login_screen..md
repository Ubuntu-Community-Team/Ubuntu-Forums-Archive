---
title: "Resolution on GDM login screen."
date: 2006-06-12
forum: Desktop Environments
---

### Post by chajuram on 2006-06-12
Hi,

I changed my resolution to the one I like in Ubuntu. When I log out, the GDM screen has a much higher resolution and the entire page (for lack of a better word) is not displayed on the monitor. I can move my mouse around to see all parts of the screen. For example, the "options" on the bottom left is outside the monitor and so is the date and name of the computer on the right bottom. 

I was having the same problem when I first logged into ubuntu using the dapper CD (lower panel not showing). But the problem was fixed with the change in resolution. For this reason I was wondering if the problem is due to resolution. I am adding the output from lscpi below. 

Thanks in advance,
Chajuram.

0000:00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
0000:00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
0000:00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
0000:00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
0000:00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
0000:00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
0000:00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
0000:00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
0000:00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
0000:01:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (LOM) Ethernet Controller (rev 81)

---

### Post by Ctrl+Alt+Del on 2006-06-12
I assume you changed the resolution using the gui dialog in gnome, this changed the resolution inside gnome for your userprofile but not globally. To change your resolution for gdm you will have to make some changes to your xorg.conf
It can be found in /etc/X11/xorg.conf
> 
sudo -s
<enter password>
nano -w /etc/X11/xorg.conf
scroll down to the bottom and you will find several sections looking like the one below:
    Subsection "Display"
        Depth       24
        Modes       "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
    EndSubsection

edit them according to your needs by removing the resolutions higher than the one you desire, double check your settings and save the file.
upon restarting your gui you should have the desired resolution in gdm.
Bare in mind that a simple typo in your xorg.conf can break your xserver which will force you to repair it in console mode, which is not hard but may present you with a problem. So doublecheck your changes :)

---

### Post by chajuram on 2006-06-12
Thanks Ctr+Alt+Del,

Your suggestion worked great.

Chajuram. :)

---

### Post by Thought_Criminal on 2006-06-19
Ctrl+Alt+Del: I was having the same problem and your post got me through it.
Thanks for your help.

---

### Post by pelago on 2006-06-19
It'd be great to have a GUI option to change this resolution, either in the 'Login Screen' thing in System > Administration, and/or maybe in the login screen menu itself.

---

### Post by irv on 2006-06-19
I was getting ready to start a new thread, but maybe this is along the same lines as this one. Will this affect the usplash screen also by changing the xorg.conf file. Here is a selected copy of my xorg.conf file on the section of SubSection "Display". It appears mine is set to the highest resolution of my display. I don't believe I could change this?

> SubSection "Display"
		Depth		1
		Modes		"1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection

Thanks

---

### Post by Ctrl+Alt+Del on 2006-06-20
No, the usplash resolution (it is actually the framebuffers resolution) is changed in grub.conf
for details see: [http://www.ubuntuforums.org/showpost.php?p=541441&postcount=30](http://www.ubuntuforums.org/showpost.php?p=541441&postcount=30)
(the vga= part)

---

