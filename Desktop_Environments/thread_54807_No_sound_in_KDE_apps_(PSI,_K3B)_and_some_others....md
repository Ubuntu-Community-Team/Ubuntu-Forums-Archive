---
title: "No sound in KDE apps (PSI, K3B) and some others..."
date: 2005-08-06
forum: Desktop Environments
---

### Post by michux on 2005-08-06
Hi all. I thought I could finally solve my sound problems with Hoary alone, but I guess I'm becoming desperate and out of ideas.

My settings:
- I use Gnome
- I use ESD daemon for sound
- The system can play sounds from different sources at the same time (like totem playing a movie, xmms playing some music, and Gnome producing some system sound) - this works great

The thing is, all non-gnome apps seem no to work. For instance:
- in PSI I have no sound, but when I log out of gnome, then suddenly all the sound go wild and I have to listen about 100 online-ofline-new message beeps before logging in again. Wild!
- In K3B I just get the standard error:
[i]Error while initializing the sound driver:
device: default can't be opened for playback (Device or resource busy)[/i]
so it seems like it's trying to use some other kind of driver than ESD
- Same occurs i.e. in Terminal Services Client. After logging out of the Windows machine I get tons of messages that there is some problem with the sound card (no beeps at this time)

There seems to be some settings problem, but I'm not sure if I should try to set up all the apps I use separately, or maybe there is some magical config file which tells the system that it should use ESD for the KDE apps?
I tried looking for some sound options in K3B and PSI but I found none referring to the sond driver...

Any thought very welcome.

---

### Post by michux on 2005-08-06
[QUOTE=michux]
- in PSI I have no sound, but when I log out of gnome, then suddenly all the sound go wild and I have to listen about 100 online-ofline-new message beeps before logging in again. Wild![/QUOTE]

OK, I got it for PSI. It just uses an external program for playing sounds. I changes "play" to "mplayer" and it works like a breeze now (although in hoary :))
I also managed to get the sound working for amaroK (just for testing cuz I use Beep-media-player anyway). I had to download the amarok-xine plugin and disable KDE sounds in kcontrol.

Still, K3B and rdesktop produce errors...

---

### Post by C38a7r1zvl on 2005-08-06
Well, KDE has its very own soundserver called artsd. Now I'm not an expert for that stuff but I guess you only have two options: a) use artsd for all your programs or b) provide some kind of a "proxy" which palms itself off as artsd but just "redirects" the stuff to your actual sound system.

---

### Post by michux on 2005-08-06
[QUOTE=dePOLL]Well, KDE has its very own soundserver called artsd. Now I'm not an expert for that stuff but I guess you only have two options: a) use artsd for all your programs or b) provide some kind of a "proxy" which palms itself off as artsd but just "redirects" the stuff to your actual sound system.[/QUOTE]

Is there such an app? Mapping artsd to esd? I never heard of such.
Anyway, these multiple ways of handling sound in Linux start to make me sick, really....

---

### Post by doc_holiday on 2005-08-10
I don't have sound in amarok (using gnome) I've installed xine engine. Anybody knows what to do?

---

### Post by doc_holiday on 2005-08-11
[QUOTE=doc_holiday]I don't have sound in amarok (using gnome) I've installed xine engine. Anybody knows what to do?[/QUOTE]
Anybody?

---

### Post by anarki on 2005-08-11
[QUOTE=doc_holiday]Anybody?[/QUOTE]
 Try this: Open Sound System from KDE Control Center go to tab 'hardware', and choose eSound (esd, Enlightenment Sound Daemon, however it is) as audio device.

If that don't work, than simply kill esd, run artsd and play music with artsd :wink:

---

### Post by anarki on 2005-08-11
Sorry about double posting.

About 'redirecting' sound: You can run artsd and artsdsp. This will redirect all contest write to /dev/dsp device on your arts sound server.

---

### Post by nekr0z on 2006-06-15
A much easier way to get sound in PSI: leave everything by default and do

sudo apt-get install sox

---

