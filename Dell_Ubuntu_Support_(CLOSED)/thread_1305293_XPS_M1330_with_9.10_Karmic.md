---
title: "XPS M1330 with 9.10 Karmic"
date: 2009-10-29
forum: Dell Ubuntu Support (CLOSED)
---

### Post by x C0MMAND0 x on 2009-10-29
Before I upgrade, what are some issues anybody has been having with upgrading/installing 9.10?  I currently have Dell XPS M1330 running 64bit 9.04.

Any issues for anybody out there?  I know it just came out, but I am still curious...

---

### Post by nwadams on 2009-10-29
brightness goes by two steps instead of one by default with the fn +up/down keys. Other than that everything works perfectly for me. 
just run alsamixer in a terminal and make sure both headphone jack volumes are set properly (one of them is 100, and the other is 80ish) and then use master to control everything as you probably do in 9.04

---

### Post by x C0MMAND0 x on 2009-10-30
Did you find a fix for the brightness control yet?  Also, did you test to see if the mic worked?

---

### Post by nwadams on 2009-10-30
No I haven't found a fix for the brightness. If you find one let me know. But it isn't a
buge concern for me cause I normally only have it either max or min. 

The mic works fine. Some tweaking of the volume Or sound manager settings may be required though. Works In skype as well.

---

### Post by x C0MMAND0 x on 2009-10-30
I just realized mine does that too under 9.04 with the brightness.  Guess I never noticed it before...

---

### Post by nwadams on 2009-10-30
mine's about half and half with 9.04 in terms of going one step or two steps. But atleast its consistant now. I have the intel graphics card, but i found that my battery life is better with karmic than before...

---

### Post by M1$3|2 on 2009-10-30
This may just be an issue with my setup but when I upgraded to Ubuntu 9.10 last night my track pad stopped working.  I can still navigate with the keyboard but no track pad for me.  I'm in the process of finding a solution, but I'm no guru by any means so it may take some time.

---

### Post by nwadams on 2009-10-30
Check your mouse settings. It may have just disabled the touchpad on upgrade for some reason.

Hope that helps.

---

### Post by x C0MMAND0 x on 2009-10-30
I have heard a lot of people have issues with the wireless adapter.  Currently, I am using Broadcom STA wireless driver from Administration > Hardware Drivers...

Is this true and is there a fix?

---

### Post by nwadams on 2009-10-30
hmm, its possible. I'm not sure on that, i'm one of the lucky ones with an intel wireless chip. But i'm fairly certain that there is some way to make the broadcom chips work.

---

### Post by x C0MMAND0 x on 2009-10-30
Would I be able to test this from a live CD?  Are you able to download and install drivers, and what if they require a reboot?  Then is a live CD of any use?

---

### Post by nwadams on 2009-10-30
make a bootable usb with a large persistant partition. You will be able to install drivers and reboot then (use the usb creater in ubuntu)

---

### Post by Zeedok on 2009-10-30
I've just done my upgrade but the video driver got the screen size wrong - I have turned off the propriety nvidia driver and everything is OK for now.  

Which Nvidia driver should I be using - 185??  I thought I read somewhere that there was a version 192 . . . if there is my system is not offering it.

---

### Post by tacantara on 2009-10-30
> **x C0MMAND0 x said:**
> Before I upgrade, what are some issues anybody has been having with upgrading/installing 9.10?  I currently have Dell XPS M1330 running 64bit 9.04.

Any issues for anybody out there?  I know it just came out, but I am still curious...

I have the same machine, but with a 32bit processor.  I was running 9.04 (Kubuntu for Dell) and had no problems.  I downloaded the RC of 9.10 a day before it went to final release.  My wireless wouldn't work, even after I removed network manager and installed wicd.  I can only get the Internet with a wire connection to my router.  I'm trying to work the problem now.  I've seen several posts regarding various problems with 9.10, and I've also seen several posts reporting no problems.

Try from the Live CD first.  That should give you some idea of how you can expect it to work, although I saw a post where someone did that, and found it to be a different experience (not necessarily good) once they installed it.

---

