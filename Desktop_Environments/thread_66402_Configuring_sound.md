---
title: "Configuring sound"
date: 2005-09-17
forum: Desktop Environments
---

### Post by Eleaf on 2005-09-17
Ok.  I'm having a very hard time getting applications to have sound.  In amaroK, after configuring its engine, it says alsa is being used by another thing.  I think its being used by KDE's little sound thing.  This seems like a really, really bad system if it takes up all the sound for that predetermined time.  It just won't give up the sound!  Its own little sounds work fine but I can't get it to work with other applications.

What do I do!?!?!  I'm surprised by the extreme lack of information on how to get this to work!  :|

---

### Post by Takis on 2005-09-18
[QUOTE=Eleaf]This seems like a really, really bad system if it takes up all the sound for that predetermined time. [/QUOTE]
The problem with ALSA is that only one process can use it at a time - so if two programs try to make sound at the same time, they fail. KDE solves this by using a daemon (arts) that locks ALSA and then listens for connections. Processes should try to connect to arts rather than ALSA. It can combine multiple sounds and send them to ALSA as if they were one.

But you're right, not all programs know how to use arts. Go to Control Centre->Sounds & Multimedia->Sound System. Check the 'Auto suspend' button, and set the threshold to something reasonably quick (I've set it to one second).

---

### Post by raven on 2005-09-26
[QUOTE=Takis]The problem with ALSA is that only one process can use it at a time - so if two programs try to make sound at the same time, they fail. KDE solves this by using a daemon (arts) that locks ALSA and then listens for connections. Processes should try to connect to arts rather than ALSA. It can combine multiple sounds and send them to ALSA as if they were one.

But you're right, not all programs know how to use arts. Go to Control Centre->Sounds & Multimedia->Sound System. Check the 'Auto suspend' button, and set the threshold to something reasonably quick (I've set it to one second).[/QUOTE]

