---
title: "Dell Mini 9 and Ubuntu 9.04-someone to share experience?"
date: 2009-04-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by vickoxy on 2009-04-21
Hi,
i run Dell´s Ubuntu 8.04 on my Dell Mini 9, and i tried some other distros (live versions)-they worked ok. Did anyone install 9.04 and maybe could tell me how is working experience with it? I am very pleased with LPIA Ubuntu 8.04, but there are many advantages of installing full version of Ubuntu. So i need advice-should i do it or not?
So, these are my aditional questions:
1) how fast ist boot/start up
2) are there many problems with drivers?
3) does it freeze as Dell´Ubuntu?
4) How is Compiz working?
5) should i set up ext4 filesystem/does it fast up the system or slow it down?
etc...

So, any advice and impressions are welcome.
Thanks

---

### Post by armandh on 2009-04-21
Ive run 9.04 beta live but I would stick with 8.10 for a matured OS, one that has already been tested in the wider world as a release and patched. I'd wait for mid summer unless it is dual boot with 8.10

it seems a bit faster than 8.10 even live from a usb memory stick
did not get compiz working but it may now in rc. [fine in 8.10]
no driver problems, wifi OOTB
have not used delbuntu in some time but I was not happy with it
8.04.1 up have been better

---

### Post by paraa on 2009-04-21
Hi,

