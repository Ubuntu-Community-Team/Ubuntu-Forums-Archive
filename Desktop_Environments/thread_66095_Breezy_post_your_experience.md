---
title: "Breezy: post your experience"
date: 2005-09-16
forum: Desktop Environments
---

### Post by f1dave on 2005-09-16
Hi,

I would like to hear from people about Breezy, as I am considering an upgrade. Basically I would like to keep this thread speculation-free, so please only people with the latest breezy preview running post your opinion. I don't need to be warned about upgrading- I just want the facts from the people who know.

---

### Post by manicka on 2005-09-16
I upgraded and stuffed my system by answering one of the questions incorrectly. Others have had more success.

---

### Post by heimo on 2005-09-16
If you have free space, consider dual booting Hoary and Breezy. :) I've had only minor problems with Breezy lately, earlier X was broken every other day, but there were often workarounds. Currently most of the stuff is working correctly (I have latest updates), some video players tend to crash occassionally. For me, USB devices are working better than with some version of Linux in Hoary. I still can't use grub for some reason (I'm not willing to spend too much time diagnosing this), so I'm using lilo.

Overall, Breezy is perfectly usable for my every day main desktop. When I earlier did upgrade (now I have fresh install from one of the older snapshot CDs) I had some small problems with X configuration. Nothing major. I really like Breezy, and be it placebo effect or not, Gnome 2.12 feels better.

Offtopic: Firefox 1.5 won't ship with Breezy, but I tried beta and it feels very, very nice and will be my main browser as soon as it stabilises. (I'm anxious.)

---

### Post by Hobbsee on 2005-09-16
I'm using breezy now....it's interesting.  Not sure if it's worth upgrading yet, or whether to wait for the actual release...

Everything seems to be working fine, except I have no sound.  A lot of the stuff from the ubuntu guide works, but some of it isnt in the repositories.  Openoffice.org is way faster (this is the 2.0 release candidate/beta/whatever it is now) than both the 2.0 beta in the repositories and the 1.3 (I think) stable version.

Kubuntu installed kde 3.4.2 as default, and there's a different KDM screen - it's very pretty, I wish we could customise it via System Settings.  As for system settings...I preferred the old kcontrol, which you could select anything from the side menu.  In System Settings, you have to hit back to do that, which only works part of the time.

If you are going to switch to breezy, be prepared for a lot of updates - I mean, a lot of updates...

I'm sure that the differences between breezy and hoary would be far more obvious using gnome, as there's gnome 2.12 as default.  

I'll further reply as I explore it more...

---

### Post by blakken on 2005-09-16
I just tried the live version of breezy and i can't say it satisfied me:first of all sound bug with alsa and second of all it simply didn't mount properly my external hard drive while in fact my hoary does both without any matter!
I lately tested and installed  the new kernel included in breezy ...can't say there is such change for my centrino ...I had to install cpudyn in order to make silent my computer! :???:

---

### Post by ticklu2deth on 2005-09-16
[QUOTE=Hobbsee]I'm using breezy now....it's interesting.  Not sure if it's worth upgrading yet, or whether to wait for the actual release...

[COLOR=DarkRed]Everything seems to be working fine, except I have no sound.[/COLOR]  A lot of the stuff from the ubuntu guide works, but some of it isnt in the repositories.  Openoffice.org is way faster (this is the 2.0 release candidate/beta/whatever it is now) than both the 2.0 beta in the repositories and the 1.3 (I think) stable version.

Kubuntu installed kde 3.4.2 as default, and there's a different KDM screen - it's very pretty, I wish we could customise it via System Settings.  As for system settings...I preferred the old kcontrol, which you could select anything from the side menu.  In System Settings, you have to hit back to do that, which only works part of the time.

If you are going to switch to breezy, be prepared for a lot of updates - I mean, a lot of updates...

I'm sure that the differences between breezy and hoary would be far more obvious using gnome, as there's gnome 2.12 as default.  

I'll further reply as I explore it more...[/QUOTE]

I don't know if this will apply in your situation, but I found that the sound was simply muted and was easily fixed in Kmix.
Hope this helps.

---

