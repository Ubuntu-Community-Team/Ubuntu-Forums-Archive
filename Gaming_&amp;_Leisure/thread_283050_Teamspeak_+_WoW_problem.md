---
title: "Teamspeak + WoW problem"
date: 2006-10-23
forum: Gaming &amp; Leisure
---

### Post by 2pacalypse on 2006-10-23
I Recently started playing World of Warcraft on Linux rather then Windows, however theres two problem which prevents me from making the full transition. 

Problem 1(A.K.A. The Major Problem)- I Cant Use TeamSpeak and World of warcraft in the same time because they disable each others Audio capabilities... I searched the forum but all the posts only made me more confused :confused: . I need that Teamspeak because all my guild meetings and Raids i'm taking part are through TeamSpeak. So can any1 please explain to me, in the simplest way possible the solution to this problem?

Problem 2(Minor One)- When ever i choose players/NPC's , Or cast spells. I cant see the graphical effects that should be on the ground. this is pretty annoying because I cant target enemies with my Grenades or simular things very well. Is this one of the few Emulation bugs?

Any Help in anyone of these questions will be much appriciated.

Thanks in advance

---

### Post by Garyu on 2006-10-23
Try the hints at the bottom of this page:
[http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide](http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide)

in short, from what it says there:

sudo apt-get install alsa-oss
aoss wine worldofwarcraft.exe

that will pipe sound from oss into alsa, which might work better. do the same thing for teamspeak (use 'aoss command' to pipe into alsa).

I haven't tried this though, as I do not own a copy of WoW. Let us know if it works out.

EDIT: If the above does not work out, you could always try this howto: [http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Sound](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Sound)
Not sure how well it performs in Ubuntu though since I haven't tried this one either... :-#

---

### Post by jdunn on 2006-10-23
This site may help you, if you can understand it.  I had to read through it a few times, myself:  [http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Sound](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Sound)
Using the ALSA-OSS wrapper 'aoss' for Teamspeak, as shown in my link and suggested by Garyu, is probably the cleanest solution...However, it didn't fix my Teamspeak problem.  

Using the aRTSDSP wrapper did work but there was a sound delay (in both TS and games) that was intolerable, even after tweaking KDE Sound System settings.  If you are using gnome, I'm guessing ESDDSP is the name of the wrapper you'd try.

If neither of these work for you then I can only suggest two other ideas:

Wait for TeamSpeak3, which will probably use ALSA instead of OSS (because ALSA supports software audio mixing but OSS does not) or...

Use a different sound card...one that has hardware mixing.  Ultimately, I obtained a Sound Blaster Live Value card and all my audio troubles dissapeared...I can even play any game with audio and listen to an MP3 on Amarok and use Teamspeak all at the same time without using any special tricks.  If you are in the market for a new sound card, this site will definitely help:  [http://www.alsa-project.org/alsa-doc/](http://www.alsa-project.org/alsa-doc/)

---

### Post by 2pacalypse on 2006-10-24
I Tried this scripts
```

sudo apt-get install alsa-oss
aoss wine worldofwarcraft.exe

```
but it didnt worked :(, and the otherwebsites only confuse me more because im dont understan anything in there. i dont even understand whats the diffrent between ALSA and OSS :S. I guess I'll just wait for TS3 (When ever that will happen)

---

### Post by jdunn on 2006-10-24
> **2pacalypse said:**
> I Tried this scripts
```

sudo apt-get install alsa-oss
aoss wine worldofwarcraft.exe

```
but it didnt worked :(, and the otherwebsites only confuse me more because im dont understan anything in there. i dont even understand whats the diffrent between ALSA and OSS :S. I guess I'll just wait for TS3 (When ever that will happen)

OSS (Open Source Sound) is the old sound system for linux and is no longer used.  ALSA is the new sound system.  Games are usually designed to use only one of these two sound systems.  Old games like Enemy Territory were designed to use OSS but work in Ubuntu because ALSA is backwards compatible with OSS.

'Mixing' allows two or more games to share your sound card at the same time.  ALSA can support mixing in software, but only ALSA games can take advantage of software mixing.  OSS does not support sotware mixing so, an OSS game will not share your soundcard.  (example:  Teamspeak was designed to use OSS so it won't share your soundcard)  AOSS is a software layer that is supposed to make linux think your OSS game is an ALSA game.  Hardware mixing is a feature of certain sound cards that will mix anything seemlessly, whether games are ALSA, OSS or anything else.

That's the jist of it.

---

### Post by Sammi on 2006-10-25
Do external soundcards hava hardware mixing?

If yes, does anyone know which cards?

I have a laptop, so it isn't possible for me to use a pci card.

---

### Post by jdunn on 2006-10-25
> **Sammi said:**
> Do external soundcards hava hardware mixing?


Probably not.  I imagine an external soundcard would use USB.  Check here:
[http://www.alsa-project.org/alsa-doc/](http://www.alsa-project.org/alsa-doc/)

---

### Post by Sammi on 2006-10-25
ok so an external card wouldnt fix this for me... :mad:

---