I installed 9.04 UNR yesterday but removed the UNR stuff ;-) 
* Everything works out of the box (I didn't check the SD Card Reader yet). So mainly no driver problems.
* Filesystem is ext4 with some SSD extra options like "noatime". Works fine so far
* Flash 10 + Firefox is driving me crazy. Youtube is fine but other flash movie pages suck
* no freezing yet, even hibernate works very good
* battery lasts for about 4h depending on load
* removed Compiz and returned to Metacity for performance reasons

At the moment I'm thinking of installing LPIA Version but there are no shared experiences about that so far.

---

### Post by snowpine on 2009-04-21
I have tested both i386 and lpia versions of 9.04 on my mini 9. Both work fine, you can't go wrong with either. With my naked eye, I can't tell a difference between the two in terms of battery life (4 hours), boot time (about 40 seconds), etc. (If somebody wants to recommend a good benchmarking tool, I'd be happy to post results.) The main advantage of i386 is a larger repository of applications. Also, lpia is not available as a live cd, so you can't try it before you install. i386 supported my Mini 9 wireless, but lpia did not until I installed the linux-restricted-modules package. Compiz seems a little glitchy (some flickering) but I am currently using the Openbox windows manager (CrunchBang desktop; a full CrunchBang lpia install is not currently possible because a few packages are missing from the lpia repository) with no problem. Ask me if you have any specific questions.

---

### Post by vickoxy on 2009-04-21
> **snowpine said:**
> I have tested both i386 and lpia versions of 9.04 on my mini 9. Both work fine, you can't go wrong with either. With my naked eye, I can't tell a difference between the two in terms of battery life (4 hours), boot time (about 40 seconds), etc. (If somebody wants to recommend a good benchmarking tool, I'd be happy to post results.) The main advantage of i386 is a larger repository of applications. Also, lpia is not available as a live cd, so you can't try it before you install. i386 supported my Mini 9 wireless, but lpia did not until I installed the linux-restricted-modules package. Compiz seems a little glitchy (some flickering) but I am currently using the Openbox windows manager (CrunchBang desktop; a full CrunchBang lpia install is not currently possible because a few packages are missing from the lpia repository) with no problem. Ask me if you have any specific questions.

Ok, did you test non lpia boot time (is it 40 sec?)? After hibernating/standby-how fast did it come up. How are Firefox and OpenOffice working (are there problems with Firefox Windows - sometimes it goes in full modus...)-is it worth to install 9.04? Or it is better to stick with lpia 8.04?

---

### Post by vickoxy on 2009-04-21
> **paraa said:**
> Hi,

I installed 9.04 UNR yesterday but removed the UNR stuff ;-) 
* Everything works out of the box (I didn't check the SD Card Reader yet). So mainly no driver problems.
* Filesystem is ext4 with some SSD extra options like "noatime". Works fine so far
* Flash 10 + Firefox is driving me crazy. Youtube is fine but other flash movie pages suck
* no freezing yet, even hibernate works very good
* battery lasts for about 4h depending on load
* removed Compiz and returned to Metacity for performance reasons

At the moment I'm thinking of installing LPIA Version but there are no shared experiences about that so far.

Can you specify Firefox problems (i use it a lot+ OpenOffice)

---

### Post by paraa on 2009-04-21
My Firefox problemy may result from only 1GB ram.
Firefox feels slower than every other app.

---

### Post by vickoxy on 2009-04-21
> **paraa said:**
> My Firefox problemy may result from only 1GB ram.
Firefox feels slower than every other app.

I have also 1 GB. But it seemed to me that live version of Ubuntu 9.04 is faster than Lpia 8.04. Still i didn´t test video streaming and other stuff...

---

### Post by snowpine on 2009-04-22
> **vickoxy said:**
> Ok, did you test non lpia boot time (is it 40 sec?)? After hibernating/standby-how fast did it come up. How are Firefox and OpenOffice working (are there problems with Firefox Windows - sometimes it goes in full modus...)-is it worth to install 9.04? Or it is better to stick with lpia 8.04?

Boot time is about the same for both--40 seconds from power on to a usable desktop (plus a couple of seconds to type my password). I do not use hibernate (no swap) and resume from suspend takes only a couple of seconds. Firefox runs okay (occasionally it will freeze up for a couple of seconds) and never comes close to maxxing out my 1gb of ram. I do not have Openoffice installed.

I can't recommend whether you should stick with 8.04 or install 9.04. One is a reliable, stable, long term support release, and the other is a beta version of an upcoming release. You have to choose based on your personality, computing needs, and tolerance for risk. :)

---

### Post by vickoxy on 2009-04-22
I have one more question-does xfce/kde really speed up the system, or is gnome accectable solution for dell mini 9 with 1GB Ram? I can tell that this version is very fast for my needs-altough, i noticed that  firefox get tired/slow with more tabs opened (is there some stable but faster alternative?)

---

### Post by snowpine on 2009-04-22
> **vickoxy said:**
> I have one more question-does xfce/kde really speed up the system, or is gnome accectable solution for dell mini 9 with 1GB Ram? I can tell that this version is very fast for my needs-altough, i noticed that  firefox get tired/slow with more tabs opened (is there some stable but faster alternative?)

The Mini 9 can handle a Gnome desktop just fine. I personally use Openbox as my windows manager, though this is more a matter of personal preference (rather than "Gnome is too slow").

Firefox is a great browser; there are many tips out there on the internet for speeding up Firefox. One thing I do is Edit->Preferences->Advanced->Network and set the cache to 0mb. This cuts down on read/write to the disk, which of course is a slow SSD. 

Another browser that I like that seems a little faster than Firefox is Epiphany-browser. It is part of the Gnome project, so it is quite stable in my opinion.

---

### Post by vickoxy on 2009-04-23
And yes, maybe the biggest issue why should i take full version of Ubuntu 9.04 is my Canon MP620 Printer. I make it work with LPIA but i need to tweak a lot (force architecture...), and with full version it is not such a big problem.
But as said, Dell´s 8.04 LPIA works fine, and i would upgrade to 9.04 only if advantages are really noticeable. I willl wait few days to see how are thinkgs with 9.04 developing.

---

### Post by paraa on 2009-04-23
There are 2 bugs concerning the SD Card Reader.
In some cases the system does not detect the card properly.
Theres a workaround for this. Just add

options sdhci debug_quirks=1

to the /etc/modprobe.d/options file.

The second bug (both are already filed but not fixed yet(9.04rc)) causes the suspend mode to crash when the system was suspended with a mounted SD card.
Some eeePC guys wrote a patch but I don't think that it would work for Mini 9. Anyone got a good idea on this case?

---

### Post by vickoxy on 2009-04-23
Hi,
i tried to install on dell mini 9 9.04 but it crahes every time on 49% (reporting some error - cd/dvd is maybe not clean...). Anyone knows what it should be? I downloaded the newest version of 9.04.

---

### Post by anjilslaire on 2009-04-23
Did you burn it slowly, like at 4x? Boot up and run th "Check media/disc" option to see if the burn is good.

---

### Post by vickoxy on 2009-04-23
> **anjilslaire said:**
> Did you burn it slowly, like at 4x? Boot up and run th "Check media/disc" option to see if the burn is good.
No, i made USB (with unetbootin) Stick ...

---

### Post by anjilslaire on 2009-04-23
ah, tha could be a problem then. I've done several usb stick installs. It's only gone bad once. Format it and try again. 
Personally, I don't use Unetbootin, though. I use the "Create a USB Startup disc" included in 8.10.

---

### Post by vickoxy on 2009-04-23
Well, i made installation of Beta 9.04 hoping that upgrade will be automatically, but i have some problems:
1) wifi won´t activate automatically after standby
2) synaptic can not find any programm (e.g. vlc) that i need
3) after standby there pop up login window (need to type my password-which i don´t won´t to do)
4) i am NEWBIE...