Hi, I have Kubuntu, KDE 3.4.2, 
I followed this guide [http://ubuntuguide.org/#configuresoundproperly](http://ubuntuguide.org/#configuresoundproperly)
but did not help, as it is more for gnome
my question how can I make more than 2 apps to work in the same time
I followed your little guide but can not make it to work ex: RP and Kaffeine to work, if I open Kaffeine than RP does not open, the moment I close Kaffeine, RP appears and ready to function
any ideas ???

---

### Post by Takis on 2005-09-26
[quote=raven]I followed your little guide but can not make it to work ex: RP and Kaffeine to work, if I open Kaffeine than RP does not open, the moment I close Kaffeine, RP appears and ready to function
any ideas ???[/quote] Howdy! Do you mean that RP does not start, or that RP does not play sound?
Also, what exactly *is* RP?

---

### Post by raven on 2005-09-26
RP is real player
and real player does not open as in you can not see the app
but the moment that I close kaffeine
real player appears and I can play streams or mp3
and not only those 2 apps, any 2 apps together cannot play sound ex: amarok, kaffeine, audacity
in a way I can not have 2 apps using the sound card, while I was using gnome, I could do it with the guide of ubuntu
but not with KDE

---

### Post by xterminus on 2005-09-26
[QUOTE=Eleaf]Ok.  I'm having a very hard time getting applications to have sound.  In amaroK, after configuring its engine, it says alsa is being used by another thing.  I think its being used by KDE's little sound thing.  This seems like a really, really bad system if it takes up all the sound for that predetermined time.  It just won't give up the sound!  Its own little sounds work fine but I can't get it to work with other applications.

What do I do!?!?!  I'm surprised by the extreme lack of information on how to get this to work!  :|[/QUOTE]

You have a couple of options.  The problem your experiencing is that your soundcard probably doesn't have drivers that support hardware mixing.  Hardware mixing means that the soundcard itself handles multiple sounds at the same time.  Software mixing means that your applications all send their sounds to a program which "mixes" all the sounds together, and it in turn actually sends the sound to your soundcard.  So your going to have to get software mixing to work.  

There are a couple options.
[LIST]
[*] You can use alsa's dmix to setup software mixing.  This is probably the most efficient way to get running, but it's also the most involved initially.  But once you have it running though, you don't have configure or reconfigure any of your applications.  A quick guide on getting dmix running can be found [here](http://www.ubuntuforums.org/showthread.php?t=32063&highlight=dmix)
[*] You can use the KDE arts sound daemon.  Set all of your applications to use arts and you should be able to play more than one sound at a time.
[*] You can use the enlightenment sound daemon (ESD) which comes with gnome to do the same thing.  ESD probably makes the most since since ubuntu is gnome based.
[/LIST]

Turning on ESD is pretty simple.  Just goto into your gnome settings, (for sound) and enable the sound server if it's not allready running.  Then tell amarok to use ESD.  You'll probably also want to run gstreamer-properties and set gnome's sound to ESD as well.  Most of this should be default in ubuntu.  Picking out ESD in amarok might do the trick in and of itself.

If you want to go the dmix route, there are a ton of guides here on ubuntuforums for the settings for specific soundcards.

---

### Post by raven on 2005-09-26
[QUOTE=xterminus]You have a couple of options.  The problem your experiencing is that your soundcard probably doesn't have drivers that support hardware mixing.  Hardware mixing means that the soundcard itself handles multiple sounds at the same time.  Software mixing means that your applications all send their sounds to a program which "mixes" all the sounds together, and it in turn actually sends the sound to your soundcard.  So your going to have to get software mixing to work.  

There are a couple options.
[LIST]
[*] You can use alsa's dmix to setup software mixing.  This is probably the most efficient way to get running, but it's also the most involved initially.  But once you have it running though, you don't have configure or reconfigure any of your applications.  A quick guide on getting dmix running can be found [here](http://www.ubuntuforums.org/showthread.php?t=32063&highlight=dmix)
[*] You can use the KDE arts sound daemon.  Set all of your applications to use arts and you should be able to play more than one sound at a time.
[*] You can use the enlightenment sound daemon (ESD) which comes with gnome to do the same thing.  ESD probably makes the most since since ubuntu is gnome based.
[/LIST]

Turning on ESD is pretty simple.  Just goto into your gnome settings, (for sound) and enable the sound server if it's not allready running.  Then tell amarok to use ESD.  You'll probably also want to run gstreamer-properties and set gnome's sound to ESD as well.  Most of this should be default in ubuntu.  Picking out ESD in amarok might do the trick in and of itself.

If you want to go the dmix route, there are a ton of guides here on ubuntuforums for the settings for specific soundcards.[/QUOTE]

Thanx for the help
I tried the link in your response, basically it like what in the unofficial ubuntu guide, but I am using KDE3.4.2, so I do not know if it is made for KDE, but it did not work anyway, when I was using gnome before, the guide or the link you supplied worked, but I am using KDE and is not working for KDE.
any suggestion for KDE
Thanx

---

### Post by greyhound4334 on 2005-09-27
I'm not an expert by any stretch, but I've got things working fairly well on my machine.  

It would help immensely if you provided some more information:
- what kind of sound card are you using?
- what engine are you using with amarok?
- do you have artsd set up?

I'm using an onboard sound chip without hardware mixing, and I can run amarok and skype and get sound from both, so it is possible.  With amarok, I've ended up using the xine engine with the "autodetect" output sink.  

With artsd, I have it set up to autosuspend if idle after 5 seconds.

We can probably get this working for you.

---

### Post by Eleaf on 2005-09-28
Aww..  Thank you guys!  Ok I have sound working in KDE.  The lag is pretty large however using arts and it does take up a lot of my processor.  I'm also having trouble playing mp3 files in Amarok and any other players.  mpeg streams work fine however.  I'm wondering what component I need for mp3 files on my computer to run?  In Amarok, the file does play but its just static. 

Thanks! =D

---

### Post by Eleaf on 2005-09-28
Alright.  I figured that out!  I needed the package mpeg3-1 and mp3's work fine!  I'm considering maybe trying something else if it will help solve the lag that arts has as for the lag is about .5 ~ 1 seconds from the time the sound is origionated but its not a very big deal untill i try and do audio editing.  I'm also having a really hard time getting jack to work..  Oh well.  I'll look it up a little bit more..  

Thank you!  =D

---

### Post by greyhound4334 on 2005-09-28
What application are you seeing the lag in?

What engine are you running with amarok?

---

