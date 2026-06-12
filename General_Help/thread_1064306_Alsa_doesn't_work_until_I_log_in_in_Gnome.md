---
title: "Alsa doesn't work until I log in in Gnome"
date: 2009-02-08
forum: General Help
---

### Post by thomasloven on 2009-02-08
Hi.
I'm seting up a home media server on a normal desktop machine.
At first I used Ubuntu Server edition, but then I wanted it to be able to play music through it's own speakers.
For this I use xmms2, so I can controll it remotely.

Now though I ran into a problem.
It seems alsa doesn't realy activate until I log in to gnome.

i.e.
-I start up the computer (using WOL or just the power button)
-I ssh into my account
-I try to use xmms, aplay, speaker-test or anything sound-related over ssh
-It doesn't work.

-I start up the computer
-I go to it and log in to gnome directly
-I ssh into my account
-Music works perfectly over ssh
It also works if I log out from gnome again.

My guess is that gnome runs some kind of magic routine for activating alsa or alternatively pulseaudio.
The problem is, I can't seem to find out what this is.
Does anyone know what to do, or where to look?

---