Is there any easy way to solve this problems?

---

### Post by jespdj on 2009-04-24
I have downloaded [Ubuntu Netbook Remix](http://www.ubuntu.com/getubuntu/download-netbook) 9.04 yesterday, which is now an official version of Ubuntu besides the desktop and server versions.

I've installed it on my Mini 9 and I love it! It boots really fast (about 20 seconds from the GRUB boot screen to the login prompt), and the application launcher is very nice. The adaptations to make Ubuntu more useable on a small screen are really good.

Note that the download page has a link to [installation instructions](https://help.ubuntu.com/community/Installation/FromImgFiles) for putting the image on an USB stick.

I'd highly recommend UNR 9.04 for the Mini 9! :KS

---

### Post by vickoxy on 2009-04-24
Ok, i reinstalled dactory  dell´Ubuntu-but still want to aks you something- do you got login window after hibernation/standby in 9.04 or it log you automatically? To me is annoying to add password each time after login.

---

### Post by snowpine on 2009-04-24
> **vickoxy said:**
> Ok, i reinstalled dactory  dell´Ubuntu-but still want to aks you something- do you got login window after hibernation/standby in 9.04 or it log you automatically? To me is annoying to add password each time after login.

Check your power management and screensaver options; I'm pretty sure you can set it to not ask for a password. :)

---

### Post by Cowchip7 on 2009-04-24
> **snowpine said:**
> Check your power management and screensaver options; I'm pretty sure you can set it to not ask for a password. :)

That should do the trick.

---

### Post by vickoxy on 2009-04-24
So now my short impressions with 9.04 desktop edition:
1) language setup didn´t work out of the box-need to install it (no big deal, thanks, ryuko2002)
2) couldnt fix login after suspend/hibernation...annoying
3) synaptic didn´t work (i fixed it, although) - thanks, **reflex**
4) boot up time is not so impressive as delbuntu (yesterday cam new dell´s updates, and i think it is booting now under 20 sec-with 9.04 it is 40-50 sec)
5) firefox works a little bit faster in 9.04, but not much faster
6) wifi does not remember password in 9.04  after restart or hibernation/standby-didn´t try to fix it
7) compiz works in 9.04 perfectly and fast enough...

So, after all, i returned to dellbuntu 8.04. It is little bit dissapoiting that i can not use 9.04 out of the box, but i am impressed with Linux allready (dell ubuntu 8.04) and i will stick to this version because it works really good for me (e.g. even Apple Bluetooth Keyboard works fine, external monitor works super-just plug in, logout-wait 10 sec and you have auto adjusted external monitor). Of course, it is in our human materialistic nature to have the newest products, but i think that i can live with some 2008 System just well (as i remember-i used Win 95 for 6-7 years, and was just happy to have something...but was never delighted with windows, as i am with linux-and just one more time i have to say-i used xandros and linpus and was also happy with those systems...)

So, i will come back to newest ubuntu versions, but in couple of months. Thank you all for help and advices!


