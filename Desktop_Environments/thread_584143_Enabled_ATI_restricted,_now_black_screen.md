---
title: "Enabled ATI restricted, now black screen"
date: 2007-10-20
forum: Desktop Environments
---

### Post by Radamand on 2007-10-20
I just finished installing Gutsy as a dual boot on my Winders box, patched software, and enabled restricted drivers for my ATI Radeon HD2900XT.
Reboot to a black screen, no login GUI, no sound, nothing.
Reboot to recovery mode gets me what I assume is the linux equivalent of single user mode.

now what?

Please dont ask me to post my xorg.conf file as I cant, have to boot into windows just to get to the forums....

---

### Post by thomasbaker on 2007-10-20
the same thing with me, i have a ati x1950 viper gt video card.  Every thing worked fine with feisty.

using live cd now. someone please help

thanks

---

### Post by ztheory on 2007-10-20
hold ALT and hit F2 (or F3)

worked on mine

---

### Post by Radamand on 2007-10-20
Alt-F2 does nothing, apparently it is a complete lockup.

---

### Post by ihcnet on 2007-10-21
Check out the Gusty release notes, it says something about ATi restricted drivers and a blank screen bug in the final release.

---

### Post by dcotruta on 2007-10-22
I'm also experiencing this problem with my X1600 Pro. Feisty worked fine - how can you go backwards like this?

---