### Post by nwadams on 2009-10-30
I think 185 is the stable driver and 192 is the beta driver. With the nvidia driver enabled are you able to reset your screen size back to the proper resolution?

You can get a binary for the 190.42 driver of the nvidia website. You may want to try that driver.

I, unfortunatly have the intel chip, so i'm going to defer to any advice someone with an nvidia chip provides.

---

### Post by Zeedok on 2009-10-30
> **nwadams said:**
> I think 185 is the stable driver and 192 is the beta driver. With the nvidia driver enabled are you able to reset your screen size back to the proper resolution?

You can get a binary for the 190.42 driver of the nvidia website. You may want to try that driver.

I, unfortunatly have the intel chip, so i'm going to defer to any advice someone with an nvidia chip provides.

I have realised that it is not just the screen size, but compiz actually goes nuts with the nVidia driver.  I might try fiddling with nvidia-settings first, but I may need to use the newest driver.

---

### Post by Zeedok on 2009-10-30
So I reinstalled the 185 version of the driver and rebooted.  I then checked nvidia-settings and the screen size is correctly configured.  In CCSM I checked the "sync to VBlank" box and now the desktop screen size is perfect and compiz seems to be running OK.  There is also a "sync to VBlank" box in nvidia-settingds, which I have checked, so the next step is to reboot and see what happens to the login screen.

I'll let you know.

---

### Post by teward on 2009-10-30
Always go for the recommended and avalable nvidia driver, because otherwise the system becomes screwy.  Even though I'm running 9.04 Jaunty, I figured this out the hard way.

---

### Post by Zeedok on 2009-10-30
Yeah, I'm sticking with the recommended driver.  So "Sync to vblank" in CCSM sorts out the desktop, but my login screen is still not rendered properly - despite the correct settings in nvidia-settings.  I'm not sure where else to go with this . . .

EDIT: I have fixed this problem.  For some reason, my xorg.conf had this resolution entered as 1360 x 1568:
> 
Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
	SubSection "Display"
		Virtual	1360 1568
	EndSubSection

I'm not sure where that came from, I have never configured a monitor of that size.  Once I corrected the resolution, all is well.

---

### Post by kangyu29 on 2009-10-30
> **M1$3|2 said:**
> This may just be an issue with my setup but when I upgraded to Ubuntu 9.10 last night my track pad stopped working.  I can still navigate with the keyboard but no track pad for me.  I'm in the process of finding a solution, but I'm no guru by any means so it may take some time.

I had the same issue(mousepad) with my eeepc. fixed it by install the newest kernel - 31-14-generic. give this a try.

---

### Post by Zeedok on 2009-10-31
On the plus side . . . suspend and resume seems to work.  First time that's worked on my setup.

---

### Post by x C0MMAND0 x on 2009-10-31
Okay, so I made a bootable USB drive and took a whirl.  The first time, I got a kernel panic almost immediately and was disappointed.  The second times, I was able to enable the Broadcom STA driver from Hardware drivers, AND connect to my wireless network.  However, after rebooting, it simply said, "Driver is activated/enabled but not in use", and I couldn't enable it to get on the internet...

Any ideas?

---

### Post by geoffm on 2009-10-31
I upgraded from 9.04. After reboot, I got a non functionnal white screen instead of gnome. The problem was compiz. I could uninstall it blindly using the console (thanks tilda!), then I rebooted and launched metacity.

Fn up/down does increase/decrease brightness by 20%, which is quite unconvenient when you use it all the time.

More importantly, I experience a **severe lockup** when I suspend. I have to remove the battery. After reboot, bug manager says here was an important **kernel crash**, etc. This happens when I run kernel 2.6.31-14, when I run kernel 2.6.28-16 it suspends and wakes up fine, but audio doesn't work...

I can't even run through the System testing app, it crashes after the audio tests. All audio tests but one fail, but audio works with rhythmbox, youtube and VLC.

EDIT:
I reinstalled from scratch. It's flawless: compiz, suspend, and audio all work out of the box with the 2.6.31 kernel. I also enjoy considerably better graphic performance with compiz than ever before, and wake up from suspend and hibernate are at least 3 times faster. well worth the few hours reinstalling all.

---