(did anyone noticed how often i use "so"?)

---

### Post by GsL9vBab on 2009-04-24
Thanks for the summary.

What I am trying to figure out is if there are speed/power efficiencies with going with a lpia build environment vs i386.  I would guess that the atom architecture has multimedia command extensions that go well beyond what the origional i386 instruction set.

Does anyone know if anyone at Canonical has considered a .lpia release stream?  Dell must have had a reason for requesting this build for its 8.04 release in the Mini 9's.

---

### Post by GsL9vBab on 2009-04-24
Where did you find a .lpia version of 9.04?

---

### Post by Brandon Williams on 2009-04-24
> **GsL9vBab said:**
> Where did you find a .lpia version of 9.04?

You can find the lpia alternate install CD here: 

    [http://cdimage.ubuntu.com/ports/releases/jaunty/release/](http://cdimage.ubuntu.com/ports/releases/jaunty/release/)

That's what I installed from. I am told that the one installer bug that I encountered at the time (just after beta) has since been fixed. It was a minor issue that was easily handled post-install, but again, the bug is marked fixed. I just haven't been willing to do another install to verify :-)

---

### Post by snowpine on 2009-04-24
> **GsL9vBab said:**
> Where did you find a .lpia version of 9.04?

From [http://cdimage.ubuntu.com/ports/releases/9.04/release/](http://cdimage.ubuntu.com/ports/releases/9.04/release/) which unfortunately is SLOOOOOW the past 24 hours since Jaunty's release. (I downloaded it weeks ago when it was in beta.)

---

### Post by novice_dell on 2009-04-24
I am a new Linux user. Last night, I tried to install the 9.04 version on my Dell Mini 9. After several failed attempts, I could burn the .img file on a SD card. When I tried to boot up through the SD card, it is completely ignored even though I have changed the boot option. I finally gave up on installing the new OS!

The problem is, while I tried the above, I might have copied the file to a wrong folder, which now made my computer bloated and very slow. 

I have attached a screen shot of my system monitor. Is it safe to delete dev/sda2 and gvfs-fuse-daemon?

Thanks for your help!!!

---

### Post by jespdj on 2009-04-24
> **novice_dell said:**
> I am a new Linux user. Last night, I tried to install the 9.04 version on my Dell Mini 9. After several failed attempts, I could burn the .img file on a SD card. When I tried to boot up through the SD card, it is completely ignored even though I have changed the boot option. I finally gave up on installing the new OS!
As far as I know, the Mini 9 cannot boot from the built-in SD card reader. It's strange, but this just doesn't seem to be possible on the Mini 9. Put the img on an USB stick (of at least 1 GB) instead. Plug in the USB stick, power on your Mini 9 and press 0 to get into the boot menu (I have to press 0 twice, it looks like my Mini 9 doesn't register the first keypress). Select to boot from the USB stick.

[Instructions for putting the img on an USB stick](https://help.ubuntu.com/community/Installation/FromImgFiles)

---

### Post by jespdj on 2009-04-24
> **vickoxy said:**
> So now my short impressions with 9.04 desktop edition:
4) boot up time is not so impressive as delbuntu (yesterday cam new dell´s updates, and i think it is booting now under 20 sec-with 9.04 it is 40-50 sec)
I am using Ubuntu Netbook Remix 9.04 (not a Dell-specific version), formatted my 32 GB SSD to ext4, and it boots up very quickly, in about 20 seconds from GRUB bootmenu to login prompt.

---

### Post by andywhoa on 2009-04-24
I installed 9.04 Netbook Remix on my Mini 9 and everything was great.  Then I rebooted and it's like Gnome won't boot properly...

I get to my desktop and the ONLY thing I see I see is my wallpaper.  No panels, no nothing.  If I right-click, I get a menu and I can start to do stuff.  For example, I select to change my background and the window opens up.  However, there is NO window boarder.  Similarly, I can create a folder on the desktop, double click and open a Nautilus window.  The window has NO window frame.

I don't know what to do :(

---

### Post by andywhoa on 2009-04-24
Any idea about this?

---

### Post by Brandon Williams on 2009-04-25
andywhoa,

The desktop switcher is buggy. Here's what I did.

Log out (press Ctrl+Alt+Backspace if necessary) to get back to the gdm login screen. When you get there, press Ctrl+Alt+F1 to get to a console login prompt. Log in and 'rm -rf .gconf*'. Exit and press Ctrl+Alt+F6 to get back to the gdm login screen.

After all of this, when I logged in, the UNR desktop worked correctly.

---

### Post by jaqrah on 2009-04-25
> **andywhoa said:**
> I installed 9.04 Netbook Remix on my Mini 9 and everything was great.  Then I rebooted and it's like Gnome won't boot properly...

I get to my desktop and the ONLY thing I see I see is my wallpaper.  No panels, no nothing.  If I right-click, I get a menu and I can start to do stuff.  For example, I select to change my background and the window opens up.  However, there is NO window boarder.  Similarly, I can create a folder on the desktop, double click and open a Nautilus window.  The window has NO window frame.

I don't know what to do :(

Pretty much the same exact experience.  I set up the 9.04 i386 standard version in vbox.  Downloaded all of the updates.  I set up Guest Additions for Linux. Went to synaptic and enabled the Netbook Remix package.  Restarted.  Get to my desktop and all I see is wallpaper.  No panels, no anything.  Right clicking doesn't do anything.  Although, hitting Ctrl+F (toggle between window and full screen vbox) temporarily allows me to view a partial desktop for about 10 seconds.  I was able to work my way to removing the netbook remix package.  Something is buggy with one of the apps in the package.

---

### Post by vickoxy on 2009-04-25
Yes, and after newest update there are some new icons available (look the panel-Bluetooth, WiFi, Sound, Go Home...)

Did anyone notiche this changes (in layout and synaptic) after dellbuntu 8.04 updates?

---

### Post by Ryback on 2009-04-25
Nice!  I am using my own custom icons for Dellbuntu 8.04 so didn't notice these.  Based on the mixed reports in this thread, I don't think I'll be upgrading to regular 9.04 any time soon...right now everything (apart from the fact the brightness won't remain at the previous level after reboot) works for me so it's not worth the risk.

EDIT: Oh and maybe a bit off topic, but in those updates that dell pushed out did anyone notice the new wireless driver?  It's good to see that being maintained.

---

### Post by vickoxy on 2009-04-25
> **Ryback said:**
> Nice!  I am using my own custom icons for Dellbuntu 8.04 so didn't notice these.  Based on the mixed reports in this thread, I don't think I'll be upgrading to regular 9.04 any time soon...right now everything (apart from the fact the brightness won't remain at the previous level after reboot) works for me so it's not worth the risk.

