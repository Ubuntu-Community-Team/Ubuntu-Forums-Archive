---
title: "No login screen with vesa"
date: 2009-04-16
forum: General Help
---

### Post by Sevy on 2009-04-16
Hi All
I have the following in 3 pc's

00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)

and in /etc/X11/xorg.conf have driver as "vesa" but when I log out,I cant login due to the screen being black.I can login without seeing it but the desktop is also black so have to reboot.
If I set xorg.conf driver as "intel" I get the login screen but the desktop takes a long while to load,particularly the sound and network icons
What else could I try?

---

### Post by Sevy on 2009-04-16
Bump;)

---

### Post by uncle-c on 2009-04-17
Dude,
I've got the same Intergrated Graphics  on the PC I am using and have had allsorts of problems with screen resolutions, black screens, no login managers etc etc. There are compatibility problems big time with this intel device, I read about them on a bugs list. Often I couldn't get into GDM or when I logged out of desktop to go to GDM I got a black screen. Even now when I login I often get messed up screen resolutions which are only fixed after I reboot. However, I have looked on the net and managed to partially solve the problem, mainly by editing the xorg.conf file and disabling GDM and hence starting my Gnome desktop using the startx command. Compiz / desktop effects are disabled by default for this graphics device, but you can enable them and by doing thus I have managed to get "the cube"  and other effects to work. Unfortunately, I don't think they intend to have fixes for the bugs relating to this intergrated card as from what I read it is too old.
Here is my xorg.conf :

```



Section "Device"
	Identifier	"Configured Video Device"
	Driver		"intel"
	Option "AccelMethod" "XAA"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	HorizSync	30 - 70
	VertRefresh	50 - 130
	Option 		"dpms"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
	SubSection	"Display"
		Viewport  0 0
		Depth 	24
		Modes  "1280x1024" "1024x786" "800x600" "640x480"
	EndSubSection

EndSection

```

The [COLOR="Red"]Option "AccelMethod" "XAA"[/COLOR] line is to aid in desktop effects and cube ( some other file alterations have to be made if it is to work) and obviously your monitor VertRefresh" and Horisync values will be different. My colours depth is 24 and screen res 1280x1024

---

### Post by Sevy on 2009-04-17
Thanks for that uncle-c
Luckily my screen resolutions work ok,Im just trying to get the login manager.
My previous pcs all had ATI graphics cards which also gave me problems,so thinking I would try these Compaq Evo's with onboard graphics,there would be an improvement,no such luck!
Ill google around,see what Ill find
Cheers

---

