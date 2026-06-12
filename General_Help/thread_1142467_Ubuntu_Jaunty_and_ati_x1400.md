---
title: "Ubuntu Jaunty and ati x1400"
date: 2009-04-29
forum: General Help
---

### Post by hacktom on 2009-04-29
Has anyone installed ubuntu jaunty on laptop/Desktop with ati x1400??? Since I came to know that ati proprietary drivers doesn't work for this card how is the 3d performance in jaunty with open drivers?

---

### Post by skymera on 2009-04-29
My friend has the X1250 running on the open source drivers.

Compiz works fine, perhaps a little jumpy at time.

Though Compiz is jumpy for me even with the proprietary drivers =X

---

### Post by mihai.ile on 2009-04-29
generally work ok, quite stable, seems that have improved a little from the last release, but if you use Blender for example you may some problems...

---

### Post by hacktom on 2009-04-30
Thanks for the replies since I also involved with open gl programming I want how is open gl performance with open source drivers before I update ubuntu.

---

### Post by hacktom on 2009-04-30
how is google earth performance anyone please??

---

### Post by jaxpiron on 2009-05-04
google earth crashes on jaunty with open source drivers. 
at least on my machine (t2500, 2gb, ati x1400).

though it works fine on intrepid with the restricted drivers.

---

### Post by Alterax on 2009-05-04
Can't tell you specifically about Jaunty's performance with the open-source drivers, as I'm running Debian.  However, the version of the open-source driver should be fairly close between the two.

I do just fine with it.  My main machine for daily use is an iBook G4 that runs with an ATI radeon chipset.  (Same driver as the x1400).  The fglrx driver isn't an option for me, as they only do binary releases for the x86--and here I am on a powerPC.

One thing I did note is that left to its own devices, with X.org autoconfiguring everything, performance was very poor.  I ended up setting up my xorg.conf file manually to take better advantage of the chipset's functions.

Here's a slightly modified version of my xorg.conf file.  I've removed the parts that limit me to 1024x768:16 resolution (best resolution for my particular monitor, dropping from 24-bit to 16-bit graphics bumped up the performance a lot--and I can't tell the difference).

hmmm... forums keeps calling it an invalid file.  But if you'd like it, drop me a private message and I'll arrange for an http download or something.

---

### Post by oyvinst on 2009-05-04
Works OK, though there are some small problems (for me, at least):
* Issues with 2D graphics corruption.
* Not the same 3D performance or level of OpenGL compatibility as with fglrx-driver on Intrepid.

Talking about an ATI X1400 radeon mobile (ChipID = 0x7145) on a Lenovo Thinkpad Z61m laptop running Ubuntu Jaunty and open source radeon driver.

---

### Post by nandotron on 2009-05-17
Hi,

I'm having some problems with the x1400 graphics card and the open drivers.  My laptop display is capable of 1920x1200 resolution but I'm limited to 1680x1050 as per display preferences.  

I had it running at 1920x1200 just after the upgrade to jaunty but in the meantime i've messed with connecting the laptop to a hdtv via the dvi and vga outs and have installed and removed the fglrx driver after finding out it wouldn't work for me.  

is there a way to get the higher resolutions back?

thanks for your help!

---

### Post by nandotron on 2009-05-19
> Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
		Virtual	3040 1050
	EndSubSection
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Hi,

I checked out my /etc/X11/xorg.conf file and this was what I got.  Pretty sure this is not what it should look like.  Is there any way to reset it?  (reinstall the driver?)

thanks

---

### Post by VeN0mizer on 2009-05-21
Not sure if this helps but I have an x1300 and also experience the crash...before I added the dontzap feature, X would just hang the system, but with it I get the black screen then the lovely login prompt...I tried compiling and installing the latest GL libraries and that helped google earth and other causes of system hangs :) BUT! I no longer have direct rendering :( SO I reinstalled the repo ones with synaptic and I got direct rendering again, but no google earth for very long :( And did I mention compiz stopped working now too even though I have direct rendering again?....stupid ATI...should have made the linux drivers open source to begin with rather than GIVING UP...yes that's right folks GIVING UP on cards just a few years old because you have no idea what you're doing and every driver is a "cross your fingers and hope for the best" patchwork, rather than spending money to hire software engineers familiar with linux....*DOH!*


Edit: Even though I'm not happy with the performance, my next laptop will have an Nvidia card for the sake of linux...I can assure you of that! I'm ready to dump ATI like I did Microsoft :P QUIT screwing around and focus on what you're doing rather than having $$ signs floating around in your head!!

Ok...I'm off my soap box now...

---

### Post by Skywalker hack on 2009-05-21
mmm...I have ATI and it worked and works perfect! But u need install the exact driver :)

---

### Post by afbase on 2009-05-22
> **Skywalker hack said:**
> mmm...I have ATI and it worked and works perfect! But u need install the exact driver :)
What driver did you use? If its not the same question, where can I find the open source drivers for the Radeon x1400 for Jaunty Jackolope (9.04)?

---

### Post by chaosrl on 2009-06-24
So, has anyone really gotten anywhere with this? I tried to play Yo! Frankie (or whatever it's called) a few weeks ago, and found that it ran like a pig, even though my computer really should be able to handle it.

---

### Post by sdowney717 on 2009-06-24
I am using jaunty with an x1300 and I cant do compiz or any 3d effects.
It just does not work. The people it does work for must be special.

---

### Post by sdowney717 on 2009-06-24
> What driver did you use? If its not the same question, where can I find the open source drivers for the Radeon x1400 for Jaunty Jackolope (9.04)?

you are already using the open source drivers. If you have an x series or older ATI card. So that is that.

---

