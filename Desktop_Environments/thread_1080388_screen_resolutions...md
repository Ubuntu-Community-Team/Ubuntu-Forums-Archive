---
title: "screen resolutions.."
date: 2009-02-25
forum: Desktop Environments
---

### Post by .Kai on 2009-02-25
Okay I unintalled Ubuntu from my computer completely installed it again using the ubuntu disk I have. the screen is kinda big. it was never this big before, I even tried using the update manager to install all the updates that's needed for Ubuntu and the screen resolution manager thingy doesn't even have settings for smaller screen sizes [only bigger ones] I tried reading stuff online but no luck..


Thank you to whoever helps me on this one. [I'm using Ubuntu 8.10 (duh)]

---

### Post by .Kai on 2009-02-25
Bump, help please?'

thanks.

---

### Post by svanheulen on 2009-02-25
Needs moar info. What video card do you have? What driver are you using? What resolutions are listed? By "bigger" do you mean higher resolution or things look larger on the screen?

---

### Post by .Kai on 2009-02-25
I don't know my video card or driver...
and also I'm the ones listed.
800 x 600 (4:3)
640 x 480 (4:3)
400 x 300 (4:3)
320 x 240 (4:3)
the screen isn't TOO big. it doesn't fit "in" if you know what I mean. 
here's a screenshot.
(not sure if it'll be much of a help though.)
[http://i40.tinypic.com/2zoaqeo.png](http://i40.tinypic.com/2zoaqeo.png)

---

### Post by svanheulen on 2009-02-25
Open a terminal, run 'lspci' and post results.

---

### Post by .Kai on 2009-02-26
This is what I get
00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 04)
00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 05)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 05)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 Controller (rev 05)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 05)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 05)
00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio Controller (rev 05)
01:00.0 VGA compatible controller: ATI Technologies Inc Rage 128 Pro Ultra TF
02:04.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)
02:08.0 Ethernet controller: Intel Corporation 82801BA/BAM/CA/CAM Ethernet Controller (rev 03)
02:09.0 Communication controller: Conexant Systems, Inc. HSF 56k HSFi Modem (rev 01)

---

