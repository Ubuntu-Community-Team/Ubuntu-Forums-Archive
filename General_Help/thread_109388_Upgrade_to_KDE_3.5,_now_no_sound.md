---
title: "Upgrade to KDE 3.5, now no sound?"
date: 2005-12-28
forum: General Help
---

### Post by BeachBum on 2005-12-28
Hello everyone!

Last night I installed kubuntu and then installed the latest KDE 3.5 packages through synaptic using the directions on the kubuntu website.  Everything seems to work, however when I play sound, I don't hear anything.  Using Amarok, the song looks like its playing (song title flashes, spectrum analyzer um...analyzes) but I get no errors, even running the program from a terminal.  Same goes for Noatun, looks like its playing, but I hear nothing and no errors.  

I checked, the sound system is enabled, hardware set to autodetect, main and PCM are turned all the way up.  I just have no clue whats going on!  I had KDE 3.4.2 installed and everything worked fine, all I did was install kubuntu and the KDE 3.5 packages :confused: .

Also, I'm using an IBM Thinkpad T42, with the intel ICH series chipset. 

Thanks for any help! :D

---

### Post by 40%TUX on 2005-12-28
once i upgrade to kde 3.5 too....but got also some weird stuff going on my compaq laptop. tried many things to bring system as it was before upgrade but all in wain. at last ( i don't have that much time and devotion, i'm too old for it) when i got tired - clean install Kubuntu 5.10. i will wait till next release of kubuntu. i don want to sound to gloomy, maybe you will have better luck.

---

### Post by ameerirshad on 2005-12-28
Add me too, though I have heared of this problem before, I never saw an ending and thorough solution! I mean, I like to play my music an watch part(s) of movies or have a Skype conversation AND be informed with sound when Thunderbird receives email (and with sound I mean anything BUT the system beep!)........... This works under GNOME But not under KDE, at least, not with me..... and any system not making things working out-of-the-box is limiting my Linux experience!

so do we have to traverse back to Gnome?

---

### Post by pelle.k on 2005-12-28
First of, you seem to have had **diffrent** experiences, and neither of you have told us what soundcard you have.

You might see it in menu->system->info center (kinfocenter) or by typing  lspci in a terminal prompt.

If it's an Audigy then the problem *might* be you have to turn off analog/digital jack out.

If it's another card, it *might* be muted in alsa by default. check that by opening volume control (system tray) and clicking "mixer", or by running alsamixer in a terminal prompt.

I will do an upgrade of kubuntu to kde 3.5 tonight, so i will let you know what might be the problem, if the former suggestions didn't help you. REPORT BACK and let us now, even if you fix it. It is of great use to other in you position. :)

---

### Post by ameerirshad on 2005-12-29
[quote=pelle.k]I will do an upgrade of kubuntu to kde 3.5 tonight, so i will let you know what might be the problem, if the former suggestions didn't help you. REPORT BACK and let us now, even if you fix it. It is of great use to other in you position. :)[/quote]

I have a VIA Technologies, Inc. VT8233/A/8235/8 237 AC97 Audio Controller (rev 50)

I don't see any of my sound mixer settings being muted

I acknowledged my problem was slightly different, but I guessed the people with knowledge will have a day task if we all post new messages here, I like to keep communication compact ;)

I'm curious about your findings on KDE! I wonder though, isn't it a known problem which KDE developers should (ideal) solved by now? I haven't got these problems under Gnome or the Legacy OS, where sound is just good.:(

---

### Post by pelle.k on 2005-12-29
So some of you did a clean Kubuntu install, and some of you installed kubuntu-desktop from Ubuntu, and then installed kde 3.5. gaaaaah! :) With a mixed bag of different sound cards this couldn't be more confusing LOL. But here it goes anyway...

I'm thinking kde tries to use arts or oss as default in System settings -> Sound and multimedia (hardware).
arts ins't that good, and oss is no good at all, because it lets noone or no other program access the sound card. If system use oss, then all other programs outputs to /dev/null which is "nothing" because they can't get acces to it. maybe thats why you say you see the bars and all of that.

