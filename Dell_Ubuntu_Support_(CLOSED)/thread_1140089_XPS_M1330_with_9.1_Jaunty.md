---
title: "XPS M1330 with 9.1 Jaunty"
date: 2009-04-27
forum: Dell Ubuntu Support (CLOSED)
---

### Post by x C0MMAND0 x on 2009-04-27
What are the known issues people have been having with the Dell XPS M1330 and upgrading to Jaunty?  I have looked around a little bit, but before I upgrade I want to know if people have specific issues they have been having.

---

### Post by angelillo on 2009-04-27
I have installed 9.04, ant it's working perfectly. I performed a fresh install (not upgrade). I have tested Ubuntu and Kubuntu variants, and both seem to work properly with my XPS M1330.

---

### Post by compman25 on 2009-04-28
No issues here with 9.04 on my xps1330

---

### Post by Gausian on 2009-04-28
Can anyone confirm that the media buttons work, as well as the external remote?  I tried the volume buttons on the live cd and they worked.  just wondering what others experienced...

---

### Post by mihai.ile on 2009-04-28
I installed yesterday and tested the remote, works just fine. Didn't tested but the media should work also without problems.

---

### Post by brogdonbr on 2009-04-28
Glad to see everyone's having a smooth transition. Maybe you can help me with my little snag in the road--wireless networking stopped working after I upgraded. When I right-click on the network icon in the upper right corner of the screen, I see that both wired and wireless are enabled. When I click "edit connections", I see my old connection listed. It just won't let me connnect. When I left-click the icon, the "Wired Network" and "wireless Nwtworks" are greyed out.

If I open up "Hardware Drivers" in the System-->Administration menu, I see that the Broadcom B43 wireless driver is active. I disabled it, thinking maybe something in the kernal upgrade made it irrelevant and was causing a conflict, but nothing (and I cannot re-activate because I have no connection to the Internet).

Anyone have any clues???

Thanks in advance!

---

### Post by Gausian on 2009-04-28
well i went ahead and installed 9.04, and as the others say both the media buttons and remote work in gnome media applications.

as for you wireless troubles, im not too familiar with broadcom chips so i cant be of much help im afraid

---

### Post by x C0MMAND0 x on 2009-04-28
What about internal mic working and volume?  I remember that was a problem for me on 8.1, that I was able to workaround, but just wondering...

---

### Post by biocorp on 2009-04-28
> **x C0MMAND0 x said:**
> What about internal mic working and volume?  I remember that was a problem for me on 8.1, that I was able to workaround, but just wondering...
i must used the same workaroud as before ...( apt-get remove pulseaudio)

---

### Post by Gregstar on 2009-04-29
I have to say WiFi with Intel 4965 and the connection is crashing every ~ 3 hours. Also watching .avi files via WiFi on a SSHFS with totem, vlc, smplayer is very bad - every seconds buckering and sound is asynchron.

Also my battery time shortend a full hour! Probably I could not use Power savings for m1330 - suspend not working after using it.

---

### Post by mihai.ile on 2009-04-29
I didn't notice problems with my wireless (intel). I can't say anything about battery but it should be only a matter of time until someone finds out where and how to use the low power scripts.

---

### Post by antoine_ on 2009-04-29
Hi,

On my side, I made a double upgrade over the last two days : I went from the 8.04 customized for Dell to 8.10 and then 9.04.

I lost the visual effects. They were perfectly working under 8.10, but they are not any more under Jaunty. It seems I have a problem with the drivers. On the wireless side, I did not notice any problem.

I use Intel chipset for visual effects, I do not have a graphic card. The drivers seem to be installed.

```
$ aptitude search intel
p   intel-microcode                 - Processor microcode data file for Intel CP
v   intel-rng-tools                 -                                           
p   intel2gas                       - A converter from NASM assembly language to
i A libdrm-intel1                   - Userspace interface to intel-specific kern
p   libdrm-intel1-dbg               - Userspace interface to intel-specific kern
i   xserver-xorg-video-intel        - serveur X X.Org -- pilote d'affichage Inte
p   xserver-xorg-video-intel-dbg    - X.Org X server -- pilote d'affichage Intel
antoine@dell-desktop:~$ 

```

I made abackup of my xorg.conf before update, and it did not change. So it must come from somewhere else. Do you have any idea why it does not work ?

---

