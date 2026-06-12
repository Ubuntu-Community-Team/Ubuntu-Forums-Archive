---
title: "Monitor Resolution screws up"
date: 2005-11-17
forum: Desktop Environments
---

### Post by vishnumrao on 2005-11-17
I recently installed breezy on my amd64 machine. Monitor resolution was at a very low setting (1024*768 or 840 *680 , not sure). Googled it and found out a solution. This is the link:  [https://wiki.ubuntu.com/FixVideoResolutionHowto](https://wiki.ubuntu.com/FixVideoResolutionHowto)

Checked out the xorg.conf, I realize that my graphics card has been correctly recognized. So I set about to fix the resolution by changing the refresh rates.I have a Amptron 17" lcd which has a native resolution of 1280*1024. I changed the resolution as mentioned in the howto, to Hor = 30-85 and Ver = 30-85. saved xorg.conf and rebooted. Boot up started normally and then as its about to bring up the login screen, the monitor shuts down and says that the signals are out of range. 

My monitor documentation says Hor = 79.*** and Ver = 75.***(not sure about the figure, dont have the documentation with me). 

Now how do I go about setting the resolution to where it was. I have created the xorg.conf.backup. Is there a safe mode of booting into Ubuntu? Like not starting up xorg at all and only using text mode? 

Any help appreciated,
Thanks,
Vishnu Rao.

---

### Post by bonzodog on 2005-11-17
either:
A) run a live cd, mount the root partition, then go to /etc/X11/, and do 

$mv xorg.conf.backup xorg.conf

then reboot;

b) I'm not sure about this, but does the grub boot menu come up first?
if it does, boot to the recovery level. *I think** this takes you into consiole mode, where you just then do as above.

---

### Post by vishnumrao on 2005-11-17
Thanks bonzodog. I already fixed my monitor resolution back to the original resolution. Went into recovery mode at startup and changed the xorg.conf to the original values. 

Can you please help me fix my screen resolution to 1280*1024. I am stuck with 1024*768. 

Thanks in advance,
Vishnu Rao.

---

### Post by SavageBeginner on 2005-11-17
Please post your "/etc/X11/xorg.conf" file.

---

### Post by perceptor on 2005-11-18
I have a similar problem... i can't get 1600x1200 resoluction using 85hz, only 60hz. All the others works fine...

Video card? here is integrated 64mb

---

### Post by vishnumrao on 2005-11-19
[QUOTE=SavageBeginner]Please post your "/etc/X11/xorg.conf" file.[/QUOTE]


Hey SavageBeginner, 

Please find my xorg.conf as attachment. Appreciate your help. 

Thanks,
Vishnu Rao.

---

### Post by SavageBeginner on 2005-11-25
Sorry about the delay.  I forgot to check back on this thread.

I looked at your xorg.conf file.  First backup xorg.conf
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```

Then, edit xorg.conf as root:
```
sudo gedit /etc/X11/xorg.conf
```

Next, in the "Screen" section  you need to add "1280x1024" to all the modes.

Find this:  	
```
Modes		"1024x768" "800x600" "640x480"
```

Change to :
```
Modes		"1280x1024" "1024x768" "800x600" "640x480"
```

Also you may need to add a modeline to the monitor section

Find this:
```
Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection
```

Change to:
```
Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
	# 1280x1024 @ 60.00 Hz (GTF) hsync: 63.60 kHz; pclk: 108.88 MHz
  	Modeline 	"1280x1024_60.00"  108.88  1280 1360 1496 1712  1024 1025 1028 1060  -HSync +Vsync
EndSection
```

That will give you a refresh rate of 60 Hz.  If you need higher go to this site:  [http://www.sh.nu/nvidia/gtf.php](http://www.sh.nu/nvidia/gtf.php)[HTML][/HTML]

Here's the file you posted with the changes I mentioned.

---

### Post by frodon on 2005-11-25
Hey, if you don't put the good hsynv and vertsync parameters, modeline will do nothing (no refresh rate increase).

You just need to put in your xorg.conf the good hsync and vertsync parameters, so please give us the exact name of your screen, or the exact parameters written in your screen specification.
If this don't work we can look for advanced way to increase your resolution but generally it's not needed.

---

### Post by vishnumrao on 2005-11-25
I already fixed that problem. Was merely a problem of putting in the right numbers. Was my mistake. I put in some wrong numbers and things went awry. 

I plugged in the right numbers and things are nice now. Am enjoying Unbuntu. 

Thanks for your time and advice. 
Vishnu Rao.

---

### Post by frodon on 2005-11-25
Could you mark your thread title as solved ?

thanks.

---

