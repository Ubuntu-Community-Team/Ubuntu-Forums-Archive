---
title: "New Skype Beta out!"
date: 2006-06-28
forum: Desktop Environments
---

### Post by padre999 on 2006-06-28
Incredible but true. A new Skype 1.3 Beta Version is available for download on [www.skype.com/download/skype/linux/13beta.html](www.skype.com/download/skype/linux/13beta.html) =D>

And it supports Alsa!

So far it runs quite well on my system except for some minor glitches.

Changelog here: [www.skype.com/download/skype/linux/changelog.html](www.skype.com/download/skype/linux/changelog.html)

---

### Post by frodon on 2006-06-28
Alsa support !!!!!!

It would mean the end of many sound issues, great info. I will test it ASAP and see if it solve the sounds problems.

---

### Post by Lfrb on 2006-06-28
Yahoo !! no more need to restart Skype everytime I want to call someone !!

---

### Post by Footissimo on 2006-06-28
Sound is much better for me using ALSA.  I'm chuffed that it works, though it's disappointing that we're looking at a beta and no mention of video chat :(

---

### Post by jdmpike on 2006-06-28
When will it hit the repos?

jdmpike

---

### Post by matjaz_pirnovar on 2006-06-28
Hi,

It DOESN'T work with me.

I still get the "Problem with the sound device" message.

I did use hijacker before and reconfigured alsa (as posted many times here on Ubuntu forum).

Where is the problem?  Please help, I'm getting fed up with not working on NEW release...

Thanks.

M

---

### Post by XVampireX on 2006-06-28
[QUOTE=matjaz_pirnovar]Hi,

It DOESN'T work with me.

I still get the "Problem with the sound device" message.

I did use hijacker before and reconfigured alsa (as posted many times here on Ubuntu forum).

Where is the problem?  Please help, I'm getting fed up with not working on NEW release...

Thanks.

M[/QUOTE]


Hey, You have to go to the settings and in the settings you can choose OSS or ALSA, choose ALSA.

---

### Post by dmizer on 2006-06-28
thank you kindly for pointing this out ... is downloading now.

edit: and that's 100% better.  it lets me choose alsa, and i can make multiple calls in the same session.  the data transfer quality appears to be better too.  my calls are not nearly as distorted as they were before.  i'm also happy i don't have to have that boring drab system tray icon anymore.

me = happy.

---

### Post by mark2741 on 2006-06-28
I downloaded and installed the beta but I can't create a new account (I'm new to Skype). Whenever I try to create the account by entering in the info and then clicking the connect button I'm getting a "Failed to Login" message. Perhaps Skype is down momentarily?

---

### Post by mark2741 on 2006-06-28
[QUOTE=mark2741]I downloaded and installed the beta but I can't create a new account (I'm new to Skype). Whenever I try to create the account by entering in the info and then clicking the connect button I'm getting a "Failed to Login" message. Perhaps Skype is down momentarily?[/QUOTE]

