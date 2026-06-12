---
title: "running teamspeak kills my sound :("
date: 2005-10-29
forum: Gaming &amp; Leisure
---

### Post by Nimbus_p12 on 2005-10-29
Hi all,
having another crack at linux, after a few years off, and after trying slackware, redhat, suse..

ubuntu certainly seems a lot easy, and fast :) but.....

Installed quake4 today, and it works a dream, got the sound working after trying the quake4 +set s_driver oss +set s_numberOfSpeakers 2
workaround..

So now I've installed teamspeak, so I wont need to use my winxp at all and.....

That works fine to on its own.... but.... :(

If I run teamspeak, and then start Q4 I lose the sound in Q4 ! :(
Its like Teamspeak is hogging the sound card ?

Anyone got any ideas ? 
I've done a search, but the answers there have left me even more confused, and I'm not sure I want to change all the config for the sound card if I'm barking up the wrong tree...

Message I get back from q4 is...

------ OSS Sound Initialization ------
WARNING: failed to open sound device '/dev/dsp': Device or resource busy
WARNING: sound subsystem disabled

And I can see that teamspeak is also set to use /dev/dsp too, so I'm guessing thats where its clashing but... surely they can both use it ?
Or is there something else I can make Teamspeak use ?

I'm running an AMD 3800+ with the asus A8N-SLI motherboard, onboard sound in the form of NVidia CK804

tho I also have a SBLive ! Player 5.1 [SB0060] option in the sound preferences, which I could use.. its a SB live PCI card thats still plugged in.. But I've no idea how to go about getting everything to use that soundcard instead..

help... ? :confused:

---

### Post by Nimbus_p12 on 2005-10-29
well... I got it working :)

disabled my onboard sound
set it to use the pci soundblaster card
did the ALSA thing
[http://ubuntuforums.org/showthread.php?t=44753&highlight=teamspeak](http://ubuntuforums.org/showthread.php?t=44753&highlight=teamspeak)
and it all works :)

yay !

---