EDIT: Oh and maybe a bit off topic, but in those updates that dell pushed out did anyone notice the new wireless driver?  It's good to see that being maintained.

You mean Network-Manager-Applet 0.7.0. A previous Manager did a good job too (maybe is now little bit faster...).

---

### Post by Ryback on 2009-04-25
Thanks for the correction...yes I didn't check to see if it was actually the driver, I just saw the new interface.  Silly me :)

Definitely faster connecting with this, I noticed (sorry to go all technical on you) as soon as I get the first green light, the second is almost immediate.  Maybe it's just me but it also seems a little snappier to detect networks after bootup/resume from suspend.

---

### Post by vickoxy on 2009-04-25
> **Ryback said:**
> Thanks for the correction...yes I didn't check to see if it was actually the driver, I just saw the new interface.  Silly me :)

Definitely faster connecting with this, I noticed (sorry to go all technical on you) as soon as I get the first green light, the second is almost immediate.  Maybe it's just me but it also seems a little snappier to detect networks after bootup/resume from suspend.

I noticed the same things. Well, happy to see that dell ubuntu goes even better with new updates-for newbie like me that means a lot...

---

### Post by dean.barnett on 2009-04-25
I installed Jaunty yesterday and suddenly can't get into either my Gmail or xmarks accounts. Passwords aren't recognized. I can get into my secondary Gmail account, but it's in Japanese! Any ideas? I don't want to go back to 8.04.