### Post by zjlajko on 2009-11-02
> **x C0MMAND0 x said:**
> Okay, so I made a bootable USB drive and took a whirl.  The first time, I got a kernel panic almost immediately and was disappointed.  The second times, I was able to enable the Broadcom STA driver from Hardware drivers, AND connect to my wireless network.  However, after rebooting, it simply said, "Driver is activated/enabled but not in use", and I couldn't enable it to get on the internet...

Any ideas?

You do not need the Broadcom STA driver from Hardware drivers.  You can use the official kernel driver wl.
sudo modprobe -r b43 b44 ssb wl #remove these if loaded
sudo modprobe ieee80211_crypt_tkip
sudo modprobe wl #load the module wl

---

### Post by Fufkin on 2009-11-02
Ok I have some embarrassing noob questions, please humour me.  I've read the thread but it's a little confusing.

Video: Do I need to install drivers?  I'm not even sure what video card I have - I think it's just the default on-board one.  When I click "Hardware Drivers" it says "no proprietary drivers are in use on this system".

I seem to remember the last time I installed Ubuntu I just clicked a magic button that said something like "use proprietary drivers" but I can't find anything like that now.  

Sound: Rhythmbox works, but Amarok doesn't, and nor does Winamp under Wine.  There are no error messages, but nothing happens when I click play.  How would I begin trying to solve this problem?  I always get overwhelmed trying to understand Pulseaudio and all that jazz.  Do I need audio drivers or something?

Thanks for any assistance in advance!

---

### Post by nwadams on 2009-11-02
> **Fufkin said:**
> Ok I have some embarrassing noob questions, please humour me.  I've read the thread but it's a little confusing.

Video: Do I need to install drivers?  I'm not even sure what video card I have - I think it's just the default on-board one.  When I click "Hardware Drivers" it says "no proprietary drivers are in use on this system".

I seem to remember the last time I installed Ubuntu I just clicked a magic button that said something like "use proprietary drivers" but I can't find anything like that now.  

Sound: Rhythmbox works, but Amarok doesn't, and nor does Winamp under Wine.  There are no error messages, but nothing happens when I click play.  How would I begin trying to solve this problem?  I always get overwhelmed trying to understand Pulseaudio and all that jazz.  Do I need audio drivers or something?

Thanks for any assistance in advance!

hi. 

For the video drivers they are installed automatically if a non proprietary driver is available. Do you know if you have an intel graphics card or nvidia. If no proprietary drivers show up I assume that you have the intel card which had an open source driver. 

If you are uncertain About which card you have post the results of lspci here. If you are u sure about terminal commands just ask.

Because you are running gnome amoraknmay have unmet dependancies because it is a kde app. As for wine...I'd reccommend playing around with the sound settings in the wine config. 

Hope that helps.

---

### Post by Fufkin on 2009-11-02
Thanks for your reply!  

> **nwadams said:**
> hi. 

For the video drivers they are installed automatically if a non proprietary driver is available. Do you know if you have an intel graphics card or nvidia. If no proprietary drivers show up I assume that you have the intel card which had an open source driver. 

If you are uncertain About which card you have post the results of lspci here. If you are u sure about terminal commands just ask.


You are right:

```
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)

```

So that means I don't need a driver?  

> **nwadams said:**
> 

Because you are running gnome amoraknmay have unmet dependancies because it is a kde app.

You were right - I installed the "Kubuntu Restricted Extras" and it works fine now.


> **nwadams said:**
> 

As for wine...I'd reccommend playing around with the sound settings in the wine config. 


Right again!  

I checked the audio settings for wine and nothing was selected - chose ALSA and it works fine now.

> **nwadams said:**
> 
Hope that helps.

It sure did!  Thanks a lot.

---

### Post by nwadams on 2009-11-02
Yes because you have the intel graphics card the driver is installed automatically. As for having restricted drivers before I expect it might have been your wifi card or some other hardware that works out of the box now. 

But I am glad I was able to help. 

I do have a question though. Do you have the issue where changing brightness goes two steps instead of 1?

---

### Post by Fufkin on 2009-11-02
> **nwadams said:**
> Yes because you have the intel graphics card the driver is installed automatically. As for having restricted drivers before I expect it might have been your wifi card or some other hardware that works out of the box now. 

