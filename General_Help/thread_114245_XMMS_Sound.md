---
title: "XMMS Sound"
date: 2006-01-08
forum: General Help
---

### Post by noeluylee on 2006-01-08
Hi,

I am having error playing XMMS. The error I encounter is -Couldnt open audio: Please check that: Your soundcard is configured properly, You have the correct output plugin selected. No other program is blocking the soundcard.

Sometimes it plays sometimes not. once I played something like in Kaffiene or my kopete just receive a msg motification with sound, then I encounter error at xmms.

is there any fix for this? :)


Thanks

---

### Post by ace2005 on 2006-01-08
Make sure xmms-arts is installed

In XMMS go into Preferances and change the output plugin to arts

Go into kcontrol and pick Alsa as the output hardware, thats the one that works the best for me but you might want to try some of the others. Make sure that "Auto-Suspend if idle after" is set to something like 1 second, so that if XMMS stops playing other apps can use the sound system

This is whats causing the problem, arts is holding onto the sound system, change the setting and all should be working fine

IF you use arts as sound output in xine or any other video apps, you may find that the audio is out of sync and that there is a delay, so using alsa directly in video apps is the best thing to do, but its fine for just audio like playing MP3s

---

### Post by noeluylee on 2006-01-08
Hi I've gone thru KControl, but I cannot find where to setup the ALSA. KControl is the Control Center right?  its where i could fine the Appearance and Themes right? can u point me the exact location where i could change the output hardware, sorry im very new to kubuntu.

---

### Post by ace2005 on 2006-01-08
Alt + F2 and then Run "kcontrol"

Then go into "Sound and Multimedia" and then into "Sound System"

In the General Tab (the one your in now) at the bottom set the "Auto-Suspend if idle after" to 1

There is also a sound buffer which might be the cause of sound going out of sync, have a play with that and see what happens

Go into the Hardware tab, select the sound output device (alsa works the best for me)

Everyone was new to Kubuntu at some point

---

### Post by angrykeyboarder on 2006-01-08
[QUOTE=noeluylee]Hi,

I am having error playing XMMS. The error I encounter is -Couldnt open audio: Please check that: Your soundcard is configured properly, You have the correct output plugin selected. No other program is blocking the soundcard.

Sometimes it plays sometimes not. once I played something like in Kaffiene or my kopete just receive a msg motification with sound, then I encounter error at xmms.

is there any fix for this? :)


Thanks[/QUOTE]

Here's what I did.

```
$ sudo apt-get install amarok-gstreamer
$ sudo apt-get remove xmms*
$ amarok &
```
That works very nicely and [ amaroK]("http://amarok.kde.org/content/view/51/1/") is an app you can use without being 2" from your screen. ;-)  Not to mention it just kicks butt in general.

---

### Post by noeluylee on 2006-01-08
I Got it :) Thanks so much :)

---

### Post by angrykeyboarder on 2006-01-09
[quote=noeluylee]I Got it :) Thanks so much :)[/quote]

Heehee. Glad I could "help". ;-)

---

