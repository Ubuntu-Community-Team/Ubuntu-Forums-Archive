---
title: "Is there any player for .mov?"
date: 2005-09-11
forum: Desktop Environments
---

### Post by srinath on 2005-09-11
I have realplayer and totem. I installed most of the codecs but the .mov does not play. Totem just opens and closes and Realplayer gives me an error.

---

### Post by krusbjorn on 2005-09-11
I have yet to find a movie file mplayer doesnt eat for breakfast. 

[http://ubuntuguide.org/#mplayer](http://ubuntuguide.org/#mplayer)

---

### Post by az on 2005-09-11
mplayer uses the w32codecs.  So does xine.  You can use totem-xine to make totem use the windows codecs and the nyou will be able to get quicktime (mov) playback.  There is a free opensource version of the quicktime cocec, but it has some trouble with sound.  Did you install all the gstreamer plugins?

If you want to switch totem to use xine, install the totem-xine package.  Install the w32codecs package, too.

---

### Post by srinath on 2005-09-11
I don't think I installed gstream. But I installed mplayer and now I have playback! Thanks a lot!

---

### Post by batterhead on 2005-09-11
[QUOTE=krusbjorn]I have yet to find a movie file mplayer doesnt eat for breakfast. 

[http://ubuntuguide.org/#mplayer](http://ubuntuguide.org/#mplayer)[/QUOTE]

I can't seem to get mplayer to install. I get the error:

ckline@dev:~$ sudo apt-get install mplayer-386
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package mplayer-386

I have all the repositories set (I think) but still nothing. I think there is a special version for AMD as well, right?

Thanks for any help.

---

### Post by Hairy_Palms on 2005-09-11
you havent got the other repos or mplayer would be found, 
[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)
then install mplayer but instead of mplayer-386 do mplayer-k6

---

### Post by krusbjorn on 2005-09-11
Edit: never mind.

---

### Post by batterhead on 2005-09-11
[QUOTE=Hairy_Palms]you havent got the other repos or mplayer would be found, 
[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)
then install mplayer but instead of mplayer-386 do mplayer-k6[/QUOTE]

Cool that worked!!

Now I have playback in Firefox (watching trailers, etc.) but no sound. Is there a fix for this? I will search some more :)

---

### Post by srinath on 2005-09-11
[QUOTE=batterhead]Cool that worked!!

Now I have playback in Firefox (watching trailers, etc.) but no sound. Is there a fix for this? I will search some more :)[/QUOTE]

Configured sound? [http://ubuntuguide.org/#configuresoundproperly](http://ubuntuguide.org/#configuresoundproperly)

---

### Post by Goober on 2005-09-12
VLC should work, it has played everything I have thrown at it thus far.  I am not 100% sure how to install it, it might be sudo apt-get install vlc, but again, I am not 100% sure.  MPlayer is all well and dandy, but I am a commited VLC fan.  

But MPlayer can configure with Firefox for watching movie trailers and such online, so I guess its give and take . . .

Just to edit that sudo apt-get install vlc will indeed install VLC for you, then run it by simply typing in "vlc" into a command line.

---

### Post by Perfect Storm on 2005-09-12
[QUOTE=Goober]VLC should work, it has played everything I have thrown at it thus far.  I am not 100% sure how to install it, it might be sudo apt-get install vlc, but again, I am not 100% sure.  MPlayer is all well and dandy, but I am a commited VLC fan.  

But MPlayer can configure with Firefox for watching movie trailers and such online, so I guess its give and take . . .

Just to edit that sudo apt-get install vlc will indeed install VLC for you, then run it by simply typing in "vlc" into a command line.[/QUOTE]

sudo apt-get install vlc vlc-plugin-esd mozilla-plugin-vlc

When installing vlc its automatically wxvlc which is the frontend of vlc.
vlc-plugin-esd to support Esound.
mozilla-plugin-vlc adds browser support.

---

### Post by Hairy_Palms on 2005-09-12
to get sound in firefox youve gotta kill the esd
open a terminal and type 
killall esd
i really hope they drop esd as default in breezy coz its got so many damn problems. first thing i do is always change everything to alsa.

---

### Post by batterhead on 2005-09-13
[QUOTE=srinath]Configured sound? [http://ubuntuguide.org/#configuresoundproperly](http://ubuntuguide.org/#configuresoundproperly)[/QUOTE]

Yup. Configured sound just like that and installed all the codecs (thought the w32 codec game me an obsolete message). Still no sound when trying to watch Apple Movie trailers (or other quicktime) in Firefox. Any thoughts?

Thanks,
B

---

### Post by srinath on 2005-09-13
Tried this too?---

[QUOTE=Hairy_Palms]to get sound in firefox youve gotta kill the esd
open a terminal and type 
killall esd
i really hope they drop esd as default in breezy coz its got so many damn problems. first thing i do is always change everything to alsa.[/QUOTE]

---

### Post by batterhead on 2005-09-13
Yes. Tried that too :(

---

### Post by SlugO on 2005-10-24
I can't get .mov's to work either. I've installed w32codecs and libquicktime1. Totem only plays sound and crashes, VLC only plays video with no sound. Any ideas on how to get them to work with Totem?

Or should I just try to sync VLC's video to Totem's sound.. :???:

---