---

### Post by vickoxy on 2009-04-25
Did  anyone notice that after last update of Dell Ubuntu 8.04 Compiz is included in OS?

---

### Post by Ryback on 2009-04-26
When I did a search in synaptic I saw that compiz was installed...although I never checked if it was there before I processed the recent update.  In any case I think you need to install compizconfig-settings-manager if you actually want to configure it through the GUI, right?  At the moment I don't have an option under my System -> Preferences (or -> Appearance) to configure any compiz effects, and my system is still using metacity.

---

### Post by vickoxy on 2009-04-26
> **Ryback said:**
> When I did a search in synaptic I saw that compiz was installed...although I never checked if it was there before I processed the recent update.  In any case I think you need to install compizconfig-settings-manager if you actually want to configure it through the GUI, right?  At the moment I don't have an option under my System -> Preferences (or -> Appearance) to configure any compiz effects, and my system is still using metacity.

Yes, you are right-need only to install compizconfig-settings-manager, but the performance is not very good (better with full non lpia version).

---

### Post by Ryback on 2009-04-26
Until I'm somewhere that I can get my hands on a cheap 2GB stick of ram, I don't think I'll be using compiz on the mini9 anyway.  Firefox has it's chuggy moments as is.  It would definitely boost the "sexy" factor when I show it off to people though! Desktops on a rotating cube are the greatest.

---

### Post by fiendishlyclever on 2009-04-26
I couldn't get on with the netbook remix so I ran the x86 version - the main improvement for me was that my internal 3G modem now works properly with Network manager.

I'm still missing one or two apps from Windows but am sticking with Ubuntu for the time being.

---

### Post by Merk42 on 2009-04-26
> **fiendishlyclever said:**
> I couldn't get on with the netbook remix so I ran the x86 version - the main improvement for me was that my internal 3G modem now works properly with Network manager.

I'm still missing one or two apps from Windows but am sticking with Ubuntu for the time being.

Which are what exactly?

---

### Post by jer85008 on 2009-04-26
I've tried to make a USB install for UNR with no luck. I have a Mini 10 coming tomorrow and really want to install it. Every time I make the USB I get a non-system disk error when loading (I have a Mini 9 that I am trying it on now). Tried Unetbootin. How did you make your USB?

---

### Post by snowpine on 2009-04-26
> **jer85008 said:**
> I've tried to make a USB install for UNR with no luck. I have a Mini 10 coming tomorrow and really want to install it. Every time I make the USB I get a non-system disk error when loading (I have a Mini 9 that I am trying it on now). Tried Unetbootin. How did you make your USB?

