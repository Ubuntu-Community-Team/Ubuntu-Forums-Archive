---
title: "Sound and KDE?  ARTS/ESD/OSS ???"
date: 2005-03-22
forum: Desktop Environments
---

### Post by moopere on 2005-03-22
Sound works fine with Hoary or Warty under gnome using esd on top of alsa.

For some reason only some sounds work under kde.  If I try the 'test sound' from Control Center I get sound, but I don't get system sounds at all, nor other sounds.

Probably something to do with Arts I imagine - things like amarok work under gnome but not under kde for instance (!!!).  Any way to change kde to esd or is arts hard coded?

Cheers,
Craig

---

### Post by moopere on 2005-03-23
[QUOTE=moopere]Sound works fine with Hoary or Warty under gnome using esd on top of alsa.

For some reason only some sounds work under kde.  If I try the 'test sound' from Control Center I get sound, but I don't get system sounds at all, nor other sounds.

Probably something to do with Arts I imagine - things like amarok work under gnome but not under kde for instance (!!!).  Any way to change kde to esd or is arts hard coded?

Cheers,
Craig[/QUOTE]
 Lots of reads, no answers though....noone having trouble with sound and KDE?

Some further developments:  Updated today to the latest hoary packages...no change, decided to completely remove gnome - mainly because its so slow and unconfigurable it drives me nuts but also because I was beginning to wonder if some weird esd related conflict was the root of my problem...

Well, after a mammoth effort of cleaning out all gnome related stuff (I went overboard with this admittedly) I reboot, kdm comes up (very nice!) I log in to KDE and get the _loud_ startup music.  Fab.  System sounds generally seem to work.

So, I'm getting pretty happy, but I'm a fan of streaming radio so I go for amarok - I know this used to work under gnome but I can't get anything out of KDE.  I've tried the arts engine and the xine engine....nada.  Plenty of network activity, so something is happening, just no sound - anyone actually using amarok to stream audio?  Whats the right engine to use?  gstreamer???

Cheers,
Craig

---

### Post by cwaldbieser on 2005-03-26
I have amarock working under KDE using the gxine engine.  I noticed amarock doesn't change the engine-properties panel until you actually hit the "Apply" button-- but it seemed to work with the defaults for me.

I don't get any system sound out of either KDE or Gnome, though I have worked out all my games, music players, etc to work with the new sound systems.

I have esd running, as that seems to make some of my apps happy, but it hogs /dev/dsp (which KDE is quick to point out when it starts up).  I tried setting arts to use esd, but that doesn't seem to make a difference.

---

### Post by Julius on 2005-03-26
I chose OSS as sound system in the control center and it works ... but with the last update amarok complained about something... anyway it did work ok

---

### Post by Ironi on 2005-03-26
I'm not having any audio probs (ALSA, with amarok & kaffeine using xine engine). However, my Audigy 2 ZS can handle multiple apps/backends attempting to access /dev/dsp at the same time. ;)

Also, amarok doesn't seem to be too great at handling streams; kaffeine is far better for those IME.

---

### Post by moopere on 2005-03-27
Thanks for the replies folks.  Looks from the small sample above that there is quite a variation in getting sound (and amarok) to work in a consistent manner.

I did get amarok working in the end, but only by installing gstreamer and telling -it- to use the artsd audiosink.

This is seriously voodoo stuff here.  I fired up one of my other machines during the testing of this problem and updated to the latest hoary/gnome, I've got to admit, the gnome/ubuntu team are really laying on the polish - things 'just work'.

I think I will now go away and dedicate my life to bringing this sort of user experience to ubuntu/kde.  I can't see any particular reason why kubuntu can't be as 'switch on and use' as ubuntu/gnome is. :roll: 

I've posted elsewhere about what I view as a serious application overlap/overkill with KDE.  For instance, once I got amarok working I compared it against kaffeine - theres a lot to like with amarok, but kaffeine does seem to perform its task somewhat better (and it worked without as much stuffing around)

So, shouting at the world in general, why do we have _both_ amarok, which doesn't work out of the box, and kaffeine (which does) in kubuntu at the same time?

I'm sure there is more than one application for gnome which plays audio, yet ubuntu/gnome have chosen rhythmbox, for better or worse...seems to work.  I think we should think about this in relation to KDE as well.  For any given task, use the application available -now- which actually performs that task well, drop the rest into universe or whatever.

Aynway, I digress, I'm going to wander off now and see if I can't learn something useful about alsa/esd/ARts/gstreamer and their relationships to each other.

Cheers,
Craig

---

### Post by neighborlee on 2005-03-27
[QUOTE=moopere]
Aynway, I digress, I'm going to wander off now and see if I can't learn something useful about alsa/esd/ARts/gstreamer and their relationships to each other.

Cheers,
Craig[/QUOTE]
----------------
I installed kubuntu via synatpic and first thing I saw when booting into kde was that permissins on /dev/dsp were wrong and I had no sound..easy fix of course but just thought I'd  mention it..

cheers
nl
----

---

### Post by Reb on 2005-04-10
It's not working for me. System sounds do fine, I tell amaroK to use gstreamer, and tell gstreamer to use arts, but arts still segfaults when I start amaroK. It's all really confusing to me.
I should add that system sounds work fine.

---

### Post by Reb on 2005-04-10
Okay... run gstreamer-properties, choose artsdsink, configure amaroK to use gstreamer and artsdsink. Works.

---

### Post by connellr on 2005-04-11
[QUOTE=cwaldbieser]I have amarock working under KDE using the gxine engine.  I noticed amarock doesn't change the engine-properties panel until you actually hit the "Apply" button-- but it seemed to work with the defaults for me.

I don't get any system sound out of either KDE or Gnome, though I have worked out all my games, music players, etc to work with the new sound systems.

I have esd running, as that seems to make some of my apps happy, but it hogs /dev/dsp (which KDE is quick to point out when it starts up).  I tried setting arts to use esd, but that doesn't seem to make a difference.[/QUOTE]

2 sugestions (but first my story...)

Ok, after trying about 1/2 a dozen "fixes" to the whole sound issue and having the same problem you mentioned above (not being able to hear system sounds, but getting sounds from applications such as music players) I decided to try something different.   I set all of my audio settings back to the default (removing any extra config files I created, etc).  I then grabed an old Sound Blaster Live PCI card from the ever-growing computer musieum I have in my closett, blew the dust off it and slaped it into an available PCI slot, I then disabled my onboard sound and Presto!  everything worked the way it should.  System sounds played fine, I could play music, movies etc hear sounds from multiple apps at once ... and its everything I dreamed it could be.  

SUGESTIONS:

1)  Spend $10 on eBay and get an old SoundBlaster Live so you dont have to deal with any of these sound headachs.

2)  If you dont feel like forking out $10 for a new sound card, or cant change sound cards for some other reason try this:  Go to Settings > Sound&Multimedia > System Notifications, and choose the option that says 'Play With' then select an option such as aplay, mplayer, or any installed console-based media player.  (if such media players are already working, telling KDE to use those apps to play system notification sounds should solve your problem).

Good Luck, Hope this helps!

---

