---
title: "question about gstreamer0.8-artsd"
date: 2005-10-13
forum: Desktop Environments
---

### Post by sal on 2005-10-13
i want to remove gstreamer0.8-artsd and synaptic tells me i would also have to remove gstreamer0.8-plugins.

so i have the following intsalled:
gstreamer0.8-artsd
gstreamer0.8-plugins
gstreamer0.8-plugins-multivers

im using kubuntu breezy 5.10 with kde 3.5

=====
the reason i want to do this is so i don't have to do an killall artsd before running skype, realplayer, and audacity.

i have all my multimedia apps set to use alsa with the xine engines.

if i remove the three packages:
gstreamer0.8-artsd
gstreamer0.8-plugins
gstreamer0.8-plugins-multivers

will this have the effect of me not having to run the killall artsd command before running skype, realplayer, and audacity?
and will it affect my w32codecs or multimedia experiance at all in a negative way?

thanks for any help.

---

### Post by mlomker on 2005-10-13
> will this have the effect of me not having to run the killall artsd command before running skype, realplayer, and audacity?

Not sure.  The two main audio engines are Xine and Gstreamer.  Most applications can be configured to use either.  Arts is the default KDE sound engine but you can use OSS and ALSA as well.

I find sound one of the most confusing things in Ubuntu...

---

### Post by monkey89 on 2005-10-13
Skype, realplayer, and audacity all do not use gstreamer.  Removing the artsd plugin won't do anything about them.

On the other hand, you may want to disable the arts sound server in general.  If your sound card supports hardware mixing, you shouldn't need it at all (if the hardware supports playing more than one sound at once).  Try it out and see if it works well - go into the KDE control center, and under sounds and multimedia, disable the sound server.  Then artsd should not be running at all.

---

### Post by sal on 2005-10-14
[QUOTE=monkey89]Skype, realplayer, and audacity all do not use gstreamer.  Removing the artsd plugin won't do anything about them.

On the other hand, you may want to disable the arts sound server in general.  If your sound card supports hardware mixing, you shouldn't need it at all (if the hardware supports playing more than one sound at once).  Try it out and see if it works well - go into the KDE control center, and under sounds and multimedia, disable the sound server.  Then artsd should not be running at all.[/QUOTE]

i already turned it off (Enable the sound system), yet still, every time i boot up artsd is still running. i want to kill it off and not have it run at all so i won't have to continualy issue the killall artsd command.

---

