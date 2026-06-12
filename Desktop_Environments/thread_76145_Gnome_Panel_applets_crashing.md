---
title: "Gnome Panel applets crashing"
date: 2005-10-14
forum: Desktop Environments
---

### Post by Bigglez on 2005-10-14
I recently introduced a friend to Linux. I chose Ubuntu and now I regret it because Gnome seems to be terribly unstable.
We did nothing fancy, we installed 5.04 from an original CD and then did an update after it was all installed. 
The problem is that *every* time we start Gnome the applets in the bottom panel crash and a window pops up to ask if we want to restart them. This is very boring and just should not happen.
The main offenders are: 
Desktop switchers
Window List
And once or twice, in the top panel, the clock.

I have removed the bottom panel, re-added it and then re-added the applets to it, but they still crash on the next reboot.
Has anyone got some idea? I have posted a bug about this to bugzilla.

---

### Post by oddflux on 2005-10-14
I've had a similar problem, it was when the drivers to my computer wern't installed and I messed around with some of the RAM on my computer.
I advise you to check everything is stable, installed and set. First. Do  a fresh reinstall of ubuntu, if all fails grab a technician.

---

### Post by pestilence4hr on 2005-10-14
I've had similar problems, it seems some of the configuration files are not compatible across upgrades.  I think your solution (assuming you haven't done *anything* to customize your installation, i.e. this is a fresh install with clean home directories) is to do [COLOR="Red"][WARNING: YOU WILL LOSE SETTINGS BY ISSUING THESE COMMANDS, PROCEED ONLY IF YOU ARE SURE YOU WANT TO LOSE THEM!][/COLOR]:

```

rm -rf ~/.gconf*
rm -rf ~/.gnome*

```

This should wipe you back to a state that a new breezy user would be in.

In addition to doing this, I had to kill gconfd and gnome-panel:

```

killall gconfd-2
killall gnome-panel

```

After logging out and logging back in, it was fixed.

Edit:  after I realized what forum this was in, perhaps you are not having the same problem.  I would also suggest a "sudo apt-get update && sudo apt-get install -f"...  perhaps your update did not complete.

---

### Post by Bigglez on 2005-10-15
Well - I had trouble with a Kubuntu install due to bad RAM (on another machine), so you make a good point (Oddflux), the only confusion being that the machine dual-boots (from hda, Linux is on hdb) Windows XP Home and that works just fine.
Is Linux more "sensitive" to bad RAM for some reason?

(Pestilence)
When I say "update" I mean that we let Synaptic do the stuff it felt it had to do. I don't think we upgraded to Breezy in any way. 
I will try the re-update you suggest.

---

### Post by Servus on 2005-11-23
I had the same problem with gnome-panel. It crashed every time I logged in… the only solution was to delete the .recentlyused files. Try!
servus

---

### Post by patrickledingham on 2008-06-13
Ive had similar problems and mate, pestilence4hr, you are a legend, this worked perfectly

Cheers

---

