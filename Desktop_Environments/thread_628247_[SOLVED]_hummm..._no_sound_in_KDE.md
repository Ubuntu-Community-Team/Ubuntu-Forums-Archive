---
title: "[SOLVED] hummm... no sound in KDE"
date: 2007-12-01
forum: Desktop Environments
---

### Post by Multi-Booter on 2007-12-01
I decided to add KDE to my Ubuntu so I can switch back and forth when I want.

The weird part is that the sound does not work in KDE but has and does in Gnome. 

:confused::confused::confused:

---

### Post by TeaSwigger on 2007-12-01
Well it so happens KDE tends to use a different sound setup (arts). So therin lies the window for different behavior in Kubuntu vs ubuntu. Obviously check the settings in the volume / mixer controller, kmix (run 'kmix' if it's not running; should place an applet in your taskbar; right click to get to the settings). Check the KDE sound config settings ('kdesu kcmshell arts' should bring it up with system wide control, iirc, or dig around in the settings options). Beyond that I'm not familiar enough with the details as it's luckily "just worked" here so far, knock wood. Hope that helps you somehow.

---

### Post by Multi-Booter on 2007-12-01
Thanks.

I went through all of that but didn't get anywhere.

I'm thinking the problem should be obvious... but I'm drawing a big blank.

I have very little time in KDE.

---

### Post by Multi-Booter on 2008-01-01
Any other ideas on this?

---

### Post by asimon on 2008-01-02
Are you getting sound under KDE without using ARTS, i.e. try from the command line (withe konsole for example) something like 'mplayer <some music file or video with sound>' or 'ogg123 mymusic.ogg' or 'mpg123 mymusic.mp3'.

If you get sound then, it's probably related with KDE's arts sound server.
If you don't get sound then it's related to your mixer settings.

I remember that I once had a sound cards which I couldn't unmute with KDE's mixer but had to use 'alsamixer' from the commandline, because KDE's mixer was not able to show the muted channels at all.

---

### Post by Multi-Booter on 2008-01-02
Well, I finally got it working... and honestly I really don't even know what I did.

I turned everything on and wide open... and ran some commands... and was about to say screw it... and suddenly I got a desktop chime sound.

I have it all working now... even the hot keys on my fancy keyboard.

**But for some reason, MUTE does not work, no matter how you try it.**
That I can live with... it's just weird... which always sends me after the answer to "why"

---

### Post by Multi-Booter on 2008-01-02
> **asimon said:**
> Are you getting sound under KDE without using ARTS, i.e. try from the command line (withe konsole for example) something like 'mplayer <some music file or video with sound>' or 'ogg123 mymusic.ogg' or 'mpg123 mymusic.mp3'.

If you get sound then, it's probably related with KDE's arts sound server.
If you don't get sound then it's related to your mixer settings.

I remember that I once had a sound cards which I couldn't unmute with KDE's mixer but had to use 'alsamixer' from the commandline, because KDE's mixer was not able to show the muted channels at all.

I kept digging after re-reading your last paragraph.

Here is what I did to solve the MUTE issue...

I went in and changed the 'channel' representing the master volume.
That fixed the problem.

So that is something you might remember if you ever run into that ever again in life.

---