### Post by antoine_ on 2009-04-29
Ok I found the answer on a french Forum. In fact this is "normal". They problem should be solved in a next upgrade.
[https://wiki.ubuntu.com/JauntyJackalope/ReleaseNotes#Display%20freezes%20with%20Intel%20graphics%20cards](https://wiki.ubuntu.com/JauntyJackalope/ReleaseNotes#Display%20freezes%20with%20Intel%20graphics%20cards)

It is possible to make it work anyway, despite the risks.

---

### Post by sultanoswing on 2009-04-29
Absolutely no problems with the installation of 9.04 - pretty much everything working out of the box, with no need to tweak the screen dimmer controls. Sound is working. I install NVIDIA drivers manually from the shell (I find it easier to keep the latest versions this way), and have had no hassles.

Wireless and bluetooth also both working flawlessly from the default install.

HOWEVER - for some unknown reason, the dist-upgrade method didn't work (from 8.10), so I was forced to do a fresh install - which was fine, since I wanted to move to ext4 anyway.

---

### Post by xoom on 2009-04-30
I'm having some issues with m1330 and Jaunty. 

My audio still doesn't work correctly (also an issue in hardy AND intrepid). The volume control only as if 75% is 0%, anything below has essentially muted the audio.

Also, a new problem with the jaunty upgrade. The xorg.conf is not using vesa or nvidia drivers (see below). as a matter of fact when enable the nvidia drivers, 180, 173 or 185(beta), with the xorg reconfigured automatically, the screen comes up black with no gdm. While it is running with whatever generic driver it uses, it has all kinds of weird artificats on the screen.

xorg.conf
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

---

### Post by Technoviking on 2009-05-05
I have had very few problems with my Dell XPS m1330 in Ubuntu 9.04. The ones I have seen are.

[LIST=1]
[*]Internal Mic and Volume: Pulse still has issues with the HDA-Intel sound card. sudo apt-get remove pulse worked for awhile, but then my laptop stopped detect my sound card for no apparent reason. Start working again after re-installing pulse.
[*]Eject button does not work with CD/DVDs.
[/LIST]

T-V

---

### Post by pormogo on 2009-05-14
Anyone with Intel GMA video running into issues returning from suspend. It seems like the second time I return from suspend it bounces me back to the GDM login and I lose all my work. It's clearly coming back from suspend (as no computer I have seen boots that quickly) but for some reason my gnome session is lost :(

To be honest I don't think it has anything to do with my video card but this doesn't seem to be a widely reported issue... It's really screwed me over a few times, a fix would be absolutely awesome.

---

### Post by 1jackjack on 2009-05-15
I've recently done a fresh install of jaunty on my m1330 (keeping my old /home partition, which worked great at keeping ALL my apps settings!). The issues mentioned cover everything I wanted to say, so here are my experiences:

Sound: everything worked just fine except skype, which was a real hassle to get working. here's a summary of my experiences and the final settings that worked for me: [http://www.ubooboo.net/zimPage.php?page=Skype_Setup](http://www.ubooboo.net/zimPage.php?page=Skype_Setup)

Media buttons: eject doesn't work (no biggie). play/pause/stop/skip have never worked with my media player (songbird). volume/mute worked initially, but NOT after above skype fix. I had to go menu>system>prefs>sound and change device back to HDA Intel (Alsa mixer). This then needs to be changed back for skype calls :(

Wireless: works just fine at home, drops out occassionally while i'm at uni when it didn't use to, but it always auto re-connects.

Internal mic & vol: didn't have to remove pulseaudio like others have. see above skype fix.

Battery life & suspend: works just fine (havent fully tested battery life yet, but seems normal so far).

Visual effects: found workaround for m1330 hardware being blacklisted for compiz (see ENABLING COMPIZ section on this page: [http://www.ubooboo.net/zimPage.php?page=Setup_Ubuntu](http://www.ubooboo.net/zimPage.php?page=Setup_Ubuntu)).

@xoom: by default, my volume manager at 50% has always been silent. have you tried r clicking volume applet in system tray, and clicking prefs. Make sure Device is HDA Intel (Alsa mixer), and select PCM for a better range. If PCM is not there, you need to r click volume applet and go 'open vol control', select the above device, and go prefs, and then check PCM.

@pormogo: I have the integrated Intel GMA graphics in my m1330, and suspend works fine.

---

### Post by bigbrovar on 2009-05-16
> **1jackjack said:**
> I've recently done a fresh install of jaunty on my m1330 (keeping my old /home partition, which worked great at keeping ALL my apps settings!). The issues mentioned cover everything I wanted to say, so here are my experiences:

Sound: everything worked just fine except skype, which was a real hassle to get working. here's a summary of my experiences and the final settings that worked for me: [http://www.ubooboo.net/zimPage.php?page=Skype_Setup](http://www.ubooboo.net/zimPage.php?page=Skype_Setup)

Media buttons: eject doesn't work (no biggie). play/pause/stop/skip have never worked with my media player (songbird). volume/mute worked initially, but NOT after above skype fix. I had to go menu>system>prefs>sound and change device back to HDA Intel (Alsa mixer). This then needs to be changed back for skype calls :(

Wireless: works just fine at home, drops out occassionally while i'm at uni when it didn't use to, but it always auto re-connects.

Internal mic & vol: didn't have to remove pulseaudio like others have. see above skype fix.

Battery life & suspend: works just fine (havent fully tested battery life yet, but seems normal so far).

Visual effects: found workaround for m1330 hardware being blacklisted for compiz (see ENABLING COMPIZ section on this page: [http://www.ubooboo.net/zimPage.php?page=Setup_Ubuntu](http://www.ubooboo.net/zimPage.php?page=Setup_Ubuntu)).

@xoom: by default, my volume manager at 50% has always been silent. have you tried r clicking volume applet in system tray, and clicking prefs. Make sure Device is HDA Intel (Alsa mixer), and select PCM for a better range. If PCM is not there, you need to r click volume applet and go 'open vol control', select the above device, and go prefs, and then check PCM.

@pormogo: I have the integrated Intel GMA graphics in my m1330, and suspend works fine.

I also had problems using skpe on my m1330 . then i downloaded and installed the dell jaunty reinstall image from here [http://linux.dell.com/wiki/index.php/Ubuntu_9.04]("http://linux.dell.com/wiki/index.php/Ubuntu_9.04")
and that fixed the issue, i can now use skype with pulse audio enabled for the first time in my life .

---

### Post by 1jackjack on 2009-05-16
sheesh, that dell image is 1.8GB! before i go for it, could you just clarify that it also works with the volume media buttons?

---

### Post by x C0MMAND0 x on 2009-05-17
**FIX FOR THE EJECT BUTTON**

Simply add this to /etc/sysctl.conf:

```
# Unlock the CDROM eject button
dev.cdrom.lock=0
```

You have to restart for it to take effect.

---

### Post by 1jackjack on 2009-05-17
@commando thanks a lot, worked for me!

---

### Post by csowm5je on 2009-05-18
Looks like latest updates to intel driver significantly improves performance. Google earth would not render properly but with latest update it works perfectly and glxgears increased from 320 to 550.

---

### Post by pormogo on 2009-05-18
csowm5je, have you tried enabling UXA support in /etc/X11/xorg.conf?

Section "Device" "AccelMethod" "uxa"

my performance was absolutely abysmal until I enabled uxa support.

---

### Post by csowm5je on 2009-05-19
my /etc/X11/xorg.conf is blank! 
(please ignore - created xorg.conf and modified)
(login as root, alt+ctr+F2, killall gdm, X -configure, mv xorg.conf.new /etc/X11/xorg.conf)
 Thanks Pormogo

---

### Post by pormogo on 2009-05-19
No problem. I still seem to be having issues resuming from suspend that I just can't seem to resolve :( It looks like the machine suspends and returns from suspension correctly however I'm staring back at GDM and I have a fresh login and all my work is gone. 

I've made a thread and bumped it a few times but there's nofeedback in it. I'm close to opening up a launch pad bug for this sucker since I just cannot seem to figure out why this is happening and it's really starting to annoy me.

---

### Post by 1jackjack on 2009-05-19
I'm having trouble running a 3D game that worked ok in Hardy, so...

@csowm5je How do we install the latest intel drivers? If I go menu>system>admin>hardware drivers, it says 'no proprietary drivers are in use'. Is it a synaptic package? I have these packages installed currently:
xserver-xorg-video-i740 (v1.2.0)
xserver-xorg-video-intel (v2.6.3)
Or do you have to compile it from source?

@pormogo Here is the current contents of my xorg.conf:
> 
Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
		Virtual	2304 1024
	EndSubSection
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

But if I add your line to the end, I get an invalid file. Does it need an 'EndSection'? Can you have 2 "Device" Sections defined? Should it replace the other one, or maybe add to it? I don't know much about X configurations...

Cheers

---

### Post by csowm5je on 2009-05-19
did you look at this thread
[http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)

---

### Post by 1jackjack on 2009-05-19
mmmmm perfect, thanks

---

