---
title: "Screensaver causing system lockup"
date: 2009-05-20
forum: General Help
---

### Post by Zelandeth on 2009-05-20
Running Hardy here, which by and large has run like a charm since the day it was installed.

There have however been one or two gremlins, one of which is infrequent enough in its appearance I ignore it, but one which does bug me...especially as it makes browsing through the screensavers installed like playing Russian Roulette.

One would think that if screensavers were going to cause problems - it'd be the fancy 3D/OpenGL based ones.  No, they all seem to behave.  Freezeups seem to more often than not be caused by the simple vector graphic based ones "vermiculate" being one which more often than not seems to cause an instant lockup...which made selecting another screensaver a bit of a challenge, as it remembers what's selected.  After a certain amount of headscratching, I moved the file out of /usr/lib/xscreensavers/ and that made it jump to the next option, one which thankfully doesn't freeze.  In the meantime, I've learned my lesson and gone back to GLMatrix which behaves itself.

Reason I'd really like to see a solution to this is that one of the other screensavers (sorry, can't remember which one off the top of my head, and I dare not go poking around there again right now!) was one I quite liked, but it often would hang after a period of time from a minute to 24 hours plus.

To begin with when it hangs the keyboard is still responsive, but after a few seconds that usually ceases.  Mouse can still be moved normally.  There's no notable increase in CPU temperature accopanying the freezup to incicate something hogging all the CPU time.  Music if playing at the time will continue completely unaffected.

When this happens, a hard reset is required to restore any sense of sanity - I've only discovered the REISUB trick in the last half hour or so, so haven't had a chance to apply it to this problem as yet - will give that a try next time.

Hardware's listed below for reference.


> Gigabyte GA-M52S-S3P
> AMD Athlon 64 X2 5000+
> 4Gb DDR2 800 memory.
> GeForce 8500GT 512Mb PCI-e.
> Hitachi DeskStar 750Gb SATA-II Harddrive.
> Hitachi DeskStar 60Gb PATA Harddrive running through a garden variety SATA/PATA adaptor.
> El-cheapo USB mouse I really need to replace
> Apple Extended II Keyboard running via Griffin iMate ADB-USB adaptor.
> Garden variety 3.5" floppy, 5.25" floppy, CD-RW and DVD-ROM drives.

This seems to be limited entirely to the screensavers, video playback and such don't produce any such problems.

Any ideas?

---

### Post by Benboom on 2009-05-20
I have had exactly the same problem you describe, but my machine is an old Mac G4 PPC machine running Jaunty. It worked fine at first but after the system had been running for a few days all the symptoms you describe started. I ended up setting the screensaver to NEVER after having problems with various different modules. Since it worked fine when I first installed Jaunty I assume there is a conflict with something I've added since then but I have no idea what it might be.

---

### Post by Zelandeth on 2009-05-20
Pretty sure that this problem has been here since install, thanks for the insight there though.

The modules which do work fine seem to work absolutely fine - have been using GLMatrix for instance since a couple of weeks after Hardy went mainsteam, and it's never hung up on me.

Just the modules that do hang up...well, do!

---

### Post by hansdown on 2009-05-20
Hi Zelandeth.

I've had the exact experiences with the screensavers in hardy.

Like you said, it's best to steer clear of the ones that you know

are a problem.

The REISUB command seems to work for these. 

There are lots of bug reports concerning the screensavers.

It never crossed my mind to edit those files. Thanks for that.

Some reading.