But I am glad I was able to help. 

I do have a question though. Do you have the issue where changing brightness goes two steps instead of 1?

Yeah I do, but I always have my brightness on max so it doesn't bother me.

Thanks again.

---

### Post by Jekshadow on 2009-11-03
Sound stops working...

---

### Post by nwadams on 2009-11-04
jekshadow. Can you check alsamixer in a terminal and see if the master was muted by accident? Also, if you dont' mind the hassle, if you make a bootable usb or cd of 9.10 and install a new install the problems that people are facing seem to be nonexistant. I dont' know why upgrading seems not to work in this version... but it may have something to do with better pulseaudio integration.

---

### Post by x C0MMAND0 x on 2009-11-04
> **nwadams said:**
> jekshadow. Can you check alsamixer in a terminal and see if the master was muted by accident? Also, if you dont' mind the hassle, if you make a bootable usb or cd of 9.10 and install a new install the problems that people are facing seem to be nonexistant. I dont' know why upgrading seems not to work in this version... but it may have something to do with better pulseaudio integration.

Are you saying it's better to do a clean install as opposed to an upgrade?

---

### Post by nwadams on 2009-11-05
> **x C0MMAND0 x said:**
> Are you saying it's better to do a clean install as opposed to an upgrade?

yes, unfortunately for this release at least, it appears to be better to do a clean install to get the full benefits of EXT 4 and grub 2. I have a flawless install on my xps m1330 by doing a clean install. 

Just a few tweaks have to be made though:
run alsamixer in the terminal to make sure both mic port volumes and PCM volume are maxed. Then controlling the output volume in all of the three outputs (speakers, head1, head2) can be controlled by the keyboard or pulseaudio's volume controls. 

The HDMI port may require some tweaking to get both audio and video through it...I haven't tested it but it caused headaches in jaunty...

Only issue...albeit minor is the brightness controls change the brightness by two steps...i'm still looking for a fix on that one. 

I have the intel graphics card and it works flawlessly. The nvidia one requires the restricted drivers still.

hope that helps everyone.

nwadams

ps. who wants to help me make a formal guide for 10.04

---

### Post by x C0MMAND0 x on 2009-11-05
A 10.04 guide for the XPS m1330?  I'd love to help with that.

---

### Post by youngerpants on 2009-11-06
I've been upgrading my M1330 for the last few releases (since 7.X?) with no problems.

This time I have 2 (small) issues;

1) Webcam is not recognised by any software and doesn't appear in /dev, although it does flash at me during startup

2) My touchpad does work, but I've lost the vertical scroll (really annoying!)... strangely, it doesn't appear in xorg.conf either... dmesg | grep mouse gives;

[    0.952058] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    1.004728] mice: PS/2 mouse device common for all mice

On the plus side, audio finally works properly, it was always a bit quiet previously

Any ideas would be appreciated.

---

### Post by nwadams on 2009-11-06
> **youngerpants said:**
> I've been upgrading my M1330 for the last few releases (since 7.X?) with no problems.

This time I have 2 (small) issues;

1) Webcam is not recognised by any software and doesn't appear in /dev, although it does flash at me during startup

2) My touchpad does work, but I've lost the vertical scroll (really annoying!)... strangely, it doesn't appear in xorg.conf either... dmesg | grep mouse gives;

[    0.952058] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    1.004728] mice: PS/2 mouse device common for all mice

On the plus side, audio finally works properly, it was always a bit quiet previously

Any ideas would be appreciated.

The gnome mouse settings under, preferences/mouse, has support for vertical or two finger scrolling. I hope that works for you. If not, I haven't yet heard why but there is some issue with touch pads not working at all after upgrading. So i'd say you are doing better than most ppl. Perhaps its time to do a clean install?

Best of luck

regards, 

nwadams

---

### Post by youngerpants on 2009-11-06
thats the funny thing, the tab for touchpad is missing under gnomes mouse proerties.

would really rather not reinstall from scratch...

---

### Post by nwadams on 2009-11-06
I am busy most of today but I will try to find a solution tonight.

---