UPDATE: stupid me....turns out the two names I tried using were both already used (you'd think Skype would tell me that though...). But now it won't work - keeps telling me I'm having a sound card issue whenever I try to make a call. ugh

---

### Post by matjaz_pirnovar on 2006-06-29
[QUOTE=XVampireX]Hey, You have to go to the settings and in the settings you can choose OSS or ALSA, choose ALSA.[/QUOTE]


Hi,

I did. My ALSA IS chosen. Everything else seems to be set properley (unless in alsa mixer itself).

As soon a little bit of ringing sound comes out when trying to call - the Problem with the sound device note shows. HOW DISTURBING.

Please any other advices??  Am I forgeting something?

What are experiences of you guys who used to have skype with hijacker before. Is it working clean now?

(HELP!)

Thanks.
Matjaz

---

### Post by matjaz_pirnovar on 2006-06-29
Hi,

My skype IS set to ALSA. And everything else seems to be properly set.

As soon as little ring tone comes out when trying to make a call - Problem with sound device appears. HOW DISTURBING!

Any other advices? Am I forgeting something?

How is skype now working for you guys who used hijacker before?

(HELP!)

Thanks
Matjaz

---

### Post by frodon on 2006-06-29
I took 5 min to test it yesterday and it didn't work for me, i will try to find some workaround later.

---

### Post by ozorba on 2006-06-29
[QUOTE=matjaz_pirnovar]Hi,

I did. My ALSA IS chosen. Everything else seems to be set properley (unless in alsa mixer itself).

As soon a little bit of ringing sound comes out when trying to call - the Problem with the sound device note shows. HOW DISTURBING.

Please any other advices??  Am I forgeting something?

What are experiences of you guys who used to have skype with hijacker before. Is it working clean now?

(HELP!)

Thanks.
Matjaz[/QUOTE]

The same problem here....

Has anyone got a solution?

Skype was working fine with Breezy. I had to do some changes as suggested here when I was running Breezy.

[http://ubuntuforums.org/showthread.php?t=32063](http://ubuntuforums.org/showthread.php?t=32063)

However, I cannot get skype working with Dapper. Neither Skype 1.2 not 1.3 beta are working.

Thanks,
OZ

---

### Post by frodon on 2006-06-29
Same here,

The only way i found to use skype is to close my music player before using it (the killall esd commands are useless in my case).
Add the contact "echo123" to make some tests, it's robot which will answer you and repeat what you say as to test skype.

---

### Post by matjaz_pirnovar on 2006-06-29
A post on skype linux forums  suggested the upgrading 5.10 doesn't really work, it should on clean 6.06 install.
[http://forum.skype.com/viewtopic.php?t=57311](http://forum.skype.com/viewtopic.php?t=57311)

I have echo123 under my skype contacts by default. Gives the sound device problem note.

Shutting down other sound programmes makes no difference.

Will keep trying. Don't want to reinstall complete Dapper again (where would I end up, reinstalling Ubuntu for every minor thing  ;) )

I keep trying...

M

---

### Post by frodon on 2006-06-29
Well, i will try to delete my asound.conf file and remove the part i added in esd.conf thus i would have the same config than a fresh install.
I'll let you know if it works for me.

---

### Post by Antonino Sabetta on 2006-06-29
[QUOTE=frodon]Well, i will try to delete my asound.conf file and removing the part i added in esd.conf thus i would have the same config than a fresh install.
I'll let you know if it works for me.[/QUOTE]

Removing (renaming) ~/.asoundrc did work for me.

---

### Post by matjaz_pirnovar on 2006-06-29
[QUOTE=Antonino Sabetta]Removing (renaming) ~/.asoundrc did work for me.[/QUOTE]

Hi Antonino,

Can you write a pathway/instructions how you renamed it?  (Or remove, sorry for such basic questions :) )

Thanks a lot.  :)

M

---

### Post by ajgreeny on 2006-06-29
Just upgraded to the beta skype and it all works great here.  Minor glitch with it appearing to reset mic levels in kmix but I soon put that right.  It even chose ALSA for sound device automatically.  Great; echo123 works a charm, so I assume calls to my caller list will as well, but no-one else on line at the moment to try it out.

---

### Post by rem on 2006-06-29
The thing is don't even have such folder (or file). Where should I find it? It's not in my home directory...
Forgot to ask: is this a Ubuntu or Kubuntu fix? Or doesn't even matter? Thanks a lot!

---

### Post by frodon on 2006-06-29
People like me who tweaked at the time their config to hear both ALSA and ESD sound to get skype working installed the libesd-alsa0 package and edited the /etc/asound.conf file, i don't know if it is what automatix and easyubuntu do when they install skype.
Just check if you have this file, if you have it make a backup elsewhere, delete it then reboot.

---

### Post by wieman01 on 2006-06-29
Too bad... just tried the new version of Skype and it turned out that it's called a BETA version for a reason... My bluetooth headset would stop the service after 15 to 60 seconds so the other party wouldn't be able to hear me any longer.

Bummer! 

Had been looking forward to the bug-fixes, but I just had to switch back to the previous version which works fine with the headset (OSS).

He

---

### Post by Antonino Sabetta on 2006-06-29
Open the terminal and type the following:
mv ~/.asoundrc ~/.asoundrc.old

"mv" means "rename" (or "move").
Please note that a restart of alsa *may* be needed. The easiest way to do it is rebooting the machine.

---

### Post by Antonino Sabetta on 2006-06-29
The removal of .asoundrc is a potential fix only for those that have fiddled with it in the past to make the old skype work. If you do not have it, it's likely that you problem is something else (or maybe the fiddling was done on the system-wide /etc/asoundrc file).

---

### Post by d3dtn01 on 2006-06-29
I also have been having trouble with skype since upgrading to dapper. I just installed the new 1.3 beta. I had to delete the /etc/asound.conf file to successfully get rid of the "Problem with your sound device" error. However, I still have a problem. When I use echo123, it's not recording my voice. To see what was up with my mic, I tried to record a test with ubuntu's sound recorder. That didn't work. It doesn't appear to be capturing the input. I'm not very familiar with how the mic works. I'm hoping that I just need to change a setting. Here's some info from my alsa mixer settings:

It says at the top: HDA Intel (Alsa mixer)
Under playback tab I have 4 volume controls: master, pcm, capture mux and capture mux. All of these are unmuted.
Under capture tab I have 1 control: capture. This is unmuted.
Under options tab my input source is mic. 

Do I have something wrong here? Or could it be a different problem?

---

### Post by rem on 2006-06-29
[QUOTE=d3dtn01]I also have been having trouble with skype since upgrading to dapper. I just installed the new 1.3 beta. I had to delete the /etc/asound.conf file to successfully get rid of the "Problem with your sound device" error. However, I still have a problem. When I use echo123, it's not recording my voice. To see what was up with my mic, I tried to record a test with ubuntu's sound recorder. That didn't work. It doesn't appear to be capturing the input. I'm not very familiar with how the mic works. I'm hoping that I just need to change a setting. Here's some info from my alsa mixer settings:

It says at the top: HDA Intel (Alsa mixer)
Under playback tab I have 4 volume controls: master, pcm, capture mux and capture mux. All of these are unmuted.
Under capture tab I have 1 control: capture. This is unmuted.
Under options tab my input source is mic. 

Do I have something wrong here? Or could it be a different problem?[/QUOTE]


i removed the etc/asound.conf file and completly broked my system ... is that really what you did to make it work?

---

### Post by d3dtn01 on 2006-06-29
[QUOTE=rem]i removed the etc/asound.conf file and completly broked my system ... is that really what you did to make it work?[/QUOTE]

Well, essentially yes.  I typed this: ```
mv /etc/asound.conf /etc/asound.conf_backup
``` then rebooted. That's didn't seem to cause me any problems.

---

### Post by rem on 2006-06-29
[QUOTE=d3dtn01]Well, essentially yes.  I typed this: ```
mv /etc/asound.conf /etc/asound.conf_backup
``` then rebooted. That's didn't seem to cause me any problems.[/QUOTE]

I see... don't know what the issue might me over here ... I manged to restore it but in failsafe only...

---

### Post by matjaz_pirnovar on 2006-06-29
[QUOTE=d3dtn01]Well, essentially yes.  I typed this: ```
mv /etc/asound.conf /etc/asound.conf_backup
``` then rebooted. That's didn't seem to cause me any problems.[/QUOTE]

Hi all,

Well, I did manage to get it work with typing above command - mv /etc/asound.conf /etc/asound.conf_backup      (well done d3dtn01)

Disabling /etc/asound.conf from previous skype adjustments seem to be the key. At least for the "Problem with the sound device" issues. Hope this command d3dtn01 posted will help others with this problem.

I am damn glad that now sound works, also when using Sound juicer (CD) simultaneously.

But I agree, there are other issues too, so let's keep working on them...

Smile,
M

---

### Post by morgengenuss on 2006-06-29
new skype beta worked out of the box for me. just downloaded the deb file and installed it.
i can only advise you to try to make it work, it really seems to be a big step forward (apart from video-calls it's really close to windows version now).

---

### Post by garba on 2006-06-29
yeah, too bad my mic doesn't work with dapper, after all no one needs a mic these days, why bother with fixing it for this super polished release

---

### Post by matjaz_pirnovar on 2006-06-29
[QUOTE=garba]yeah, too bad my mic doesn't work with dapper, after all no one needs a mic these days, why bother with fixing it for this super polished release[/QUOTE]


Hi,

You did check all the boxes in alsa and enabled mic. options?

ps: in previous postings usb types of mics don't seem to work very well.

I'm using non-usb headset + mic successfuly...

M

---

### Post by mark2741 on 2006-06-29
[QUOTE=matjaz_pirnovar]Hi all,

Well, I did manage to get it work with typing above command - mv /etc/asound.conf /etc/asound.conf_backup      (well done d3dtn01)

Disabling /etc/asound.conf from previous skype adjustments seem to be the key. At least for the "Problem with the sound device" issues. Hope this command d3dtn01 posted will help others with this problem.

I am damn glad that now sound works, also when using Sound juicer (CD) simultaneously.

But I agree, there are other issues too, so let's keep working on them...

Smile,
M[/QUOTE]
I don't even have an /etc/asound.conf file. Should I?

---

### Post by matjaz_pirnovar on 2006-06-30
[QUOTE=mark2741]I don't even have an /etc/asound.conf file. Should I?[/QUOTE]

Hi,

No, not at all. Only if you have reconfigured your alsa when you were using previous version of skype (together with the hijacker).
If you haven't, then no worries.

Then Skype 1.3 shouldn't have "Problem with sound device" note I guess. You don't get this message or you do?

:) 

M

---

### Post by RafRaf on 2006-06-30
HI, 

I did not have any /etc/asound.conf file either but I got no sound from skype test call. Anfter a computer restart it now works fine :)

