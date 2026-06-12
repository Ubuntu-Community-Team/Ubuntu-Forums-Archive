---
title: "Xgl/Compiz movie woes, Metacity multi-booting"
date: 2006-09-10
forum: Desktop Environments
---

### Post by Onos on 2006-09-10
I get Xgl and Compiz running (actually looks pretty decent on my Compaq Presario 5301RSH)...

...but to my deep chagrin, I find out that mplayer is not playing back *.avi, *.mp(e)g or *.asf without severe artifacting and an annoying band of miscoloration at the top 10% of the screen.

As for .mov (Quicktime) files, they playback without any distortion/artifacts... but the audio synch is very delayed.

A HOWTO or tutorial I googled up somewhere suggested running mplayer with these options:

```
mplayer -zoom -vo x11 "movie.avi" 
```
(this runs smoothly, but has synching issues with the audio)

```
mplayer -zoom -vo x11 -hardframedrop "movie.avi"
```

(Runs a little more roughly, some artifacting on higher framerates. Significant choppiness/artifacting at fullscreen settings, but the audio is synched.)

And it goes without saying - that this solution will not work when running mplayer embedded in firefox... although I am guessing that there is some way of setting this up to do it by editing ~/.Xsession or ~/.mplayer/config  or a similar file.


Which leaves me (for being a linux n00b) with the alternative of switching back to Metacity.

I think I goofed up something somewhere: trying to loading Metacity from the gdm login screen often (usually) results in some kind of looping behaviour where I wind up having to re-log in three or four times before Metacity finally decides to complete loading in.

Is there anything that I can do to fix that (short of something drastic - such as reloading the OS for the sixth time) ?

Maybe one of these days I will learn how to leave well enough alone (sticking w/ the stock Metacity....) ](*,)



Attached images: comparing movie playback in Compiz/Xgl vs. Metacity

---