I would say use ALSA (Advanced Linux Sound Architecture, and remeber to press apply so the sound server get's restarted) as default audio device, and if that doesn't work your card is probably not supported by alsa drivers. (I guess your best bet then would be to use esd, which isn't good, but still better than oss/arts)
Try to configure every program you use for ALSA. If you can't find it in outputs, in say VLC, thats because there's a plugin for this purpose (vlc-plugin-alsa).

You do know you can "test sound" on the general tab.

Did you try out alsamixer by the way? Were you card listed there and all **relevant** outputs maxxed?

---

### Post by BeachBum on 2005-12-29
Thanks for your help,

Here is my exact situation: Thinkpad T42 with intel ICH4 audio controller
1. Installed Kubuntu-desktop
2. Added Kubuntu KDE 3.5 Repo
3. Updated + upgraded
-During the process, I was watching streaming video from cnn, and I recieved some error with regards to audio, then to video, then konqueror crashed.  
4. Reboot - video from the site works, no audio


The ICH4 fix proposed a few threads up didn't do anything.

I uninstalled the alsa package (which also uninstalled ubuntu-minimal) and then reinstalled both.  No change.

All volumes are turned up.

Kcontrol set to "autodetect" sound hardware, but I will try setting it to ALSA when I get home tonight.

---

### Post by mlomker on 2005-12-29
I tried upgrading during the 3.5 beta and lost my sound, but the final release installed okay for me.  They made a lot of changes in the media manager for 3.5 and it's probably conflicting with something in Gnome that was installed first.  

You'd probably have better luck if you were upgrading from a clean Kubuntu installation, I'd imagine.  As pelle mentioned, it's impossible for them to test every possible upgrade method...and by the time they get most of the bugs out the next version is released.  Such is the fun of 6 month release cycles.

In (K)ubuntu's defense, that's why they don't backport 3.5 into Breezy...they need the time to work through most of these bugs.

It would have been a *great* idea to back up your machine prior to upgrading to 3.5 ... it's something that I strongly recommend to everyone.  Partimage on  a Knoppix disc is a great tool if you have enough disk space on a different partition (so that you can back up your root partition to it).

---

### Post by hoodwink on 2005-12-29
FWIW, I upgraded to 3.5 on a Kubuntu 5.10 system. No problem with sound, but a few "weird" things.

1. The sound speaker image on the panel did not appear.
2. After I hunted down kmixer and modified the settings. the speaker appeared.
3. Mouseovering the speaker showed 49% setting (I had set 100%) in kmixer. Only after moving the settings using the speaker icon was the correct setting reported.

P.S. Don't try this at home. Unless you have a crappy onboard sound card like mine, 100% will blow you into the next room.

---

### Post by BeachBum on 2005-12-29
Guess I'll have to reinstall it.  By backup, do you mean /home on a seperate partition?  I learned my lesson a few installs ago and started doing that!  I should have figured this would happen, as upgrading horay to breezy via synaptic resulted in the same sound problem.   oh well, ya live and ya learn, thanks for the help!

---

### Post by veloct on 2005-12-30
System Settings > Sound and Multimedia > enable sound system and in the second tab choose ALSA.  That should do it.

---

### Post by pelle.k on 2005-12-30
> System Settings > Sound and Multimedia > enable sound system and in the second tab choose ALSA. That should do it.
Yeah, I use ALSA 100% and have no problems... yet (i havn't installed skype though. That is going to give me hell i suppose...)

> Guess I'll have to reinstall it. By backup, do you mean /home on a seperate partition? I learned my lesson a few installs ago and started doing that! I should have figured this would happen, as upgrading horay to breezy via synaptic resulted in the same sound problem. oh well, ya live and ya learn, thanks for the help!
Maybe im an oddball, but i like to reinstall. Mostly the format part. i like it Klean. hehe :)

---

### Post by BeachBum on 2005-12-30
There's nothing wrong with a nice Klean slate, gives me something to work on afterwards!  I just dislike the downtime during the install.  

I did start fresh again, installed kubuntu, then made a few customizations, then upgraded to 3.5 and sound still doesn't work.  When I try to play music through amarok or noatun, it looks like something is playing but no sound comes out.  When I try to play any audio from Konqueror, using kaffeine, I get these errors:

can't init audio driver "alsasink' - trying another one...

- I press ok then this pops up

can't init video driver "xvimagesink' - trying another one...

- I press ok then this pops up

no useable video-driver found! (xvimagesink)

-then Konqueror crashes.  These were the errors that I got during the update to 3.5 the first time.  I'm going to guess that its 3.5 related, though I'd hate to give up the new eye candy...oh well.  I'll just have to grab the taskbar v2 applet from kde-look.

---

### Post by newuser111 on 2006-01-05
if you have a lot of sound problems, the best thing to do is download and compile the latest ASLA from the alsa website, it comes with alsaconf which ubuntu left out for some reason?

use this guide [https://wiki.ubuntu.com//HdaIntelSoundHowto](https://wiki.ubuntu.com//HdaIntelSoundHowto) but download the needed files mentioned from [http://www.alsa-project.org/](http://www.alsa-project.org/)

---

### Post by BeachBum on 2006-01-05
I'll have to try that.  

Funny thing though.  When I install Ubuntu straight, no KDE, sound works just fine.  When I go to install KDE (3.4.3 I think, the one in the Apt repos), and get it all setup, sound doesn't work.  Its most likely just a configuration that the KDE packages change, but I haven't a clue what it is and where to look.

I understand KDE likes to use Arts, so is there a way to install KDE without Arts?  What configuration files should I look to for changes in sound configuration?  

What really bugs me is that I installed KDE the same way before, install Ubuntu, then KDE, and sound worked before.  For some reason now, even just installing KDE from the standard Apt repos, something is changed.  

Any clues?

---

### Post by taseal on 2006-01-05
I was just gunna make a post asking how to upgrade to 3.5

scratch that Idea lol

---