---

### Post by rem on 2006-06-30
[QUOTE=rem]i removed the etc/asound.conf file and completly broked my system ... is that really what you did to make it work?[/QUOTE]

[QUOTE=rem]I see... don't know what the issue might be over here ... I manged to restore it but in failsafe only...[/QUOTE]

yes, indeed my bad! don't know how exactly but i managed to wipe out the asound.conf's file content instead of deleting or renaming it completly. that's why my system got broken... but here's a success story:

i fixed it with the Live CD (amazingly it worked like a charm with *sudo e2fsck /dev/hda1* - complete successful recovery when i thought everything was lost). anyway, mounted hda1 from within the cd after recovery and deleted asound.conf file this time and rebooted... my new skype is working great now! Man.. Ubuntu rocks!

---

### Post by mips on 2006-06-30
I just installed the new beta version and I must say the sound is much better using alsa.

No problems here, I simply installed it and it worked first time.

---

### Post by Linux-Freedom on 2006-07-01
[quote=wieman01]Too bad... just tried the new version of Skype and it turned out that it's called a BETA version for a reason... My bluetooth headset would stop the service after 15 to 60 seconds so the other party wouldn't be able to hear me any longer.
[/quote]
 
I have a similar problem after 10 to 120 seconds (it varies from call to call) the other party cannot hear me any longer. (I have no problem hearing them) I am using a wired headset that has had no problem before on the previous Linux version and the Window versions. 
 