### Post by nwadams on 2009-11-06
when you boot your system, which kernel is it booting to? There was an issue about grub not booting to the new karmic kernel by default which was causing problems.

---

### Post by LK_gandalf_ on 2009-11-07
I have an xps 1530 but it's almost the same.
I first upgraded my kubuntu from 9.04 to 9.10, then after a lot of crashes, problems and instability I decided to do a fresh install. A good decision.

The system now is PERFECT, everything works out of the box, from the wireless to the touchpad, the sound, video, everything. It's extremely fast, far more than the 9.04. I use Kubuntu 64 bit, with the / on ext4 and the /home on ext3.

I have only an issue: the multimedia keys don't work (play, rewind, forward...), except the volume up and down.
Does anyone have a fix for this?
Thanks

---

### Post by nwadams on 2009-11-07
mine seem to be working with totem. What media player are you using? I've had trouble getting them to work with some video players.

---

### Post by geoffm on 2009-11-08
So what's the difference between 32 bits and 64 bits Ubuntu? I read somewhere that only certain software takes advantage of the 64 architecture and it is less stable so if you don't use that rare specific software stick to 32 bit... is that right? Or is there actually a higher performance with 64 ubuntu on the XPS M1330?

---

### Post by nwadams on 2009-11-08
64 bit is just as stable as the 32 bit. All of our CPU's have been 64 bit for years. Nearly everything has just as good support in 64 bit as in 32 bit. As far as higher performance...i've never used 32 bit on mine so I couldn't tell you. I've been using 64 bit for nearly two years now, I recommend 64 bit.

---

### Post by mcnaz on 2009-11-15
Have a funny problem with Karmic and my M1330.

It happens when the laptop is on power and hibernated. When resuming from battery (from an on-power hibernate), laptop resumes to the welcome & login screen, freezes then hibernates again after a few seconds.

After the second resume, the welcome & password screen is usable and I am able to login. Occassionaly, however, the keyboard locks and random characters (i.e. zzzzzz... not password hashed) appear on the password dialogue edit box.

This is on on an Intel integrated graphics M1330.

Anybody else experienced this or can offer a solution? I have meanwhile raised a bug report on Launchpad.

---

### Post by ethanay on 2009-11-17
Fresh install of 9.10 w/ext4, these are my bugs:

1. resume from extended (several hours) suspend interrupted to suspend again -- 2nd resume works
2. updates require restart to regain functionality of updated components (e.g., gvfs, cups) without notifying user
	e.g., file system failure, printing failure
3. "printout mode" does not work with 810C printer driver through print server
	"controlled by 'printout mode'" non-functional -- must directly select dpi, color and quality settings	

4. gnome-do bugs...
	fails to launch home folder on initial autostart (--quiet)
		restart gnome-do required
	weather applet fails to update automatically
		persistent network error after elapsed time set in docklet settings
		manual updating required
		problem goes away when multiple locations are entered

Haven't submitted any bugs yet.  The system works wonderfully overall...

---

### Post by nwadams on 2009-11-17
@mcnaz

sorry for late reply. I did some playing around with my system. I dont' normally use hiberate but it works for me...well it takes on the order of 10 minutes to bring it fully out of hibernate and back up to speed.

about the keyboard locking and stuff. Does it show up in the password box itself or in a box similar to the search box if you type stuff in nautilus?

Keep me informed if you find a solution or have further problems.

@ethanay

suspend resume seems to work for me. Are you pressing the keys more than once, or otehrwise initiating suspend twice (closing lid etc). How much ram is your system running?

I'm sorry I can't help you with the rest of your problems. 
i'd make separate topics in the respective sections for all three of the rest of your issues. You'll be much more likely to get help for them that way. 

Good luck, and sorry I couldn't really help you.

I guess i'm going 0/2 tonight guys...not my night i guess...I'll keep my eye open for solutions though. 

Regards,

nwadams

---

### Post by ethanay on 2009-11-19
No worries -- just mentioning the bugs FYI

Suspend works for me mostly, but when I close the lid and leave it suspended for a while, then resume, it automatically suspends a 2nd time.  It's similar to this bug: 
[https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/149665](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/149665)