Unetbootin is for .iso files; NBR is distributed as an .img: [https://help.ubuntu.com/community/Installation/FromImgFiles](https://help.ubuntu.com/community/Installation/FromImgFiles)

---

### Post by anjilslaire on 2009-04-27
You can also download the Ubuntu ImageWriter and instructions from here:
[https://wiki.ubuntu.com/UNR#Writing%20the%20Image](https://wiki.ubuntu.com/UNR#Writing%20the%20Image)

---

### Post by vickoxy on 2009-07-10
Did anyone install lately the Ubuntu 9.04 on dell mini 9, and can anyone confirm me that all is working out of the box (repositories, language setup-i use german, auto updates...), or i have to tweak a lot to make it work fine...

And i want to install desktop edition...

---

### Post by The Jinx on 2009-07-10
the only thing i had to do was add a line into the /etc/modprobe.d/alsa-base.conf to get my audio up and running [this is only because i have the Vostro a90] other than that everything seemed to work out of the box for me.

---

### Post by vickoxy on 2009-07-10
HEEEELP!!!

I have same error as in april: now at 66% of installation it stops reporting input/output error-Live 9.04 works just fine. I downloaded .iso and made with unetbootin in Windows Live USB Stick, but installation went bad-what should i do?

---

### Post by vickoxy on 2009-07-10
Should i use FAT or FAT32 to format USB Stick? What if i do with unebootin daily live....? Oh not again-i should stick with dellbuntu-but live 9.04 works so well....!!!

---

### Post by vickoxy on 2009-07-10
So, here is the error-please help!!!

---

### Post by vickoxy on 2009-07-10
Same error on 66% with another stick formated in FAT32...

Anyone knows something? Live Version works perfect...

---

### Post by Mathieup75 on 2009-07-12
I tested the Notebook remix edition (9.04) and it works great.  I actually like the notebook layout.

Only problem I am trying to resolve is the integrated microphone that is not working.

Did not have a chance to test SD card reader yet, heard it may be problematic.

I will now try the standard 9.04 edition of Ubuntu and see.

---

### Post by vickoxy on 2009-07-16
Finally i made one good installation of Ubuntu 9.04 Desktop edition (the problem was in Unetbootin-needed new version). I am testing it now, but i think that i am not going back to dell´s Ubuntu 8.04. So, little report:

PROS:

- definitely faster in all applications. Specially noticable if you are upgrading to 2GB RAM.
- Adobe Reader and OpenOffice 3.0 (which i use a lot)-working much, much faster-no problems with PDF Books...
- Network Manager connects faster
- Stabil-almost everything working aout of the box

CONS (for Newbies as me, for other no big issue):

- need manually to install Flash, Java, Acroread, Skype, VLC, Cairo-Dock-but there is plenty of forums and users that are helping with any problems.
- specially annoying were to me these Ubuntu Keyrings/Password-but it needs just a simple tweaking in gconf-editor
- Synaptic doesn´t work always so well-so needed to install programms from Terminal (if you added medibuntu in repos, you can install programms only from Terminal). I repair it with xapian-index line in terminal-after index rebuilded all programms were correctly listed.
-Bluetooth was definitely better under Hardy (specialy if you are using Apple Wireless Keyboard)

But, all these cons are problems for newbies as me. As i am eager to learn more about linux/and like it/ i didn´t cease to work on it-and it is woth it.

Although i have MacBook, i use Dell mini as desktop computer-connected with external Display and Bluetooth Keyboard. With 2GB Ram, Office, Firefox and Acroread are doing extraordinary good job for me.

So. i will reccomend anyone to go to 9.04 on dell mini.

---

### Post by KegHead on 2009-07-16
Hi!

I'm using 9.04 with my mini 9.

2gb ram, 4gb hd with no problems.

KegHead

---

### Post by Student Driver on 2009-07-16
I have a Dell Mini 9 with Bluetooth, camera, wifi, and 64GB SSD.  It works fine now, but I went to Blueman for bluetooth functionality and use the normal desktop (rather than UNR) only because of conky.  Otherwise, I would keep using the cool netbook interface.

---

### Post by anjilslaire on 2009-07-17
> **vickoxy said:**
> - Synaptic doesn´t work always so well-so needed to install programms from Terminal (if you added medibuntu in repos, you can install programms only from Terminal). I repair it with xapian-index line in terminal-after index rebuilded all programms were correctly listed.

What? Medibuntu has no effect on the ability to install from Synaptic. With the medibuntu repo's included, installing any application can be done just as easily from terminal or GUI.

---

### Post by vickoxy on 2009-07-17
> **anjilslaire said:**
> What? Medibuntu has no effect on the ability to install from Synaptic. With the medibuntu repo's included, installing any application can be done just as easily from terminal or GUI.

I know that, but as said, installing the programm from terminal wasn´t problem-it shows taking it from medibuntu. But after installing it wasn´t shown in Synaptic. Then i made xapian-index and it was shown in synaptic just as it has to be (installed...).

---

### Post by ugm6hr on 2009-07-18
> **snowpine said:**
> I do not use hibernate (no swap) and resume from suspend takes only a couple of seconds.

I have 9.04NBR installed on my 8GB Mini 9.  I am now usinf XFCE4 instead of Gnome/NBR, but I still find suspend doesn't work.

I have no swap. partition.  I always have a 8GB ext3 SD card plugged in (for staorage).

When I use suspend (either from logout screen or by closing lid), I get a backlit black screen with a single flashing cursor top-left.  Nothing appears to resume from this: tried all Fn keys, touchpad etc.  The Power button does not resume either, and holding it down does a hard reset.

What am I missing?

EDIT: Seen this post:
> **paraa said:**
> There are 2 bugs concerning the SD Card Reader.
In some cases the system does not detect the card properly.
Theres a workaround for this. Just add

options sdhci debug_quirks=1

to the /etc/modprobe.d/options file.

The second bug (both are already filed but not fixed yet(9.04rc)) causes the suspend mode to crash when the system was suspended with a mounted SD card.
Some eeePC guys wrote a patch but I don't think that it would work for Mini 9. Anyone got a good idea on this case?

And this:
[https://bugs.launchpad.net/ubuntu/+source/ubuntu-netbook-remix-default-settings/+bug/330671](https://bugs.launchpad.net/ubuntu/+source/ubuntu-netbook-remix-default-settings/+bug/330671)

Any progress on this?  I never used Suspend on my laptop, but find the idea apealing for a NetBook.

---

### Post by nodius on 2009-08-27
First of all, I am a newbie.
I installed 9.04 remix a week ago on my Dell Mini 9 but I had problems with sound. Playing mp3s, watching movies (AVI) or viewing youtube videos all had the same problem: Every few seconds the sound would skip a fraction of a second. Quite annoying.
I couldn't find a solution so I installed 9.04 desktop version just to see.
Same thing.
Otherwise everything else is working just great, which is a shame for sound.
I tried to return to 8.04 using the dvd that came with my mini 9, but the create usb startup application on that dvd gives me an error message. I'm stumped.
anybody else has that specific sound problem?

---

### Post by vickoxy on 2009-08-27
> **ugm6hr said:**
> I have 9.04NBR installed on my 8GB Mini 9.  I am now usinf XFCE4 instead of Gnome/NBR, but I still find suspend doesn't work.

I have no swap. partition.  I always have a 8GB ext3 SD card plugged in (for staorage).

When I use suspend (either from logout screen or by closing lid), I get a backlit black screen with a single flashing cursor top-left.  Nothing appears to resume from this: tried all Fn keys, touchpad etc.  The Power button does not resume either, and holding it down does a hard reset.

What am I missing?

EDIT: Seen this post:


And this:
[https://bugs.launchpad.net/ubuntu/+source/ubuntu-netbook-remix-default-settings/+bug/330671](https://bugs.launchpad.net/ubuntu/+source/ubuntu-netbook-remix-default-settings/+bug/330671)

Any progress on this?  I never used Suspend on my laptop, but find the idea apealing for a NetBook.

Sorry-didn´t see your question. Well, i think that i found somewhere that these problem have always those who have no swap partition- i do not even know what that is, but it just occurs to me that i read always-"have no swap, suspend does not work". I reinstalled ubuntu 8.04/9.04, linux mint version many times-and had never issues with suspend/hibernation-but i always left swap partition (default) intact...

Why i installed ubuntu many times, maybe you ask yourself? Just found many other ways to crash the system....but suspen always worked very nice (had though some problem with dell´s  ubuntu and network manager...)

---

### Post by ugm6hr on 2009-08-28
> **vickoxy said:**
>  never issues with suspend/hibernation-but i always left swap partition (default) intact...

Swap partition is not recommended if you have an SD hard drive (as in Mini 9) due to the potential for frequent writes shortening the SD lifespan.

---

### Post by vickoxy on 2009-08-28
> **ugm6hr said:**
> Swap partition is not recommended if you have an SD hard drive (as in Mini 9) due to the potential for frequent writes shortening the SD lifespan.

You have system installed on SD Card (or you mean SSD drive)? Or it means that is also not recomended if you use external sd card just as storage?

I don´t know-hibernation/suspend is to me very important to have with one netbook, so i would always prefer it to working fine...

---

### Post by ugm6hr on 2009-08-28
> **vickoxy said:**
> You have system installed on SD Card (or you mean SSD drive)? Or it means that is also not recomended if you use external sd card just as storage?

SSD has a limited lifespan in terms of number of writes.  Hence, there is a theoretical disadvantage with using swap, which can cause multiple writes and re-writes on the SSD.

---

