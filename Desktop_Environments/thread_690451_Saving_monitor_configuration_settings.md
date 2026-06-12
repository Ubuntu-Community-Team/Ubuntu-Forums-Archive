---
title: "Saving monitor configuration settings"
date: 2008-02-07
forum: Desktop Environments
---

### Post by bookworm_2008 on 2008-02-07
I am getting very frustrated as Ubuntu isn't remembering the monitor settings I assign it to.

I have an HP w2408H (1900 x 1200 at 60 MHZ) and Samsung Syncmaster 1100DF connected to my system.

It constantly boots in low res graphics mode. I select Samsung from list of monitors and generic wide screen 1900 x 1200 for HP as the monitor isn't listed but OS isn't retaining my assigned monitors.

Is there a way to force these settings to boot configuration parameters so I can get on with my life and not to deal with this issue anymore?

---

### Post by talsemgeest on 2008-02-08
I had a similar problem to you. 
I have tried so many different ways to try to do what you said, with no success.
I ended up reinstalling and that fixed the problem...

---

### Post by bookworm_2008 on 2008-02-08
Thanks for the feedback I'll give it a try.

---

### Post by n-alexander on 2008-02-08
> **bookworm_2008 said:**
> I am getting very frustrated as Ubuntu isn't remembering the monitor settings I assign it to.

I have an HP w2408H (1900 x 1200 at 60 MHZ) and Samsung Syncmaster 1100DF connected to my system.

It constantly boots in low res graphics mode. I select Samsung from list of monitors and generic wide screen 1900 x 1200 for HP as the monitor isn't listed but OS isn't retaining my assigned monitors.

Is there a way to force these settings to boot configuration parameters so I can get on with my life and not to deal with this issue anymore?

under root, if you go to that application which controls monitor resolution and video card (setting/administration or something, I'm not sure, but is it only available for root), do you see your monitor and resolution or do you see something generic?

If what you see is something generic, then:

1) go to /etc/X11
2) is there a xorg.conf?
3) if NO, there must be xorg.conf.failsafe or something. Open it. In the header, it tells you which command line tool to use to create an initial xorg.conf. 
4) as root, go back to that application, set you video card and monitor, and check "make default for this computer only". Test, apply. Test sometimes works only on second attempt.
5) as root, go to Screen Resolution application (this is NOT the one that controls monitor and video card, this one is available for all users), select you resolution, check "make default for this computer only"

I could get all my users' setting right, except for the login window.

---

### Post by talsemgeest on 2008-02-08
Ive tried doing that before but it didnt work for me...

---

### Post by tcommbee on 2008-02-08
What graphics card and driver do you have? your system probably runs with vesa drivers, which don't support high resolutions. otherwise the monitor and screen sections in /etc/X11/xorg.conf should contain something like:

```
Section "Monitor"
	Identifier	"HP w2408H"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"the name of your device section"
	Monitor		"HP w2408H"
	DefaultDepth	24
	SubSection "Display"
		Depth	24
		Modes 	"1900x1200"
	EndSubSection
EndSection

```

---

### Post by bookworm_2008 on 2008-02-09
Thanks for all the feedback.

How do I get to to /etc/X11 ? I am a newbie as far as Linux is concerned.

I disconnected my second monitor and opted to choose HP only. I managed to get higher resolution by tricking OS to use another monitor but it only lets me go as high as 1280 x 1024 no matter what monitor I choose.

Previously it was defaulting to vesa driver but I managed it to accept Intel i965 configuration which defaults to Intel 810 graphics driver when selecting it. The system is based on Intel G35 Express (965 based) graphics chipset.

Another problem I have is the fact that I am able to start Linux under fail safe Gnome session only otherwise it goes into a login loop. Is there a way around to resolve this? Do I need to re-install the OS again? If so how do I manage it as by pressing the first option it does a live boot off the CD.

:confused:

---

### Post by talsemgeest on 2008-02-10
To edit the xorg.conf, simply type into the terminal: ```
gksudo gedit /etc/X11/xorg.conf
```
Hope this helps :)

---

### Post by aonegodman on 2008-02-13
I'm having the same issues each time I do a reboot my screen reso comes up to high and won't let me reset it 1280x768.

I've done all the xorg.conf file editing before and it don't help.

I'm running an Nvidia MX440 graphics card, Gnome desktop, compiz with 1 sceeen only.

I've tried to settings in both System > Administration > Screens and Graphics,

also

System > Preferences > Appearance and also Screen Resolution.

No Effect - won't change screen. Acts like it's lock in 1280 X 960.

Anybody?   Thanks    :(

---

### Post by iramhernandez on 2008-02-13
I have the same chipset and you are going to have to hand edit your xorg.conf file until the next version of the intel drivers are out.  Hopefully then, this chipset will be better supported.

I've had to learn the hard way how to hand edit the xorg.conf. Post your xorg.conf here and I''ll take a shot at it.  Also, run the following command from a terminal window and post the output:

```
xrandr --verbose
```

---