On the plus side, I must say that the sound quality is 100% better for me. However, I must find a fix for this because I usually talk for more than 10 seconds :grin:. Any ideas?

---

### Post by mips on 2006-07-01
Well it's still beta. Might want to look in the Skype Linux forums.

---

### Post by rpalyvoda on 2006-07-01
It's a pity there is no video conferencing... And I've got to keep using XP for that.

---

### Post by vaskark on 2006-07-01
Why oh why can't they make skype with gtk2!?!?!

---

### Post by amoore on 2006-07-02
First of all, Im very excited that development is still on for the linux version of Skype. I thought that Skype had forgotten about us linux users. 

But the new beta .deb dosen't work for me. I can hear sound but skype does not capture my audio. I did use both the options for OSS and ALSA with no luck. Suport for ASLA would be great!!! If it worked!!!! After all it's just a beta.

I am however disapointed that this new version of Skype for linux does not have SMS messaging or Video chat.
 
Also, it would be nice if the people over at Skype mate would release a new version of Skype mate for linux with the updated d-bus or just release their code open source for us that have B2k adapters.

Secondly, skype should include a bluethooth modual for bluethooth headsets or bluethooth phones that would allow skype to connect to these devices but, maybe Im asking too much, after all it would just be away for me to use skype more and buy more skype mins. "$$$$cha-ching$$$$ $kype"