It is related to time:  if I suspend by closing the lid and resume within a few hours, it is fine.  If I suspend by pressing the button then it is fine.

However, if I suspend overnight by closing the lid, then it triggers a second suspend immediately upon resuming.

---

### Post by cygnis1 on 2009-11-20
I am also having problems with suspend on my xps 1330 running Karmic (clean install).  When I close the lid and open it up I get a black screen and can not resume.  Also how can I disable the touchpad?  the mouse preferences I can only choose to disable the touchpad while typing, not disable it altogether.  I download the touchpad control from the Ubuntu Software Center, and it gives me the option to disable the touchpad, but that only lasts 5 minutes at the most.  I have searched online for another touchpad controller, but haven't found one.
Cygnis1

---

### Post by Zoot7 on 2009-11-21
i myself have a Dell XPS M1530 and it's been pretty near flawless with Ubuntu since Gutsy. :)

> **cygnis1 said:**
> Also how can I disable the touchpad?
I know it's probably not the solution you're looking for but to my knowledge the touchpad can be disabled in the BIOS.

---

### Post by cygnis1 on 2009-11-21
there used to be a KDE app that would disable the touchpad, but you would have to do it for each session.  That was nice, in case you didn't have your mouse handy, or your batteries were dead.

---

### Post by Fr33d0m on 2009-11-22
System > Preferences > Mouse.  The Touchpad tab has a setting for that.

---

### Post by Kai69 on 2009-11-22
Hi all i also have a Dell XPS M1330 I installed ubuntu last weekend because windows xp went nuts on me never used linux before I did a full install no windows at all
so far insalled 185 driver for nvidia no problems with sound or graphics even skype works (webcam and mic) the only thing i am struggleing with is the HDMI witch does not work 
also the fan dosnt cut in very much is this because the cpu and graphics card are not working as hard, Im still trying to get my head around linux.

---

### Post by Fr33d0m on 2009-11-22
Well I'm quite disappointed in Dell's performance here.  I've searched for the fixes to problems that exist every upgrade such as the brightness adjustment moving in two increments and found that they seem to have abandoned the dell Ubuntu forums.  You can't post new threads and nothing has been posted all year.

