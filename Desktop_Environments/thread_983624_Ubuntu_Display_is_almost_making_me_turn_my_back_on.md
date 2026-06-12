---
title: "Ubuntu Display is almost making me turn my back on Linux and head back to Windows"
date: 2008-11-15
forum: Desktop Environments
---

### Post by Vorge on 2008-11-15
I keep having the same problem over and over again. Here's a link to another of my threads for info of whats going on: [http://ubuntuforums.org/showthread.php?p=6132935#post6132935]("http://ubuntuforums.org/showthread.php?p=6132935#post6132935")
At first I thought it was because of the programs I installed, but now if I re-install Ubuntu (which I've done like 7 times) and don't install any programs, once i shut off my computer the screen gets cut. If want pictures go to the link I gave. This is really making me mad. I tried changing the refresh rate and all that but it doesn't help. Any information would be greatly appreciated because Ubuntu is really getting on my nerves.](*,):cry:

---

### Post by inobe on 2008-11-15
okay i see that your monitor is out of sync when ubuntu gets loaded to your desktop !

first i have to ask you for hardware specs, make and model of your pc and monitor.

i have a few questions, have you enabled the video driver ?

---

### Post by Marcus Derekus on 2008-11-15
Did you try manually configuring /etc/X11/xorg.conf?

try opening xorg.conf and find the **Section "screen"**

Edit it like so:

```
Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth    24
	Subsection	"Display"
		Depth	24
		Modes	"1680x1050_60"
	EndSubSection
EndSection

```

Replace **"1680x1050_60"** with desired resolution

Then reboot

This usually works

---

### Post by inobe on 2008-11-15
> **Vorge said:**
> I keep having the same problem over and over again. Here's a link to another of my friends for info of whats going on: [http://ubuntuforums.org/showthread.php?p=6132935#post6132935]("http://ubuntuforums.org/showthread.php?p=6132935#post6132935")



i forgot to mention, opening new topics for the exact same issue is against the rules, please stay on one topic !

since this topic was opened' lets start fresh, please answer the questions.

what are your system specs, i need this information to determine what graphics card you are using ?

---

### Post by keithld on 2008-11-15
Vorge do you have another monitor you can try with your computer?...

I'd try that if you do and see if the same thing happens...

---

### Post by Vorge on 2008-11-16
> **keithld said:**
> Vorge do you have another monitor you can try with your computer?...

I'd try that if you do and see if the same thing happens...
Yeah I'm thinking of trying that with my Vista's monitor.

At others: I will bring up the hardware specs soon.

---

### Post by inobe on 2008-11-16
in most cases enabling a video driver and restarting x fixes display problems !

going to system/ administration/ hardware drivers/ enable video driver

now hit ctrl+alt+backspace will send you back to logon screen, put in user name and password, your desk should load up correctly.

---

### Post by spelingchampeon on 2008-11-16
Biostar K8M800 Micro AM2 with onboard video and lan
2gig Kingston memory
Samsung 216BW monitor
WD 400gig SATA hard drive
Optional Geforce TI4200 128M video card

I feel your pain. I have installed 7.10, 8.04 and 8.10 a total of 10 times over the last 2 weeks, and can never get my onboard video or Geforce TI4200 to work using the VESA drivers for my onboard video, or the restricted (Nvidia) drivers. I've tried EVERYTHING that I could find in this forum, or at the Nvidia site. Its just a bad situation.

Today, I was finally able to get 7.10 up and running at 1680x1050 @ 60hz by only allowing X to set up with 1680x1050 during the installation. After that, I ran the 7.10 update (242 files), made sure the default Ubuntu drivers were ok, THEN switched over to the restricted Nvidia drivers. It has been running ok, I was able to use Compiz AND was able to install VMWare (which 8.04 GCC did not like).

While I realize that Ubuntu is free, its the little things like getting 2 programs to run that is keeping Ubuntu from putting even more pressure on Windows and Apple. Most people wont have the 2 weeks (roughly 20 hours) to spend on anything like this. Another thing that keeps me scratching my head is the Kernel updates screwing up good programs, that otherwise have no major issues.

---