### Post by blueturtl on 2007-10-22
Guys, the Ubuntu team cannot fix the ATI driver because it is restricted (that's what it means). It's up to ATI.

If your system boots to a blank screen you can try logging in through a text terminal:

Hit Ctrl+Alt+F2 (the last key can be between F1 and F5)
You should get a login-prompt in text mode, log in using your username and password.

Now, type in the following command (we'll backup your current configuration):
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.mybackup

You will be prompted for your password again.

Next, enter the following command:
sudo nano /etc/X11/xorg.conf

A configuration file should appear, you can scroll up and down using the arrow keys.
Find where it says something like this:

```
Section "Device"
        Identifier      "Ati Technologies [Radeon model etc]"
        Driver          "fglrx"
        Busid           "PCI:1:0:0"
EndSection
```

Change where it says 'fglrx' to 'ati'.
Hit Ctrl+X to exit, hit Y to accept changes and finally hit Enter to finish.
Reboot and you should be back in graphical mode with the open-source ATI driver.

edit. In case you don't know how to reboot in text mode, you have to give the command 'sudo reboot' ;)

---

### Post by Kymus on 2007-10-22
I'll try that out, thanks blueturtl :D

---

### Post by arno77 on 2007-10-22
Thanks for the hint. I tried it but nothing happens (i.e no login-prompt in text mode) when hitting Ctrl+Alt+F2 (I also tried all keys from F1 to F5). 
Has anybody an idea how to get into text mode alternatively?
I am really lost because feisty that worked fine also now boots into a black screen.  

> **blueturtl said:**
> Guys, the Ubuntu team cannot fix the ATI driver because it is restricted (that's what it means). It's up to ATI.

If your system boots to a blank screen you can try logging in through a text terminal:

Hit Ctrl+Alt+F2 (the last key can be between F1 and F5)
You should get a login-prompt in text mode, log in using your username and password.

Now, type in the following command (we'll backup your current configuration):
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.mybackup

You will be prompted for your password again.

Next, enter the following command:
sudo nano /etc/X11/xorg.conf

A configuration file should appear, you can scroll up and down using the arrow keys.
Find where it says something like this:

```
Section "Device"
        Identifier      "Ati Technologies [Radeon model etc]"
        Driver          "fglrx"
        Busid           "PCI:1:0:0"
EndSection
```

Change where it says 'fglrx' to 'ati'.
Hit Ctrl+X to exit, hit Y to accept changes and finally hit Enter to finish.
Reboot and you should be back in graphical mode with the open-source ATI driver.

edit. In case you don't know how to reboot in text mode, you have to give the command 'sudo reboot' ;)

---

### Post by blueturtl on 2007-10-22
> Thanks for the hint. I tried it but nothing happens (i.e no login-prompt in text mode) when hitting Ctrl+Alt+F2 (I also tried all keys from F1 to F5).
Has anybody an idea how to get into text mode alternatively?

If you cannot get into the text terminal, then the system is probably locked up (truly locked up). You can try booting the safe mode option when the system starts.
If you have both Windows and Ubuntu the menu should be displayed automatically, if you only have Ubuntu, you have to hit esc right before the OS starts loading to see the menu.

From the menu select the safe mode option. This should give you a text mode view with all administrative rights. Note that when you're logged in as root you can leave the 'sudo' prefix off all the commands I listed in my previous post.

---

### Post by arno77 on 2007-10-22
> **blueturtl said:**
> If you cannot get into the text terminal, then the system is probably locked up (truly locked up). You can try booting the safe mode option when the system starts.
If you have both Windows and Ubuntu the menu should be displayed automatically, if you only have Ubuntu, you have to hit esc right before the OS starts loading to see the menu.

From the menu select the safe mode option. This should give you a text mode view with all administrative rights. Note that when you're logged in as root you can leave the 'sudo' prefix off all the commands I listed in my previous post.

Hi blueturtle,
I entered in recovery mode and it worked indeed. Thanks a lot!
But now I have a really bad (=low) resolution. Would be great to receive a hint how to resolve this, too.

---

### Post by blueturtl on 2007-10-22
> Hi blueturtle,
I entered in recovery mode and it worked indeed. Thanks a lot!
But now I have a really bad (=low) resolution. Would be great to receive a hint how to resolve this, too.

Have you tried to do this under  System->Administration->Screens and Graphics ?

---

### Post by arno77 on 2007-10-22
> **blueturtl said:**
> Have you tried to do this under  System->Administration->Screens and Graphics ?

Yes, but the maximal resolution I get is 800x600 73Hz. Don't receiver higher resolution options. 
The optimal one is - it says - 1280x1024 60Hz.

I have a Dell Flat Panel SE 197FP (which is correctly detected)
and a
256MB ATI X1300 Pro Half Height Graphics Card

I very much appreciate your help.

---

### Post by leona on 2007-10-22
Get same problem with Nvidia cards too, basicly if you enable the restricted drivers you either get a corrupted or blank screen, happened on both my sony vaio and desktop machines, so I guess no 3d for me :(  
(fixed by doing sudo dpkg-reconfigure xserver-xorg and going though the options, but now stuck on 2D)

---

### Post by Kymus on 2007-10-22
It worked great.

First reboot, I couldn't change the resolution, it just stuck, so I rebooted again and now everything seems fine.

thanks again!

---

### Post by blueturtl on 2007-10-22
> Yes, but the maximal resolution I get is 800x600 73Hz. Don't receiver higher resolution options.
The optimal one is - it says - 1280x1024 60Hz.

I have a Dell Flat Panel SE 197FP (which is correctly detected)

I realize I'm used to doing things "the old school way" but if you don't find it too daunting we could take another look at the xorg.conf file.

Now that you are running in a graphical mode you no longer need to do this in a terminal, but I find this is the easiest way to talk you through it so bear with me. ;)

Ok, firstly open a virtual terminal through Applications->Accessories->Terminal.

Then type in the following command: gksudo gedit /etc/X11/xorg.conf

Find where it says something like this:

```
Section "Monitor"
        Identifier      "M1700"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "nVidia Corporation NV28 [GeForce4 Ti 4200 AGP 8x]"
        Monitor         "M1700"
        Defaultdepth    24
        SubSection "Display"
                Depth   1
                Modes           "1280x1024"     "1024x768"      "800x600"      $
        EndSubSection

...
```

The following is from my xorg.conf, but essentially it is the same as yours. Just the monitor and the video card names are different. The lowest bit as you can see lists resolutions. If you find the two higher resolutions are not listed, you may add them manually. There are multiple entries (don't let this confuse you, they're for different color depths). Just modify all the lines that start with 'Modes' to include the resolutions like "1280x1024" and "1024x768". After you've edited the lines, save the file and reboot your system (or alternatively just log out and then hit Ctrl+Alt+Backspace to restart the graphics subsystem).

Hope this helps.

---

### Post by flamarro on 2007-10-22
Hi guys,
I also have this problem too, again....
I have a ATI X1300 also and every time i install restricted drivers, in the boot end, i came to a black screen where i cant do anything.
I used to resolv the problem like i said in [this]("http://ubuntuforums.org/showthread.php?t=514463") thread, but, when i install from scrach, jesus, i start a damn fight whith my ATI. I dont know what the hell envy do, but, when i install like he says, in the end, i dont have that black screen, and then i can uninstall it, play around with restricted drivers, that that black screen dosent come again.....
i have now 64 bit edition installed, i tryed from [here]("http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide"), (yes, feity at the time), and didn't make also, but uninstalled fglrx, stayed installed xorg-fglrx, and when i restarted, all seems good. Now i did a fresh install of gutsy, and got the damn black screen again...
I will try the gutsy way now.... and other ways also, trying every thing i can..... In the end i now i will make it, but when i do i think i dont now how i got there....
Not much of a help isn't it..... :(

PS: Like i said, did the Envy way, and the result
```
fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1300 / X1550 Series
OpenGL version string: 2.0.6747 (8.40.4)

```

Case closed......... for now :)

---

### Post by arno77 on 2007-10-22
> **blueturtl said:**
>  Just modify all the lines that start with 'Modes' to include the resolutions like "1280x1024" and "1024x768". After you've edited the lines, save the file and reboot your system (or alternatively just log out and then hit Ctrl+Alt+Backspace to restart the graphics subsystem).

Hope this helps.

Hi, thanks for your patience.
I did as you suggested. The device/screen/monitor part of the xorg.conf looks now like this:

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"ati"
	Busid		"PCI:3:0:0"
EndSection

Section "Monitor"
	Identifier	"DELL SE197FP"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"DELL SE197FP"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1280x1024"	"1272x1272"	"1024x768"	"880x704"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1280x1024"	"1272x1272"	"1024x768"	"880x704"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1280x1024"	"1272x1272"	"1024x768"	"880x704"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1280x1024"	"1272x1272"	"1024x768"	"880x704"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1280x1024"	"1272x1272"	"1024x768"	"880x704"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1280x1024"	"1272x1272"	"1024x768"	"880x704"	"800x600"	"720x400"	"640x480"
	EndSubSection
EndSection

I only added "1280x1024", the rest was there. Logged off and hit Ctrl-Alt-Backspace .. but no effect. I still have the low resolution. :(

---

### Post by blueturtl on 2007-10-23
Have you re-checked the System->Administration->Screens and Graphics ?

What about System->Preferences->Resolution ?

Just to make sure, since those can remember your previous settings. By default X should use the highest resolution and color depth your system can support.

We're starting to run at the limits of my knowledge but don't worry, I still have a few things up my sleeve... ;)

---

### Post by blueturtl on 2007-10-23
> Hi guys,
I also have this problem too, again....

...Case closed......... for now :D

Did you fix your problem?

You should have a much better time after the new open-source ATI drivers come out. AMD (which owns ATI) has recently released spesifications for all their hardware (a very good thing) so we're soon going to have better drivers than the ones ATI offers. Unfortunately that's not just yet so we still have to fiddle a bit. Maybe in Gutsy +1 or +2 ATI isn't going to be as much of a problem anymore.

---

### Post by SKiFF on 2007-10-23
> **thomasbaker said:**
> the same thing with me, i have a ati x1950 viper gt video card.  Every thing worked fine with feisty.

using live cd now. someone please help

thanks

yeah I have ATI x1950, same thing happens.

---

### Post by Saint Angeles on 2007-10-23
I'm just a linux noob so bear with me. My Radeon X1550 is doing the same thing... black screen. I installed from the kubuntu 7.10 disc and it happened. I reinstalled feisty and did a dist upgrade and it did the same thing.

So I put in a dapper 64-bit disc and did all the upgrades to gutsy. when i try to use the new 2.6.22... kernel, the black screen shows up. I managed to get x going when i use the older kernel however.

bah... ive been doing everything on the forums and Ive prolly put about 35 hours into fixing this. help!

---

### Post by arno77 on 2007-10-23
> **blueturtl said:**
> Have you re-checked the System->Administration->Screens and Graphics 

What about System->Preferences->Resolution ?


Back again! I checked all you mentioned.

I attach some screen-shots of "Resolution" and "Screens and Graphics"; maybe they contain some useful info. The resolutions I can choose from in "Screen and Graphics" are 640x480, 720x400, 800x600. In "Resolution" it is even only 800x600, 640x480.

Some more info that may be useful. At start-up I receive messages I have not received before the update to gutsy. Among other things it says "kinit: no resume image ... doing normal boot" and "* booting hardware drivers / error receiving uevent message: No buffer space available"

I also receive a screen telling: "Ubuntu is running in low-graphics mode" and it gives the options to <Configure> (which doesn't work), <Shut down>, or <Continue>.

---

### Post by flamarro on 2007-10-23
> **blueturtl said:**
> Did you fix your problem?

You should have a much better time after the new open-source ATI drivers come out. AMD (which owns ATI) has recently released spesifications for all their hardware (a very good thing) so we're soon going to have better drivers than the ones ATI offers. Unfortunately that's not just yet so we still have to fiddle a bit. Maybe in Gutsy +1 or +2 ATI isn't going to be as much of a problem anymore.

Yes, for now i fixed my problem, i've got the 3D working.
I really dont know is why doing method 1 or method 2 following [this]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide") guide, in the end i always have that black screen, and, when i use Envy way, i get a fully desktop working, and, now in Gutsy, it even has fglrx probed from the beggining. I say this because, earlier i had to copy fglrx.ko to some that volatile directory, sudo modprobe fglrx, and then CTRL+BACKSPACE to start X, with some things a litle diferent in some ocasions. In Envy way, it downloads the same driver, so i think there must be a very simple thing that he does that causes not to have black screen. the only thing i did by hand is put in /etc/modules the line fglrx.

---

### Post by SKiFF on 2007-10-23
> **flamarro said:**
> Yes, for now i fixed my problem, i've got the 3D working.
I really dont know is why doing method 1 or method 2 following [this]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide") guide, in the end i always have that black screen, and, when i use Envy way, i get a fully desktop working, and, now in Gutsy, it even has fglrx probed from the beggining. I say this because, earlier i had to copy fglrx.ko to some that volatile directory, sudo modprobe fglrx, and then CTRL+BACKSPACE to start X, with some things a litle diferent in some ocasions. In Envy way, it downloads the same driver, so i think there must be a very simple thing that he does that causes not to have black screen. the only thing i did by hand is put in /etc/modules the line fglrx.

can you give a more detailed account or step by step one of your actions, because I tried all of the above as well and nothing... :/

---

### Post by ACLerok on 2007-10-23
I had this same problem with my x1950GT.  

If you've never manually edited your xorg.conf before, I wouldn't recommend doing this, but what I ended up doing was disabling the restricted drivers, manually updating to 8.40.1 (without using Envy) and then having to edit xorg.conf to remove all the other Screen directives except for the ones for fglrx.  The initial set up of Xorg put a Screen directive for radeon, and vesa.  After installing 8.40.1 and rebooting, it black screened exactly like the first time I enabled the restricted drivers.  After making sure that my Screen directive in xorg.conf was based only on fglrx, with the correct settings for my monitor, everything came up. 

I did have to reinstall compiz-settings-manager however, because starting the preferences would crash with a python bug.  

I have a feeling this had to do with me doing some manual installation of software from other repositories and then doing a dist-upgrade however.

---

### Post by arno77 on 2007-10-23
> **flamarro said:**
> Yes, for now i fixed my problem, i've got the 3D working.
I really dont know is why doing method 1 or method 2 following [this]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide") guide, in the end i always have that black screen, and, when i use Envy way, i get a fully desktop working, and, now in Gutsy, it even has fglrx probed from the beggining. I say this because, earlier i had to copy fglrx.ko to some that volatile directory, sudo modprobe fglrx, and then CTRL+BACKSPACE to start X, with some things a litle diferent in some ocasions. In Envy way, it downloads the same driver, so i think there must be a very simple thing that he does that causes not to have black screen. the only thing i did by hand is put in /etc/modules the line fglrx.

Sorry, but I am a bit lost. What exactly did you do?
Would be great if you could share this. I also wanna have a working X1300!!!
... and what the hell is "Envy way"?

---

### Post by tva995 on 2007-10-23
there have been several references to the ENVY way of installing the fglrx dirver...  what is the ENVY way?  where do I find the howto?  please advise.  thanks.

---

### Post by wvalters on 2007-10-23
Try here:

[http://albertomilone.com/nvidia_scripts1.html]("http://albertomilone.com/nvidia_scripts1.html")

---

### Post by flamarro on 2007-10-23
> **arno77 said:**
> Sorry, but I am a bit lost. What exactly did you do?
Would be great if you could share this. I also wanna have a working X1300!!!
... and what the hell is "Envy way"?

Sorry for so late response, only now come here...
previews post show the page of Envy, and as you may have seen, he made a gui for ATI and NVIDIA cards to be installed.
As for the past months i have been colecting some hints of how xorg.conf should be configured. Heres mine as attachment.
The end of the file kind of repeats in the section devices, dont now why, i think becauase i altered using screens and graphics to change my monitor.....
What i did was this..... In a fresh install od 7.10, i use restricted driver manager, choose ATI and restarted. Black screen in the end. Restarted again, choose safe mode, edited xorg.conf with vim /etc/X11/xorg.conf and change all fglrx to vesa.
Restarted again, edited /etc/modules, added a line fglrx,  downloaded Envy, used it, and restarted again. This time it was all it takes, it was the faster way ever.....
I, like you all, tryed everything that appears here to resolve this problem, this time was quick, but in 7.04 i experimented this way and didnt manage either, as i said before ( follow that links i gave, maybe helps )

---

### Post by blueturtl on 2007-10-24
Ok,

there are so many help requests here that I'm going to have to start differentiating your problems (in case they are caused by different things).

Firstly I would like all who posted having the blank screen after installing the ATI restricted driver to answer the following questions:

1. Are you using a laptop?
2. Did you upgrade to 7.10 through 7.04 (Feisty -> Gutsy) or did you perform a clean install?

> Some more info that may be useful. At start-up I receive messages I have not received before the update to gutsy. Among other things it says "kinit: no resume image ... doing normal boot" and "* booting hardware drivers / error receiving uevent message: No buffer space available"

I also receive a screen telling: "Ubuntu is running in low-graphics mode" and it gives the options to <Configure> (which doesn't work), <Shut down>, or <Continue>.

```
kinit: no resume image, doing normal boot
```
The resume image is used when your computer hibernates. Everything you have in the memory is dumped into the image which is then restored at boot time (this should recover things just as they were before your hibernated). No resume image simply means your computer is not returning from hibernation.

I'm a bit stumped right now, but I'll get back to you if I can think of something to try next (previously when I had problems with X, there were no ways other than xorg.conf to modify screen preferences, so I'm not sure I'm aware of everything that could be interfering with it).

> So I put in a dapper 64-bit disc and did all the upgrades to gutsy. when i try to use the new 2.6.22... kernel, the black screen shows up. I managed to get x going when i use the older kernel however.

If switching kernels helps you with this it's either a fault with the driver or the kernel (both things we can't really do anything about except wait). I recommend you stay with a kernel that works.

edit:

The instructions [here]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide") as well as [here]("http://albertomilone.com/nvidia_scripts1.html") seem valid. I cannot confirm for myself as I don't have an ATI card. Can anyone testify as to wether any of these work?

---

### Post by arno77 on 2007-10-24
> **blueturtl said:**
> 

1. Are you using a laptop?
2. Did you upgrade to 7.10 through 7.04 (Feisty -> Gutsy) or did you perform a clean install?



1. no
2. did upgrade from feisty to gutsy

---

### Post by blueturtl on 2007-10-24
arno, did you have the restricted drivers enabled before you upgraded?

Another question, is your home folder on a separate partition? The reason I'm asking is that if it is, it would be easy for you to try doing a fresh installation of the system without losing your files or settings. I know it's a rather lame suggestion, but it's a viable one if all else fails.

edit:

(from a previous poster)
> ...and then having to edit xorg.conf to remove all the other Screen directives except for the ones for fglrx. The initial set up of Xorg put a Screen directive for radeon, and vesa. After installing 8.40.1 and rebooting, it black screened exactly like the first time I enabled the restricted drivers. After making sure that my Screen directive in xorg.conf was based only on fglrx, with the correct settings for my monitor, everything came up.

This seems to suggest there may be something wrong in the xorg.conf.

Can you scout your xorg.conf to see if there are indeed multiple entries for Screen? If you find extra entries remove them and see if that helps. For example having multiple entries with the same identifier is bad.

The entries look something like this:

```
Section "Screen"
        Identifier      "Default Screen"
        Device          "nVidia Corporation NV28 [GeForce4 Ti 4200 AGP 8x]"
        Monitor         "M1700"
        Defaultdepth    24
        SubSection "Display"
                Modes           "1280x1024"     "1024x768"      "800x600"       "720x400"       "640x480"
        EndSubSection
EndSection
```

---

### Post by blueturtl on 2007-10-24
Continued... arno,

did you have the right resolution before you tried installing the restricted ATI driver?
Often times the automated driver installations make backups of your xorg.conf before they modify the real thing so I was just wondering if you can tell me what files are in the /etc/X11 folder? Just in case, since if there is a backup it might be a lot faster to restore that then to try and figure out what is wrong with the current file.

I'm gonna write some more after I get some sleep. Sleep deprivation rarely gets you good advise. ;)

---

### Post by tva995 on 2007-10-24
i'm using a desktop
i did a clean install of gutsy...

i have a radeon 9600 card..

first tried the easy way (apt-get install) the restricted driver... black screen...
uninstalled the that driver...
next installed the driver from the ati website... black screen...
i've looked over the xorg.conf file... everthing looks in order..

i'm open to suggestions....  thanks...

---

### Post by blueturtl on 2007-10-25
> i'm using a desktop
i did a clean install of gutsy...

i have a radeon 9600 card..

first tried the easy way (apt-get install) the restricted driver... black screen...
uninstalled the that driver...
next installed the driver from the ati website... black screen...
i've looked over the xorg.conf file... everthing looks in order..

i'm open to suggestions.... thanks... 

Have you tried [Envy]("http://albertomilone.com/nvidia_scripts1.html")? Some people report success using it instead of the official methods.

---

### Post by dalamar666 on 2007-10-25
Envy looks pretty cool.  Will it work from a live cd?  I am not getting the black screen people here are reporting, I jsut get command prompt.

---

### Post by aknight_sa on 2007-10-25
> **blueturtl said:**
> Have you tried [Envy]("http://albertomilone.com/nvidia_scripts1.html")? Some people report success using it instead of the official methods.

i have an ATI X1950 Pro AGP card.. and i tried envy... same problem..

---

### Post by flamarro on 2007-10-25
> **blueturtl said:**
> Ok,

there are so many help requests here that I'm going to have to start differentiating your problems (in case they are caused by different things).

Firstly I would like all who posted having the blank screen after installing the ATI restricted driver to answer the following questions:

1. Are you using a laptop?
2. Did you upgrade to 7.10 through 7.04 (Feisty -> Gutsy) or did you perform a clean install?



```
kinit: no resume image, doing normal boot
```
The resume image is used when your computer hibernates. Everything you have in the memory is dumped into the image which is then restored at boot time (this should recover things just as they were before your hibernated). No resume image simply means your computer is not returning from hibernation.

I'm a bit stumped right now, but I'll get back to you if I can think of something to try next (previously when I had problems with X, there were no ways other than xorg.conf to modify screen preferences, so I'm not sure I'm aware of everything that could be interfering with it).



If switching kernels helps you with this it's either a fault with the driver or the kernel (both things we can't really do anything about except wait). I recommend you stay with a kernel that works.

edit:

The instructions [here]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide") as well as [here]("http://albertomilone.com/nvidia_scripts1.html") seem valid. I cannot confirm for myself as I don't have an ATI card. Can anyone testify as to wether any of these work?

Glad for your help
This black screen, as it is known in the forum, the black screen of death, appears not only with the manual restricted drivers instalation.
In a fresh install, when i select the drivers selecting ATI restricted, when we do restart, in the end black screen, this way black screen appears **always**. When we follow the various manual restricted drivers installs, in the end, we have those black screen, one way or the other, when we dont have black screen, doing fglrxinfo appears MESA.... Then we try so numerous thing, small things, that eventually some combinations does the trick... In my case, this last time was the easiest, because i tryed Envy and it suddenly just worked.
Now i tryed the new drivers, and it was even worst, because, before i have the lack screen but monitor was on.... now monitor turns off..... 
ho well, restart, safe mode, edit xorg, change fglrx to vesa, restart, keeo on reading and try another thing :(

---

### Post by tva995 on 2007-10-25
yes... tried envy... alas, no success there either...

---

### Post by Doomguy0505 on 2007-10-25
The problem is the MESA modes can't be found, I say blame ATI

---

### Post by LeBurt on 2007-10-25
I resolved my black screen problem (ATI Radeon 9600) by adding this to xorg.conf, in the device section where you find driver "fglrx":

```
Option "BusType" "PCI"
```

See my [post]("http://ubuntuforums.org/showthread.php?t=590773") for more details.

Hope this helps...

---

### Post by arno77 on 2007-10-26
Hi Blueturtl.

> **blueturtl said:**
> arno, did you have the restricted drivers enabled before you upgraded?


Not that I know of. 

> **blueturtl said:**
> 
Another question, is your home folder on a separate partition? The reason I'm asking is that if it is, it would be easy for you to try doing a fresh installation of the system without losing your files or settings. I know it's a rather lame suggestion, but it's a viable one if all else fails.


I fear not. Did the recommended (automatic) partitioning "use all free space" or so. Attached a screen-shot of my partitions.

---

### Post by arno77 on 2007-10-26
... continued continued.

> **blueturtl said:**
> 
did you have the right resolution before you tried installing the restricted ATI driver?


No I didn't (although I did not receive a low-resolution message at boot) but it was also not that bad as it is now. 

> **blueturtl said:**
> 
Often times the automated driver installations make backups of your xorg.conf before they modify the real thing so I was just wondering if you can tell me what files are in the /etc/X11 folder? Just in case, since if there is a backup it might be a lot faster to restore that then to try and figure out what is wrong with the current file.


Attached screen-shot of content of etc\X11\

---

### Post by blueturtl on 2007-10-26
> Attached screen-shot of content of etc\X11\

There are indeed a few backups in there, but none of them look to be older than the ones we made. Aahhm, I'm sorry buddy, don't know what to tell you. :(

There is one more thing that might have something to do with this so here goes. The monitor you say you have is a Dell LCD. Do you have the manual handy? If you do (or if you're not tired of Googling) search for the information regarding it's horizontal synchronization and vertical refresh. In the xorg.conf file you have the monitor section like so:

```
Section "Monitor"
        Identifier      "Dell 1907FP"
        Option          "DPMS"
EndSection

```

Edit it so that it looks like this(the information below is provided via a Dell support link so it should be correct) :

```
Section "Monitor"
        Identifier      "Dell 1907FP"
        Option          "DPMS"
        HorizSync 30-81
        VertRefresh 56-76
EndSection
```

Reboot and see if it changes anything. This information is often regarded as obsolete unless you own a tube monitor (with tubes, you'd almost always have to have this information for proper refreshrates and resolutions). Nevertheless maybe we should give it a shot?

Also somewhere on the net someone listed the key combinations Ctrl + Alt + + and Ctrl + Alt + - (the last keys being + and -). You can also try those to see if it affects anything. We're going to have to hold a toast if we ever actually get this to work. ;)

edit: I provide you the horizync and vertrefresh values based on [this]("http://support.dell.com/support/edocs/systems/1907FP/en/about.htm#Specifications") link (Dell support US, and the model of the display you spesified in your earlier post).

---

### Post by skychris on 2007-10-26
Hi everyone,

I'm quite new on linux and beeing brainwashed by windows since DOS3.1, it doesn't help !!

so far, here's my problem :
laptop Acer Aspire 5670
ATI Radeon X1400
I installed feisty clean and it worked fine, upgraded to gutsy and worked almost fine, but when I tried to install the brand new ATI driver (released on Oct 26th) I got this damn black screen, I used to resolve some previous glitches the " sudo dpkg-reconfigure -phigh xserver-xorg" line but now that I have to boot on recovery mode, it doesn't work anymore. Any other way to reset those driver?

Thanks a lot
Chris

---

### Post by blueturtl on 2007-10-27
> Hi everyone,

I'm quite new on linux and beeing brainwashed by windows since DOS3.1, it doesn't help !!

so far, here's my problem :
laptop Acer Aspire 5670
ATI Radeon X1400
I installed feisty clean and it worked fine, upgraded to gutsy and worked almost fine, but when I tried to install the brand new ATI driver (released on Oct 26th) I got this damn black screen, I used to resolve some previous glitches the " sudo dpkg-reconfigure -phigh xserver-xorg" line but now that I have to boot on recovery mode, it doesn't work anymore. Any other way to reset those driver?

Thanks a lot
Chris

Hi Chris!

Did you see my earlier posts in this thread? Start reading from page 1 to go through all the suggestions previously made.

edit: to solve your intermediate problem, the line 'sudo dpkg-reconfigure -phigh xserver-xorg' probably doesn't work because as root (in safe mode) you do not need the 'sudo' prefix. Try entering the command without 'sudo' and see if it works then.

---

### Post by arno77 on 2007-10-27
> **blueturtl said:**
> 
There is one more thing that might have something to do with this so here goes. The monitor you say you have is a Dell LCD. Do you have the manual handy? If you do (or if you're not tired of Googling) search for the information regarding it's horizontal synchronization and vertical refresh. In the xorg.conf file you have the monitor section like so ....



Thank's. IIII'll try all  these and let you know.

I also tried this which I found at [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/150930](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/150930)
1) changed the resolution in /etc/usplash.conf to 1024x768:
   xres=1280
   yres=1024
2) executed the following:
sudo update-initramfs -u -k 

Wasn't a good thing to do, though. Monitor run crazy, everything was quadrupled. But I was able to change things back by using the old xorg.conf; so it seems I am back to the beginning.

---

### Post by skychris on 2007-10-27
HI blueturtl,

thanks for the quick answer. After spending several hours last night trying to fix this stuff, I got crosseyed and I missed some case sensitive command lines and directories ;o) my appologies... I,ve managed to get back a working desktop display but with the vesa driver and a wrong screen resolution. I will try to follow the instructions on the "Ubuntu Gutsy Installation Guide" linked above and will let you know...
thanks again

chris

---

### Post by skychris on 2007-10-27
... So far so good... BUT...

I followed the "Ubuntu Gutsy Installation Guide" and everything worked fine. But now, when I run the Synaptic Package Manager, it's trying to remove the nvidia-glx package but can't. it send back the following message : "E: nvidia-glx: subprocess post-removal script returned error exit status 2"   what dos it mean?

cheers

---

### Post by skychris on 2007-10-27
I got this message when I'm trying to solve it ( in Synaptic or in Terminal )
 sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  nvidia-glx
0 upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 13.7MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 120133 files and directories currently installed.)
Removing nvidia-glx ...
dpkg-divert: rename involves overwriting `/usr/lib/libGL.so.1.2' with
  different file `/usr/lib/nvidia/libGL.so.1.2.xlibmesa', not allowed
dpkg: error processing nvidia-glx (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 nvidia-glx
E: Sub-process /usr/bin/dpkg returned an error code (1)

???

---

### Post by blueturtl on 2007-10-28
> I followed the "Ubuntu Gutsy Installation Guide" and everything worked fine. But now, when I run the Synaptic Package Manager, it's trying to remove the nvidia-glx package but can't. it send back the following message : "E: nvidia-glx: subprocess post-removal script returned error exit status 2" what dos it mean?

cheers

Don't know what that means but you could try the command
```
sudo apt-get -f install
```

and see if that fixes it. Obviously do not have Synaptic running while you do this.

Also check the restricted driver manager and what it says about the state of the driver. You can find it in the System->Administration menu.

Edit: Guess you tried what I suggested already. Seems to me that something has overridden the package manager and it is causing trouble. You're gonna need someone more experienced than me to deal with this.

---

### Post by Igniteflow on 2007-10-29
A seriously big thank you Blueturtle, that worked a treat!



> **blueturtl said:**
> Guys, the Ubuntu team cannot fix the ATI driver because it is restricted (that's what it means). It's up to ATI.

If your system boots to a blank screen you can try logging in through a text terminal:

Hit Ctrl+Alt+F2 (the last key can be between F1 and F5)
You should get a login-prompt in text mode, log in using your username and password.

Now, type in the following command (we'll backup your current configuration):
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.mybackup

You will be prompted for your password again.

Next, enter the following command:
sudo nano /etc/X11/xorg.conf

A configuration file should appear, you can scroll up and down using the arrow keys.
Find where it says something like this:

```
Section "Device"
        Identifier      "Ati Technologies [Radeon model etc]"
        Driver          "fglrx"
        Busid           "PCI:1:0:0"
EndSection
```

Change where it says 'fglrx' to 'ati'.
Hit Ctrl+X to exit, hit Y to accept changes and finally hit Enter to finish.
Reboot and you should be back in graphical mode with the open-source ATI driver.

edit. In case you don't know how to reboot in text mode, you have to give the command 'sudo reboot' ;)

---

### Post by Monkeon on 2007-10-29
I too was getting the black screen of death problem with an ATI 9800 Pro.  I tried a bunch of the recommended fixes, but wasn't getting very far with it!  I finally decided that maybe it was something to do with my monitor (a viewsonic vx2025wm LCD).

Here's where it gets a bit weird...whenever I installed a fresh copy of Gutsy with my viewsonic plugged in, it went to low graphics and no 3d effects etc (only vesa worked).  So I plugged in a knackered old Samsung Syncmaster and...what do you know...working 3D effects right off the live CD, which continued  when installed.  I then nicked the Viewsonic settings off another xorg.conf I found floating around on the internet and voila, it now works as it should!

Now quite why Gutsy couldn't pick up a new model Viewsonic (which was picked up when I had a 9800 pro All In Wonder in my machine - but that's another story), but could pick up a legacy Samsung is anyone's guess....

Anyhoo, not sure this tale will help anyone, but thought I'd share it just in case!

Just got to pluck up the motivation to try to get fglrx working now!  On which note, is there a way to back up compiz settings....I'm thinking a compiz.conf file...or is that a bit too easy?

Cheers

Monkeon

---

### Post by MikeBrown on 2007-10-29
@blueturtl:
Thank You for your help! I also was getting a blank screen after enabling the ati download. The advice to take out the "sudo" command in the root, then change the given to "ati" worked like a charm!

---

### Post by skychris on 2007-10-30
Hi Blueturtl, 
Thanks again for your support,

I've already tried the command on a terminaL window, here's the log
************
I got this message when I'm trying to solve it ( in Synaptic or in Terminal )
sudo apt-get install -f
Reading package lists... Done
Building dependency tree 
Reading state information... Done
The following packages will be REMOVED:
nvidia-glx
0 upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 13.7MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 120133 files and directories currently installed.)
Removing nvidia-glx ...
dpkg-divert: rename involves overwriting `/usr/lib/libGL.so.1.2' with
different file `/usr/lib/nvidia/libGL.so.1.2.xlibmesa', not allowed
dpkg: error processing nvidia-glx (--remove):
subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
nvidia-glx
E: Sub-process /usr/bin/dpkg returned an error code (1)

**************

on top of that, I have a few softs that dont launch anymore, from Amarok to frozen bobbles...
would I have to reinstall it all ?

chris

---

### Post by blueturtl on 2007-11-03
> on top of that, I have a few softs that dont launch anymore, from Amarok to frozen bobbles...
would I have to reinstall it all ?

chris

I honestly don't have the answer to this. The information is not sufficient. To me it would seem some files may have been modified outside the package manager or you are/have been using some third party repository which is causing breakage. Sorry again. You should post this in a new thread to get proper attention, since most people who look at this thread are   either solving ATI display issues or looking for solutions to ATI display issues. Your problem falls under a different category at the moment.

---

### Post by skychris on 2007-11-03
Hi Blueturtl,
 you're right, I should've posted it somewhere else... sorry... but I solved the problem by removing manually the file that should have been overwritten, and it worked fine, I have now all my package up to date ;o)

---

### Post by jho3k on 2007-11-04
So I'm brand new to this and I let ubuntu (7.10 - Gutsy) install the Ati restricted drivers. On reboot I got the Black Screen Of Death. I booted to recovery mode from the moot menu (GRUB) and followed blueturtl's instructions (minus the 'sudo'):

> **blueturtl said:**
> Guys, the Ubuntu team cannot fix the ATI driver because it is restricted (that's what it means). It's up to ATI.

If your system boots to a blank screen you can try logging in through a text terminal:

Hit Ctrl+Alt+F2 (the last key can be between F1 and F5)
You should get a login-prompt in text mode, log in using your username and password.

Now, type in the following command (we'll backup your current configuration):
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.mybackup

You will be prompted for your password again.

Next, enter the following command:
sudo nano /etc/X11/xorg.conf

A configuration file should appear, you can scroll up and down using the arrow keys.
Find where it says something like this:

```
Section "Device"
        Identifier      "Ati Technologies [Radeon model etc]"
        Driver          "fglrx"
        Busid           "PCI:1:0:0"
EndSection
```

Change where it says 'fglrx' to 'ati'.
Hit Ctrl+X to exit, hit Y to accept changes and finally hit Enter to finish.
Reboot and you should be back in graphical mode with the open-source ATI driver.

edit. In case you don't know how to reboot in text mode, you have to give the command 'sudo reboot' ;)


On reboot I was able to logon again and was shown a prompt about using ubuntu in low quality graphics mode, it asked me to choose a driver so i chose the radeon driver (for my card) and selected 'generic lcd panel 1280 x 1024' (for my monitor), or somthing like that. On reboot I was able to go back to high res mode. Then I installed Envy, it did its thing but when it restarted I was back to BSOD. Again I followed blueturtl's instructions (change 'flgrx' to 'vesa' in 'xorg.conf) and after rebooting I now have high res back and also in the restricted drivers applet(?) it says the ati drivers are in use?! Thanks guys!

---

### Post by nixie21 on 2007-11-04
I boot fine now using the latest ATI drivers...  I can not get compiz working, I need to install xserver-xgl to make it work, but once I install that, the system is not stable as user switching, or any image intensive thing will get me the black screen???  I tried changing fglrx to ati, but no go on that?  Also, why do I have 2 device in my xorg.conf?? (for video card)

As of Now I have this (works fine, but no compiz)

nixie21@Main:~$ glxinfo | grep direct && glxinfo | grep glx && glxinfo | grep OpenGL
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI RADEON 9600 Series
OpenGL version string: 2.0.6958 Release
OpenGL extensions:
nixie21@Main:~$ fglrxinfo
display: :0.0 screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI RADEON 9600 Series
OpenGL version string: 2.0.6958 Release

xorg.conf =

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
# sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
Identifier "Default Layout"
Screen 0 "aticonfig-Screen[0]" 0 0
InputDevice "Generic Keyboard"
InputDevice "Configured Mouse"
InputDevice "stylus" "SendCoreEvents"
InputDevice "cursor" "SendCoreEvents"
InputDevice "eraser" "SendCoreEvents"
EndSection

Section "Files"

# path to defoma fonts
FontPath "/usr/share/fonts/X11/misc"
FontPath "/usr/share/fonts/X11/cyrillic"
FontPath "/usr/share/fonts/X11/100dpi/:unscaled"
FontPath "/usr/share/fonts/X11/75dpi/:unscaled"
FontPath "/usr/share/fonts/X11/Type1"
FontPath "/usr/share/fonts/X11/100dpi"
FontPath "/usr/share/fonts/X11/75dpi"
FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
Load "i2c"
Load "bitmap"
Load "ddc"
Load "dri"
Load "extmod"
Load "freetype"
Load "glx"
Load "int10"
Load "vbe"
EndSection

Section "InputDevice"
Identifier "Generic Keyboard"
Driver "kbd"
Option "CoreKeyboard"
Option "XkbRules" "xorg"
Option "XkbModel" "pc105"
Option "XkbLayout" "us"
EndSection

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ImPS/2"
Option "ZAxisMapping" "4 5"
Option "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
Identifier "stylus"
Driver "wacom"
Option "Device" "/dev/input/wacom"
Option "Type" "stylus"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "InputDevice"
Identifier "eraser"
Driver "wacom"
Option "Device" "/dev/input/wacom"
Option "Type" "eraser"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "InputDevice"
Identifier "cursor"
Driver "wacom"
Option "Device" "/dev/input/wacom"
Option "Type" "cursor"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "Monitor"
Identifier "EN9110"
Option "DPMS"
EndSection

Section "Monitor"
Identifier "aticonfig-Monitor[0]"
Option "VendorName" "ATI Proprietary Driver"
Option "ModelName" "Generic Autodetecting Monitor"
Option "DPMS" "true"
EndSection

Section "Device"
Identifier "ATI Technologies Inc RV350 AR [Radeon 9600]"
Driver "fglrx"
Option "VideoOverlay" "on"
Option "OpenGLOverlay" "off"
BusID "PCI:1:0:0"
EndSection

Section "Device"
Identifier "aticonfig-Device[0]"
Driver "fglrx"
Option "VideoOverlay" "on"
Option "OpenGLOverlay" "off"
EndSection

Section "Screen"
Identifier "Default Screen"
Device "ATI Technologies Inc RV350 AR [Radeon 9600]"
Monitor "EN9110"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 4
Modes "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 8
Modes "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 15
Modes "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 16
Modes "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 24
Modes "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
EndSection

Section "Screen"
Identifier "aticonfig-Screen[0]"
Device "aticonfig-Device[0]"
Monitor "aticonfig-Monitor[0]"
DefaultDepth 24
SubSection "Display"
Viewport 0 0
Depth 24
EndSubSection
EndSection

Section "DRI"
Mode 0666
EndSection

Section "Extensions"
Option "Composite" "1"
EndSection

---

### Post by blueturtl on 2007-11-11
> Then I installed Envy, it did its thing but when it restarted I was back to BSOD. Again I followed blueturtl's instructions (change 'flgrx' to 'vesa' in 'xorg.conf) and after rebooting I now have high res back and also in the restricted drivers applet(?) it says the ati drivers are in use?! Thanks guys!

You can make sure the ATI driver is in use by trying some of the 3D screensavers or alternatively by examining the output of the command:

```
glxinfo | grep OpenGL
```

This is what you want to be seeing:

OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI RADEON xxxx Series
OpenGL version string: 2.0.6958 Release

If you get something that looks more like this, you are not using the restricted driver:

OpenGL vendor string: DRI R300 Project
OpenGL renderer string: Mesa DRI R300 20060815 x86/MMX+/3DNow!+/SSE2 NO-TCL
OpenGL version string: 1.3 Mesa 7.0.1

> I boot fine now using the latest ATI drivers... I can not get compiz working, I need to install xserver-xgl to make it work, but once I install that, the system is not stable as user switching, or any image intensive thing will get me the black screen??? I tried changing fglrx to ati, but no go on that? Also, why do I have 2 device in my xorg.conf?? (for video card)

Compiz is hard with some ATI cards right now. You should check that your particular model is listed as being capable of running it with the current drivers (I know for example that the ATI XPress200 videocard in this laptop cannot run Compiz, and therefore I won't even attempt to make it work). You can most likely expect your problems to be fixed within the year as the new open source based ATI drivers mature and become available. Most likely we will be running Gutsy +2 by then, sorry.

You have multiple screen entries, but their identifiers are different. That means there are several profiles. I suspect the profiles have been created by driver setup (if you installed the ATI driver from their site) or Envy or any of the other things you might have tried to get the driver to work. The identifiers point to the use of aticonfig so that might have created the entries. Multiple entries in xorg.conf are not harmful unless their identifiers are identical or unless the profile in use is the wrong one.

---

### Post by Farenheit on 2007-11-29
Hey, I've been reading this for awhile and finally decided to post.  I have an ATI 1800XL All In Wonder and was getting the black screen of DEATH.  I tried all of the driver installation guides and none of them worked.  I saw that people were using the Envy loader so I gave that a shot.  I installed the driver the first time, then rebooted.  I was greeted with a black screen of death.  CTRL-ALT-F1, edited xorg.conf back to vesa, then rebooted.  Being pretty fed up at this point, I went back into Envy and then tried the manual ATI driver installation.  I chose the 7.11 drivers.  It rebooted, and what do you know, this time it worked.  I've got 3D now, verified to be using the fglrx driver.  Compiz looks like the win, 3D screensavers work, glxgears gets 9300 fps, life can continue again.  I don't know if that will help anyone, but it worked for me (who knows why).

Everything works well except video playback.  When I play a video file (mpg, wmv, etc.) it flickers horribly.  Don't know if that's just a bug with these drivers...who know's if there's a fix.
:
**EDIT** Figured out why video and games flicker.  On my system, Compiz seems to cause it.  I have been playing Enemy Territory Quake Wars, and I saw a post to disable Compiz before playing:
metacity --replace

Then I reenable it afterwards:
compiz --replace

No flicker :)

---