### Post by greyhound4334 on 2005-09-16
So far so good for me with breezy.  Going on my second week with it.  I run mostly firefox, amarok, jedit, apache2, php5, mysql, konsole, kate, thunderbird, plus a few wine apps.  Occassionally get a weird hiccup with one of them (probably amarok the worst, then firefox), but rarely anything that a restart of the app doesn't cure.  Haven't lost any work.  Overall, I'd say it's crisp and pretty solid.  Don't know what the sound problems others are having is.  Aside from amarok freezing up sometimes (which *could* be an ALSA problem I suppose), sound is fine on my box.

---

### Post by GeekWar on 2005-09-16
Upgraded from Hoary to Breezy last night. During the download I created backup tar files of my home directory and my entire system as well as scripts to automatically restore my system in case I killed it I'd get all of my work back in 20 minutes or less. I will admit I'm glad I didn't have to use them because even though it showed no errors doing the backups I still wasn't entirely sure it would work.  ;-) 

I followed the steps I'd found here:
[http://ubuntuforums.org/showthread.php?t=60118](http://ubuntuforums.org/showthread.php?t=60118) 
After my original attempt failed miserably (Hence the system backup this time)

Originally I couldn't get x to start but I'd seen that problem all over so I instantly vim'd my xorg.conf file with no success. Well... I tried at least. So I copied my current xorg file to a backup and then proceeded to reconfigure xorg. sudo'd an init 1 & 2 loaded right into my desktop. Copied the driver and module information for my ATI card back into my xorg file; rebooted and here I am. I've got full hardware accelleration; been jamming away with Beep-Media-Player; and using all of my regular apps without any issue.  

To be honest I actually had to go to the About Gnome app just to verify to myself I'd made any upgrade at all.  :roll:

---

### Post by ewangr on 2005-09-16
So far Breezy has been working just fine for me except for the CPU getting pegged near 100% anytime I connect to it using remote desktop.

It correctly sees my external Firewire and USB-2 drives (Hoary didn't seem to like the FW drives), it properly picked up my video setup, and it automatically configured my Realtek HD sound (every other distribution has required me to at least modprobe the sucker). Of course I did have to go to Kmix to unmute...

Only other thing was some fun with my wireless card. It got the right driver, but doesn't seem to realize during installation that you might use other channels. Once the system was up and I could iwconfig ath0 it, I was able to fix that pretty quickly.

FWIW,
Ewan

---

### Post by mlomker on 2005-09-16
I tried upgrading about a week ago and went back.  I couldn't get VMWare to install, there were some odd performance issues (inexplicable slow-downs), and various administrative applets would not work.  My timezone was set to UTC and I couldn't change it, for example.  They are moving a lot of stuff around in Kcontrol.

Keep in mind that I'm amd64.  It's quite possible that 32-bit has fewer issues right now.

---

### Post by Manny C on 2005-09-16
Yep..Breezy works fine for except for the following issues:
[list]
[*]Not autodetecting any USB mouse that is hotplugged.
[*]Not autoconnecting to my wireless network on boot up
[*]The official repos are usually slow (20 something kb d/l) and the local mirrors are burping too much to be of any use.
[/list] 

Running Kubuntu on Compaq Presario 2267ap laptop. Suspend works fine using KLaptop - needed to tweak the acpi-support script though. 

Only other comment is that the KDE icons in the toolbar for OO2b are too big. I don't know how to make them smaller.

Screenshot included.

---

### Post by XDevHald on 2005-09-16
Same here, but...

Wireless does not work (not sure why)
Network connection dies for no reason. (This gets VERY annoying)
Update Manager does not continue with 1 of 46 mirrors (Does this on occassions when it's feeling lonely :p)
Firefox is slow as a slug if not worse (Could be security issues from a stand point of 1.0.5)

Yep that's it for now, I'll keep mine updated as others view this.

**EDIT: **Didn't look at the forum and notice the KDE, sorry mine is gnome :p

---

### Post by f1dave on 2005-09-16
Oh no, you've killed it all! How dare you! :D

Seriously though, thanks to all the folks posting so far. Right now UWA's dished out a crapload of projects, so I don't think I'll be upgrading just yet ;) But I certainly look forward to hearing more people's experiences with kubuntu breezy in this thread.

---

### Post by DarkT on 2005-09-17
My overall experience of breezy/kubuntu has been good, I had sound problems but  I've fixed them, dist-upgrading killed my system but a clean install from the preview CD worked fine and I've found the system to be almost fully stable. 
 
One of my only niggles with it at the moment is pointless package dependencies, such as kubntu-desktop being dependant on the HP printing packages which is pointless unless you own a HP printer (thankfully we have BUM to turn the services off). There's also the small problem of ubuntu-update not checking (or knowing) when a package list has been updated, I have to manually reload packge lists to get any updates (this happened occasionally in hoary) and yes, I know, "use apt-get", but sometimes ubuntu update manager is more convenient because it's easy to select which ones you want updated and which ones you don't.

Anyway, otherwise I've found it to be a bit faster but that might just be psycologial because it's new ;)

________

[QUOTE=Hobbsee]I'm using breezy now....it's interesting.  Not sure if it's worth upgrading yet, or whether to wait for the actual release...

Everything seems to be working fine, except I have no sound.[/QUOTE]
I had similar problem but managed to figure out a fix, check the end of the first page from [this](http://ubuntuforums.org/showthread.php?t=63993) thread (alsactl store seems to works for me now which it wasn't when I posted that), if you have an Audigy card that should fix it otherwise check whether it's muted as some else said & check the bugzilla reports I linked to in the first post of that thread.

---

### Post by Hobbsee on 2005-09-17
[QUOTE=DarkT]
I had similar problem but managed to figure out a fix, check the end of the first page from [this](http://ubuntuforums.org/showthread.php?t=63993) thread (alsactl store seems to works for me now which it wasn't when I posted that), if you have an Audigy card that should fix it otherwise check whether it's muted as some else said & check the bugzilla reports I linked to in the first post of that thread.[/QUOTE]
 all the mirrors are exceptionally slow - I think it would be way faster to download a CD and install it that way - and you get to check out the nifty installer, which wouldnt be all bad...

I didnt really play around with the sound much - I pretty much upgraded because i'd hosed my hoary system, and so thought i'd check out breezy to see what it was like, and then possibly go back to hoary again, which I did.

It looks nice though - I like the usplash!

---

### Post by MadPriest on 2005-09-17
Tried to upgrade 5.04 yesterday. 
The X did not want to start. As usually (seems like i don't learn on my own mistakes), i didn't make any backups.
So, using other computer i donloaded the preview disk and make a fresh install.
Everything works fine, except some apps still missing (like gstreamer and PocketPC syncronisation software, for example).
Wireless, sound, video - all works fine.
I have IBM t40 laptop.

---

### Post by schrombot on 2005-09-17
So far I have had a pretty good experience. I have had a couple of minor set backs, but it is no big deal as this isn't a final. Whenever I log out my x server freezes and I have to reboot and if I try to set a static ip for my network, it completely drops my connection. I can access anything in my network, but the internet is a lost cause. It son't let me switch back to dhcp either. I am gonna play with it some more and hopefully I will figure it out. If anybody has any advice, that would be great since I have only been using linux for about 2 weeks now.

---

### Post by rosslaird on 2005-09-17
Breezy has been working perfectly for me after a dist-upgrade last week. I only had one hiccup (I had to use a static ip for one of the machines on my network rather than dhcp), but that got fixed quickly and since then everything has been fine. Actually, Breezy seems to have fixed various small issues and is just as stable as Hoary on my system.

On the other hand, a dist-upgrade of this magnitude is serious business, and various things could go wrong, so I can see why people might be cautious, especially if they are not familiar with the intricacies of apt (or synaptic). The worst thing for most people would be to lose their net connection, or their X server, or both (because then you can't get online to ask questions and get help), and that seems to be happening to various people. I have 2 machines, so if one goes down I can switch to the other for help, but not everyone has this option, and a crash during the upgrade could seriously sink a system. So I agree with the idea of working from a CD, or using a separate partition, or whatever.

Ross

---

### Post by Freddy on 2005-09-17
For me it has been as stable as Hoary, don't really know what I think of this new Control Center (System settings) yet, I believe that the Gnome guys will like it though, cause it feel not that bloated. Had some problem with my first updates of the system through Kynaptic and had to reinstall and use the konsole instead but after that Breezy has just meen a breez :) 

(K)ubuntu has finally won me over and it's gonna be the only Linux dist for me, so from now on it's just Kubuntu and freeBSD running on my comp's. /// Freddan

---

### Post by belred on 2005-09-17
i'm currently using hoary with vmware with no problems.  i just tried breezy live cd and it worked for me but the install version didn't even install.  i posted this to the breezy top level group with the error messages,  but i didn't get a response that this would be fixed.    so i'm crossing my fingers that the next beta release will work.

bryan

---

### Post by Freddy on 2005-09-18
I have been on Breezy Badger for a little more time now and I'll have to say that the ControlCenter replacment sucks, at least when you are using the new Baghira style, no biggi though you can access the old kcontrol if you really like to.

After my first installment I tried to use Kynaptic to upgrade the hole system and it went bad and many upgrades broke, I reinstalled it and used the console instead and it went real smooth, I've tried to upgrade with kynaptic with a smaller amount of upgrades but still it seems that the program has some problem with that, haven't tried Synaptic though.   /// Freddan

---

### Post by gaz514 on 2005-09-19
It seems fine so far, except my hard disks won't show up on the desktop, that's the only problem I've had so far... oh yeah, and Sun java doesn't seem to be in any repositories (at least for AMD64)

---

### Post by e^e on 2005-09-19
Breezy has been working fine for me since i updated. everything works, though i don't have a wireless card, so don't know about that. What i did notice though is that more repos has been added, and when searching for something in synapatic, it takes a bit longer to show the results.

 Something i stumbled upon when i updated and restarted the pc, was that Xorg didn't configure automatically, and so it when into console just after booting. So i had to configure it manually with dpkg.

thnx and keep up the good work.

---

### Post by Freddy on 2005-09-19
[QUOTE=gaz514]It seems fine so far, except my hard disks won't show up on the desktop, that's the only problem I've had so far... oh yeah, and Sun java doesn't seem to be in any repositories (at least for AMD64)[/QUOTE]
This is for all realeses. Sun java and w32codecs should be in the backports but they are not converted to Breezy yet and it's not a real great idea to enable the Hoary backports for Breezy. If you really need it, just use it for those packages and keep track of it if anything breaks after you enable the Breezy backports when they arrive. /// freddan

---

### Post by ezphilosophy on 2005-10-17
Overall, everything has been pretty good.  Just one fairly big problem:

Everytime I log out, the computer screen goes blank, and apparently, freezes.  I have to manually shut the computer off.  This problem is in KDE and Gnome.  I noticed someone else also posted a similiar problem above.

---

### Post by garnertr on 2005-10-17
I had zero problems, followed the wiki instructions for both my laptop and my desktop and everything is golden...

---

### Post by Pablo_Escobar on 2005-10-17
Some graphic cards problems for me (You've got to love ATI drivers), I managed to do it.
Overall everything is veeery good for me.
Sometimes just nautilus bumps out, but that's not biggy :)

---

### Post by ryke on 2005-10-17
hi... in my opinion, Breezy has a lot of minor, but nasty problems... in fact, I have 2 computers and in the 2nd one I still have Hoary, that works perfectly.

probably (and I hope so :-) ), within a few days, problems will be fixed, and then will be the time to install Breezy.

I think that this version has been released without enough time to check it properly (in fact, there are people claiming for a 5.10.1... think in a person who installs for 1st time kubuntu and find a lot of problems)

regards

---

### Post by OldGaf on 2005-10-18
I upgraded to Breezy and everything seems fine. I will do a clean install in a week or so.

---

### Post by Valeran on 2005-10-19
I did a clean install about 3 days before the actual release.  I have had only one problem.  Amarok seems to keep crashing on me.  However, I understand that this is not just an Ubuntu problem.  Besides, RythmBox works just fine.  Other than that, it has been a flawless experience.

---

### Post by manicka on 2005-10-19
I clean installed about 6 weeks ago and haven't looked back. I've found breezy very stable from just after the final relase fo gnome 2.12. 

KDE/Kubuntu however, is another story. I recently installed it as I like to have it running to help with support requests. Everything felt  a bit buggy  and sluggish to me and not as slick as 3.4.2 in hoary. At this stage I have removed most of it and just have the libraries I need for some favourite apps like amaroK, k3b and klipper.

---