[http://www.google.ca/search?q=screensaver+problems+in+ubuntu+8.04&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.ca/search?q=screensaver+problems+in+ubuntu+8.04&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

---

### Post by Zelandeth on 2009-05-21
Well, taking chunks out of /usr/lib/xscreensavers was a bit of a gamble - randomly deleting files is generally a Very Bad Idea (TM) in my opinion - hence I moved it, rather than deleted it.  That way if the very worst came to the worst, I'd have been able to stick it back again.

Seems from one of the other posts that you can get around a module crashing the screensaver switching app by editing the associated prefs file (.gconf/apps/gnome-screensaver/%gconf.xml) to point to one that you know works.  From what I've seen though removing them doesn't seem to cause any ill effects.

If anyone would be interested - and I can find the patience to do it - I could scan through and make a "blacklist" of the modules which hang my system, if they seem to be common to other peoples experiences, at least we might be able to save some folks some hassle.

---

### Post by hansdown on 2009-05-21
I could offer to help. I see 80 screensavers in the default install.

I'm not using compiz, or anything special.

---

### Post by Zelandeth on 2009-05-22
Crikey, this might take me a while.

I've got the additional screensaver packages installed on here which means that there are 245 (only counted once!) to chose from.  

It's made harder by the fact that I know that at least one of these things doesn't always hang within a couple of seconds...Hmm...will spend a bit of time on it just now, and see what I find.

Worth noting as well that it's the 64-bit version of Hardy I'm running here, in case that's likely to be a contributing factor.

---

### Post by hansdown on 2009-05-22
Ive been going through the list.

All was good 'til antspotlight. While still in the preferences window,

mouse cursor was "jittery". Screensaver moved super slow.

---

### Post by Zelandeth on 2009-05-22
Right, had a quick scan through earlier this evening.

The following are those which caused trouble.

Braid: Instant soft lockup.  Was still able to open up a new terminal session and restart X however.

IMS Map didn't actually hang the system, but made it grind to all but a complete standstill when running.

Interaggregate - Had to resort to REISUB to get out of that one.

Slip, as with IMS Map, doesn't actually hang the system, but pulls about 99% of my CPU time without actually doing anything.

Substrate - Which is the one I want to actually USE, hangs up after it's been running for a while - sometimes.

Whirlwindwarp - Instant crash.

Zoom - As with IMS Map, pulls loads of resources, but doesn't actually do anything.

These are only those which did things pretty much instantly, Substrate for example I know will often happily work for an hour or so before it falls over.  Other times - as with this evening, it rolls over dead after only a few seconds.  I love erratic faults!

Hansdown, from memory, Antspotlight's one of the more graphically demanding screensavers in the basic list - possibly a problem with your 3D card's drivers?

Most of the really demanding ones here run okay (despite all of Compiz' eye-candy being switched on), some of those which decide to drop over dead are really rather simple in comparison!

---

### Post by CatKiller on 2009-05-22
gnome-screensaver is, in my opinion, a mess. When it was first introduced there was a huge backlash against it because there were some really fundamental things that xscreensaver could do that gnome-screensaver didn't (like being able to select which screensavers would be used, or change the parameters of the existing screensavers), and the dev just marked the bug reports as wontfix.

One solution, which was widely used at the time, was to uninstall gnome-screensaver and just use xscreensaver instead.

Another that I used, until gnome-screensaver bugged me by initiating the screensaver when I was playing fullscreen games, was to manually edit out the ones that were problematic in gconf-editor. The list of which screensavers get used is stored at /apps/gnome-screensaver/themes. You can just take out the ones that you don't want to see and still have a selection, but if you start the Screensaver Preferences tool this list will be re-populated, so it's probably worth exporting the values of this key when you've got a selection that you're happy with, just in case.

Because of the decision to strip this function out of gnome-screensaver, you can't actually look at the screensavers when you're selecting them for this list. I seem to recall that if you have both gnome-screensaver and xscreensaver installed you can get xscreensaver to display a specified screensaver from the command line. It's been a long time since I used a screensaver, though, so I can't remember exactly what it was. It's a pity, because I used to really like the screensavers.

---

### Post by hansdown on 2009-05-22
Zelandeth and CatKiller,

You guys are awesome. I never really worried about screensavers, because

I didn't use them much. GLMATRIX is pretty good for impressing my microsoft

using buddies, along with hovering the cursor over music files to make them 

play.

---

### Post by calla2 on 2010-02-21
Newbie here
     Got the same problem with screensaver. I was checkin out the selection and got to the one that is named Molecule, the demo came up and showed making molecules. Now when I go to that screen it freezes the system except the mouse. Same no it locks on that screensaver and lock up.
     Any luck with your problems
:confused:

---