### Post by svanheulen on 2009-02-26
I did some searches and this is the best info I can find:
[http://www.linuxforums.org/forum/ubuntu-help/141385-problems-ati-rage-128-pro-ultra-tf.html](http://www.linuxforums.org/forum/ubuntu-help/141385-problems-ati-rage-128-pro-ultra-tf.html)

Hopefully that helps or at least gives some more clues.

---

### Post by skotos on 2009-02-26
Nowadays, just 2 types of graphics display cards should be available... Thus, it should be easy to solve this by *going proprietary* and running **Envy** that is now part of the standard repositories.

Envy might help you going with Nvidia and ATI cards. Try it and it might solve the problem without even working at the command line at all.
I would obviously start by trying the ATI driver, since an ATI display card is reported by your *lspci* output!

And, if everything goes as expected.... well, I would immediately switch to install the *Simple CompizConfig Settings Manager* to enjoy the cube, the multiple displays configurations, the output to the TV and the rest!!!

HTH :popcorn:

---

### Post by svanheulen on 2009-02-26
The proprietary ATI driver is for the Radeon series cards. The lspci listing says it's a "ATI Technologies Inc Rage 128 Pro Ultra TF" which is not in the Radeon series.

---

### Post by .Kai on 2009-02-27
May I know how to install "Envy"?
@svanheulen So it wouldn't work right..?

---

### Post by .Kai on 2009-02-27
Bump! anymore help?

---

### Post by shankru85 on 2009-02-27
Did you try out System->Adminstration->Hardware Drivers and System->Adminstration->Hardware testing etc ? 

Honestly i dont have an NVIDIA or ATI card whatever. And havent tested this thing functionality. Just thought i could throw in my 2 cents.

---

### Post by shankru85 on 2009-02-27
Btw, on how to install envy..

sudo apt-get install envyng-qt (or)

sudo apt-get install envyng-core

---

### Post by beekr on 2009-02-27
Open a terminal and took a look at your xorg.conf file.

Back it up with:
```

cp /etc/X11/xorg.conf /etc/X11/xorg.bak

```

Then I edited the file with:

```

sudo vi edit /etc/X11/xorg.conf

```

Once that was opened, step down till you find the line that says "Configured Video Device". This is what you might find:

Section "Device"
Identifier "Configured Video Device"
EndSection

Edit the file and right under "Identifier" try adding a line that says Driver "ati" So when you are done, it should looked like this:

Section "Device"
Identifier "Configured Video Device"
Driver "ati"
EndSection

<Esc>:wq

Then exit the terminal and reboot system. When it comes back up, Click on Applications >> other >> screens and graphics. From there, you should be able to select a monitor type. It will ask you to log out and back in. Then, you will be able to go to System >> Preferences >> Screen Resolution and select higher resolutions than 800x600. 

Beekr

---

### Post by hictio on 2009-02-27
.Kai,

What is this box of yours?
A laptop or a desktop?
Do you have the tech specs of your monitor? Be that a laptop LCD or a regular monitor?
You'll need the exact values for the 'Horizsync' & the 'Vertrefresh', once you have those (the ones for your monitor!), you'll have to edit the file '/etc/X11/xorg.conf', adding those values.

Check this thread: [help please with resolution ibex](http://ubuntuforums.org/showthread.php?t=975452&page=2)

---

### Post by .Kai on 2009-02-28
@shankru85 It didn't do anything. 
@beekr I tried it. but there's no Applications >> other >> screens and graphics [: and it only shows two screen resoutions
@hictio 
It's a desktop and I don't get where to add the info of my drives.

---

### Post by hictio on 2009-02-28
> **.Kai said:**
> 
@beekr I tried it. but there's no Applications >> other >> screens and graphics [: and it only shows two screen resoutions


beekr, probably meant System > Preferences > Screen Resolution
If you go there, and don't see any other resolution listed it's b/c the system, or X Window, doesn't recognize your card (or monitor) automatically, and therefore switches to a safe default, so it doesn't blow your monitor while trying to run at a higher resolution.


> **.Kai said:**
> 
@hictio 
It's a desktop and I don't get where to add the info of my drives.


You don't need the info on your drives for this (?????)
You need the tech specs of your monitor, the vertical & horizontal refresh rates, Google those with the exact model of your monitor.
Then, edit the '/etc/X11/xorg.conf' file, adding those values, take a look at the post I linked above.
It is as "easy" as that, the correct values, plus the desired (and supported, of course!!!!) resolution value added to the configuration file, a re-init of the graphic environment (Ctrl + Alt + Basckspace) and presto.

If your card also supports it, you can enable Desktop Effects too, but first focus on getting out of that restrictive screen resolution :D

---

### Post by beekr on 2009-02-28
No actually I didn't mean System > Preferences > Screen Resolution. If Applications > Other > Screens and Graphics is not there, you can add it. Add it by right clicking on applications and select menu edit. Wait for main menu screen to open. From Main menu, left column [MENUs] select "Other" and a new list of text will appear in the right screen [items]. Place a check mark in the box to the left of screens and graphics, this will automatically select "other" if it was NOT in your drop down list under Applications. Close this window and reboot.

---

### Post by .Kai on 2009-07-01
Hey guys, I know this is like a really old thread.
but sometimes the screen size is just how i want it and when i unintall/reinstall it'll be big any idra how to fix it? i tried what you guys had on here but none of it seems to work.

---

### Post by .Kai on 2009-07-02
can anyone help me here? D;

---

### Post by Jarkycat on 2009-07-02
Can you paste in the contents of your xorg.conf for us?

In a terminal, type in:

cat /etc/X11/xorg.conf



Do you know what resolution you used to run at?   What kind of monitor do you have?

---

### Post by .Kai on 2009-07-03
Here, this is what I got.
```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
```
and I'm not really sure what kind of monitor(I assume it's ATI Technologies Inc Rage 128 Pro Ultra TF ) I have and the resolution I Had before I think the one I have on XP is 1280x800

---

### Post by Jarkycat on 2009-07-03
Ok, so it has a r128 chipset.  This is different than the standard ATI driver suggested earlier.

Let's try specify it as the driver and see if this allows you to use the other resolutions.

Here's what we need to do:

1) Backup your xorg.conf. At the terminal, type in:
[B]
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-backup[/B]


2) Make a few changes to the current xorg.conf. At the terminal, type in:

**gksudo gedit /etc/X11/xorg.conf**