Third, skype should include a optional plugin for Evolution so that you could click and call from your contacts.

All being said, I can wait till this beta version is more mature, good job skype for keeping the linux devlopment a live. keep up the good work.

-Skype user: AndrewMoore420

---

### Post by jvictor on 2006-07-02
Tried it out 
Looks good used ALSA (with disabled ESD), audio quality is good 
had to install qt libs though

```
      sudo apt-get install libqt3-mt
```

No video till now is a dissapointment.

Seamless IM & Videoconferencing is something what Linux lacks :(

---

### Post by nocturn on 2006-07-03
[QUOTE=jvictor]
Seamless IM & Videoconferencing is something what Linux lacks :([/QUOTE]

AFAIK, you can have that on Linux, BUT not using a proprietary program (Skype) that is lightyears behind it's windows counterpart.

Ekiga is one program that does voip and video.  I heard it is quite good.

---

### Post by jvictor on 2006-07-03
> Ekiga is one program that does voip and video. I heard it is quite good.

Thanks i just tried the windows version :) and it works .. so I'm gonna test it today with win <-> linux and will come bac with the results

---

### Post by encompass on 2006-07-09
Still doesn't work for me... same problem I had before.
The sound after everywhere from 1 second to 60 minutes. It will suddenly make the sound un-understandable and "clicking noises" when ever they speak or make a noise.  They can hear me ok.  But I can't understand them.,  Hang up and call again and it works fine.  I am going to start a post on this.

---

### Post by andb on 2006-07-11
Ok, its ALSA but its not always friendly... If I start a call, I can then listen to music, but if I have Quod Libet even running (not playing), there is no error but also no sound in Skype. Skype and mplayer happily coexist, but the sound levels are far too different to be useable. If Beep Music Player is playing, Skype gives me a "Problem With Sound Device" when I initiate a call. Ive only played with it a little while, but it seems like this beta is more of a issue fix release than a new feature release...

edit: after restarting the machine, skype and quodlibet seem to be working together fine...

---

### Post by frodon on 2006-07-11
did you set the sound device to alsa in the skype options ?
Also you have to remove all the tweaks you've done in the past with OSS/ALSA or ESD.
In my personnal case this beta solved all the sound issues i had in the past with skype.

---

### Post by matjaz_pirnovar on 2006-07-13
I have the same issue as andb with RealPlay.

Can listen to it  but when initiating skype call - Problem with the sound device.

Sound Juicer, gmplayer and xmms work fine.

Although with xmms I must set the pre-amp volume lower to have skype/computer volume higher. 
When increasing main volume in xmms, also skype volume increases. So, the only way to make xmms quieter (to listen it in the background) is to lower the pre-amp volume.

M

---

### Post by matjaz_pirnovar on 2006-07-13
Have a side question guys,

Anyone knows how to record voice on new skype?

Using Sound Recorder I'm able to record only my voice but not partner's. Audacity doesn't want to work...gives me error when installing it.

Just a short tip is enough.

Thanks.

M

---

### Post by Hiroshima on 2006-07-14
Hmmm, I tried the normal version of (Skype Kubuntu Dapper) and the icon just bounced a while and then disappeared.  I thought maybe the beta would have better luck starting up, but sadly, not.

Since l lot of people seem to have Skype working, perhaps it isn't a skype question for me but something in the way it is loading...

Any ideas?  Thank you, Hiroshima

---

### Post by seeklinux on 2006-07-14
Works for me too. I couldn't seem to make calls any more after the recent update (new kernel?).  I uninstalled the old version and installed the beta and I can make calls again. And you can test your audio first which is a nice addition.

---

