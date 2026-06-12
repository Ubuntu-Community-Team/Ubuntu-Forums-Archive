---
title: "Ubuntu 5.10 - Looping 'bongo drum' sound problem"
date: 2005-11-15
forum: Desktop Environments
---

### Post by Giardap on 2005-11-15
I have just installed Ubuntu 5.10 on an older machine (Pentium II 450, 384 RAM, 45 GB hard drive on an Intel board that came with a Gateway 2000 in 1998). I think it has on-board sound - AC'97 ???

Install went fine. As I logged in, entering user and password, a continuous 'bongo drum' sound started and repeated (possibly some 'event' system sound). I could continue to log in, and the web browser works, but the sound just keeps going. Anyone know a fix for this? Is it a known bug?
I'm new to Linux and really only operate at GUI level. I installed Hoary Hedgehog on another machine previously without problems. Is this problem only a 5.10 issue? Thanks

---

### Post by suRoot on 2005-11-15
Not sure why you're having the problem, but you can kill the sounds by going to System -> Preferences -> Sound & killing the check box for "Sounds for events".  You can also remove them on the "Sound Events" tab, look for the ones under "User Interface Events" and "System Events".

After you fix that, try playing an mp3 or wav or something to see if your sound card works properly.  If not, we can all go from there.

---

### Post by Giardap on 2005-11-16
OK- tried that but without success. Still this incessant drum sound!

---

### Post by bryan986 on 2005-11-16
Goto System->Administration->Login Screen Setup
Click the Accessability Tab
Uncheck the "Make a sound when login window is ready"
Uncheck the "Make a sound after a successful login attempt"
Uncheck the "Make a sound after a failed login attempt"

---

### Post by dcstar on 2005-11-16
[QUOTE=bryan986]Goto System->Administration->Login Screen Setup
Click the Accessability Tab
Uncheck the "Make a sound when login window is ready"
Uncheck the "Make a sound after a successful login attempt"
Uncheck the "Make a sound after a failed login attempt"[/QUOTE]
Or there is some program crashing and restarting continuously that causes the sound.

Possibly time to look at the system logs for anything suspicious (Applications-System Tools-System Log)

---

### Post by Pyxidis on 2005-11-17
Hi all,
I have the same problem myself.  I just upgraded a Tiny laptop from Hoary (which worked perfectly well) and now when I start the machine up, the "rolling bongo" thing happens to me.  Also, I can't get any sound from other apps, including the CD player, XMMS, Totem-Xine or anything.  Very frustrating.  I googled and the only suggestions I found where to try changing the sound server to ALSA or something.  If I do this and reboot I get no sound at all, which while less annoying is just as useless.  I really don't want to go back to Hoary as my wireless lan works beautifully with Breezy, but I may have no choice until a fix is found.

In the absence of any working fixes for Breezy, you could try installing Hoary instead.

Pyx.

---

### Post by bin on 2005-11-17
Yup - been there and danced the dance:) 

Funny thing is that re-installing 5.10 again "fixed" it. Had the same problem with 5.04 as well.

When it happed the first time on 5.10 I just switched the machine off in disgust - next day it was fine!!!

I think it's something to do with ESD gettings its knickers in a twist.

in light

bin

---

### Post by Giardap on 2005-11-20
Thanks.
Tried suggestions from Bryan986, dcstar and pyxisis (reinstall Hoary 5.04) without success. Even installed on its owndedicated 10GB hard drive. No joy!
It must be smething specific to my hardware (Gateway 2000 350 with extensive upgrading!). Hoary installed fine on a newer machine recently.
Pity. Thanks to all for suggestions.

---

### Post by Giardap on 2005-11-24
OK - a sort of a solution...

I installed Kubuntu 5.10 instead!
No loopy bongo; plays audio CD's straight off; fingers crossed.

---

### Post by Giardap on 2005-12-12
OK - another sort of workaround (it's not a solution, since I've never really found out what caused the problem and then arrived at a logical solution)
This was an empirical approach)

Disabled onboard sound in BIOS. Installed a new cheap (€12.5/c.$15) 5.1 soundcard) in a free PCI slot and the loopy bongo sound problem was solved. The sound was in fact the bongo drum triplet event sound you get at the first sign-in screen where it asks for your username. I was then able to get the CD audio to work. CD Direct Audio Extraction worked with the CD player in Win XP but not in Ubuntu where I had to physically connect the CD player by cable to the new sound card.
Hope this helps someone else.

---