This will open up a text editor than you can use with your mouse, etc.  Here we'll insert our changes (listed in bold) in 2 sections.  You can copy and paste the entire area below over if you like.

Section "Device"
	Identifier	"Configured Video Device"
	**Driver		"r128"**
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
                [B]Subsection "Display"
	              Depth 24
	              Modes "1280x800" "1024x768" "800x600" "640x480"
                EndSubsection[/B]
EndSection

3) Save the file and exit.

4) Reboot the system

5) When you're back in the system, see if you can change the resolution again.


Let me know if it works.

---

### Post by pytheas22 on 2009-07-03
Kai: you mean when you reinstall Ubuntu, the screen defaults to a low resolution?  That probably would happen because you need to install drivers for the graphics card after installing Ubuntu, and reboot for the drivers to be activated.  What kind of video card do you have?

---

### Post by .Kai on 2009-07-03
@Jarkycat I tried doing it like you did, but it didn't seem to load in the right screen resolutions.
@pytheas22 Hey, all I know it's a ATI Technologies Inc Rage 128 Pro Ultra TF like i said in PM. and the name it's a cybervision c70(an old monitor. :/)

---

### Post by Jarkycat on 2009-07-03
Ok, let's have it reconfigure itself again.  Maybe it'll find the r128 driver this time.

In the terminal, type in:

**sudo dpkg-reconfigure -phigh xserver-xorg**


When you get back from the reboot, try to change your resolution again and see if its different.



If still unsuccessful, list your newly updated xorg.conf once again for us.

cat /etc/X11/xorg.conf

---

### Post by .Kai on 2009-07-04
I typed in sudo dpkg-reconfigure -phigh xserver-xorg and got the ```
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.2009070407551
``` message and I restarted and it didn't work.

here's the updated xorg.conf (seems to be blank again.) >_<
```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
```

---

### Post by Jarkycat on 2009-07-04
Ok, the auto-reconfigure attempt reset everything.

We'll try to force the r128 driver again but with a few adjustments.   Hopefully these will be enough to get the driver and higher resolutions working.

First, I looked up your specific monitor display frequencies found here: [http://www.monitorworld.com/Monitors/cybervision/c70.html](http://www.monitorworld.com/Monitors/cybervision/c70.html)

According to it, I'm not sure if you can reach 1280x800 resolution with it.  So we'll try for the goal of 1024x768 which is still decent for 17" monitor.  Will be better than 800x600 you're running at now.

Ok here we go:

1) Make sure the r128 driver is loaded into the kernel.  Type in the terminal:

**sudo modprobe r128**


2) Make a few more changes to the current xorg.conf. At the terminal, type in:

**gksudo gedit /etc/X11/xorg.conf**

This will open up a text editor than you can use with your mouse, etc. Here we'll insert our changes (listed in bold) in 2 sections. You can copy and paste the entire area below over if you like.


Section "Device"
Identifier "Configured Video Device"
[B]Driver "r128"
VendorName     "ATI"
BusID          "PCI:1:0:0"[/B]
EndSection

Section "Monitor"
Identifier "Configured Monitor"
[B]HorizSync       30-70
VertRefresh     50-75[/B]
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
[B]Subsection "Display"
Depth 24
Modes "1024x768" "800x600" "640x480"
EndSubsection[/B]
EndSection

3) Save the file and exit.

4) Reboot the system

5) When you're back in the system, see if you can change the resolution again.  Change it in the control panel, etc.


Hope these additional changes will do the trick.

---

### Post by .Kai on 2009-07-04
That seemed to work. :D thank you so much. I would hug you if I could. XD

---

### Post by AjShare on 2009-08-05
Thankyou Jarkycat.....You solved it like a charm.
I have a "notorious" sis 760 chipset(display adapter) in my ASUS K8S-MX motherboard. I was not able to get my favourite resolution "1024x768"..
I just replaced my Xorg.conf with your solution minus the two lines below.
[B]Driver "r128"
VendorName     "ATI"[/B]
Hope this helps those who struggle with their resolution.
Thankyou once again.....

---

### Post by ssaes on 2009-10-09
Just want to thank everyone for this information which was extremely useful in helping me resolve issues with screen resolution on my Ubuntu Desktop PC.

Thanks!!!!

---