I did find a post for the CD Eject button on the M1330: [http://ubuntuforums.org//showthread.php?t=115499]("http://ubuntuforums.org//showthread.php?t=115499")

Standard disclaimer applies.  This is a fix for prior versions and may not work for 9.10 so be careful.

Otherwise there might be help in the Dell PPA at: [https://launchpad.net/~dell-team/+archive/ppa]("https://launchpad.net/~dell-team/+archive/ppa")

Or you might find help at this wiki:  [https://wiki.ubuntu.com/InstallingUbuntuOnADellXPSM1330]("https://wiki.ubuntu.com/InstallingUbuntuOnADellXPSM1330")

There are also some links here that might help: [https://wiki.ubuntu.com/LaptopTestingTeam/DellXPSM1330]("https://wiki.ubuntu.com/LaptopTestingTeam/DellXPSM1330")

---

### Post by ethanay on 2009-11-22
> **Kai69 said:**
>  the HDMI witch does not work 


hi Kai69,

i haven't tested the HDMI on mine yet.  i think the standard configuration enables analog, and you have to manually switch to the digital output when you want to use it.  try switching to digital output and see if that enables HDMI:

open volume control via menu
preferences > sound
or via gnome bar icon
right click > sound preferences

> hardware tab > settings for selected device > choose HDMI

and see if selecting it/messing with anything there (volume?) can help enable HDMI sound :-k

---

### Post by Zoot7 on 2009-11-22
> **ethanay said:**
> open volume control via menu
preferences > sound
or via gnome bar icon
right click > sound preferences

> hardware tab > settings for selected device > choose HDMI

and see if selecting it/messing with anything there (volume?) can help enable HDMI sound :-k

One of the good things about Pulseaudio; it's very easy to choose your output device. :)

---

### Post by ethanay on 2009-11-23
Zoot7 -- can you confirm that HDMI out works?

---

### Post by Zoot7 on 2009-11-24
> **ethanay said:**
> Zoot7 -- can you confirm that HDMI out works?
Not with Karmic no, I haven't tried it yet.

I did however get it working with Hardy, by using Pulseaudio to route the audio through the HDMI port.

---

### Post by nwadams on 2009-11-24
I can confirm that it works in karmic. You have to set the audio output to that device though.

---

### Post by Kai69 on 2009-11-24
hi all i have made another thread for this problem but its still not resolved.
ok gone in system>pref>sound>hardware no HDMI listed. On graphics card Gforce 8400m gs when i plug the hdmi lead in my tv is recognised set to clone or twinview do not get sound or picture is there anything i am missing.
I have only been using linux ubuntu 9.10 full install no MS for a week and so far been happy still getting my head around terminal (never used it in MS) im a mouse clicker but every thing works apart from HDMI

---

### Post by Kai69 on 2009-11-24
Wireless printer works found and installed via wifi
HP-photosmart-C4500-Series

---

### Post by Kai69 on 2009-11-25
pulseaudio is this something i have to install. Im off work for a few days so tomorrow ill see if i can get hdmi working ill keep you posted.

---

### Post by ethanay on 2009-11-26
> **Kai69 said:**
> pulseaudio is this something i have to install. Im off work for a few days so tomorrow ill see if i can get hdmi working ill keep you posted.

pulseaudio should be installed by default...can you go to your sound preferences > hardware tab > and take a screenshot of the hardware profile list like in the attached photo?

i'm currently on someone else's computer that has no HDMI, but yours should have HDMI output options listed!  if it doesn't, the only things i can think of are
a. pulseaudio wasn't installed for some reason (corrupt installation?)
b. maybe HDMI was disabled in your BIOS somehow?

anyone else have any thoughts? let us know if you figure it out!

---

### Post by Kai69 on 2009-11-26
hi dont know how to take screenshot tried alsorts on sound panel (profile) i do have
Digital stereo (IEC958 ) output + analog stereo input if i set sound to this i lose sound through laptop speakers

---

### Post by ethanay on 2009-11-27
> **Kai69 said:**
> hi dont know how to take screenshot tried alsorts on sound panel (profile) i do have
Digital stereo (IEC958 ) output + analog stereo input if i set sound to this i lose sound through laptop speakers

1.Applications > Accessories > Take Screenshot
2.set to "grab the current window"
3.set "grab after a delay of X seconds" to ~5 seconds or more
4.click "take screenshot"
5.switch to sound preferences window, hardware tab
6.click on the "profiles" list
7.wait for the screenshot

:)

---

### Post by Kai69 on 2009-11-27
/home/kai/Desktop/Screenshot-Sound Preferences.png[IMG]file:///home/kai/Desktop/Screenshot-Sound%20Preferences.png[/IMG].

---

### Post by ethanay on 2009-11-28
That is very strange!  I have my laptop with me again -- see the attached picture for what my list looks like

Did your HDMI work in Windows?  The one thing I would say is try to reinstall.  Or boot in with the LiveCD and see if HDMI is recognized there.

Other than that, I have no more suggestions :(

---

### Post by Kai69 on 2009-11-28
Ahh ding dong!! when i got my laptop it had windows xp pro installed and hdmi didnt work then. I installed vista after xp went nuts and reinstalled all the drivers from dell which i downloaded from there website and burned to disk the drivers for the xps m1330 is for vista only (tried loading on xp wont install only recognised for vista) . I now have ubuntu only installed (please dont make me go to the dark side) lol 
i was just wondering if dell do drivers for ubuntu? I did notice a lot of the drivers for the xps also cover inspiron/lattitude/studio. just going to raid the website .

---

### Post by Kai69 on 2009-11-29
Hi all ok.. Did a lot of serching last night and found out dell have thier own version of ubuntu 9.04 so i downloaded the iso and burned to disk 1.8GB .
I have just run the disk as a live cd run i connected the hdmi lead went to System>Preferences>Display pressed the confure monitors button and it found my tv .
In 9.10 if I press sys >pref>disp i get [ATTACH]138027[/ATTACH] so i have to use nvidia settup but this dosnt work if in display i press no and bring up display box and press detect monitors nothing happens.
Do you think i should install 9.04????

---

### Post by ethanay on 2009-12-09
That is strange but good news!  Do you have a 9.10 live cd?  I would try the same with 9.10 -- my understanding is that Dell folds their changes (e.g., Dell-specific bug fixes) into the latest versions...but I could be wrong.  Use whatever works best for you!

ethan

---

### Post by br0nx finest on 2009-12-10
> **nwadams said:**
> hmm, its possible. I'm not sure on that, i'm one of the lucky ones with an intel wireless chip. But i'm fairly certain that there is some way to make the broadcom chips work.
I was able to get an older Dell laptop with a Broadcom wireless chip to work flawlessly, I just searched it via Google and found a link w/ a command that worked.
 
I'm going to try and search it back up now.

---

### Post by nwadams on 2009-12-10
> **br0nx finest said:**
> I was able to get an older Dell laptop with a Broadcom wireless chip to work flawlessly, I just searched it via Google and found a link w/ a command that worked.
 
I'm going to try and search it back up now.

ya. I keep forgetting how much things improve. I remember a year and a half ago and ndis wrapper was needed for some of the broadcom chips, and now most of them just work out of the box. And its only going to get better. If you find the link, or hte instructions please post them. Any help we can get the better. 

nwadams

---

### Post by Benny Bauer on 2009-12-18
Hello to All!

Just bought a used M1330 and read your interesting thread. 
I got nearly all working with the 9.10 64bit DVD. The HDMI works with the 190.42 Nvidia Driver from nvidia homepage. I plugged the HDMI cable into my denon receiver and configured the second detected screen with full HD resolution. Only after applying this, the HDMI gave a sound output. The only thing is that the signal is DolbyDigital 2.0 Stereo and not 5.1.
If anyone has a solution for 5.1 sound it would be nice to hear (read) :-)


Another, but a bit strange thing is to get the option GTM380 build in GPS to work....
but the christmas time will come....

Have nice days,

Benny

---

### Post by PsychedelicReaction on 2009-12-22
I own a xps 1330m and since the karmic upgrade suspension to ram doesn't seem to work: all i get is a black screen with a blinking cursor in the upper right cursor and the pc doesn't suspend at all, all i can do is an hard reboot. Any idea?

---

### Post by cygnis1 on 2009-12-23
I had the same problem.  I had an 8 gig flash card in my machine, and read a post about flash drives and suspend/hibernate problems.  I have removed the flash drive and now it suspends, although I have to log in to get to the desktop (I didn't have to log in again in previous versions of Ubuntu).  But at least it now works.  I hope this helps.
Cygnis1

---

### Post by PsychedelicReaction on 2009-12-23
LOL it works! Thank you :)

---

### Post by kngharv on 2010-01-01
> **Zeedok said:**
> I've just done my upgrade but the video driver got the screen size wrong - I have turned off the propriety nvidia driver and everything is OK for now.  

Which Nvidia driver should I be using - 185??  I thought I read somewhere that there was a version 192 . . . if there is my system is not offering it.

Though the proprietary Nvidia driver was the number one reason why my system crashes in the past, it has gone a long way and it's been very stable in my experience.  Because my previous experience with nvidia driver bring my entire system down in the past, i usually stay away from any of their experimental drivers.   

I am currently using their 190 driver (the latest stable release).  And it has been good to me.

I am looking forward to the nouveau driver.  But at the time I tried it, it doesn't support any of the 3D acceleration yet :)

Harv

---

### Post by pappfer on 2010-01-06
I own an XPS M1530 but it's almost the same.
For me everything works except surround sound. I can make it work but it's not the best solution. Details here: [http://ubuntuforums.org/showthread.php?t=1286863](http://ubuntuforums.org/showthread.php?t=1286863) and here: [http://ubuntuforums.org/showthread.php?t=1320013&page=7](http://ubuntuforums.org/showthread.php?t=1320013&page=7)

Also - a little bit different problem - my notebook temp gets extremely warm and touchpad starts acting weird as I described here: [http://ubuntuforums.org/showthread.php?t=1250929](http://ubuntuforums.org/showthread.php?t=1250929)

---

