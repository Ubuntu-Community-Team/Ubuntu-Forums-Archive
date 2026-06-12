---
title: "CD drive glitches"
date: 2006-02-03
forum: Desktop Environments
---

### Post by seakiwi on 2006-02-03
Hi

Can someone please tell me how the heck to set things up so that my CD drive will work consistently. This is driving me totally nuts!

The other day I had things working fine for playing audio CDs. I have KsCD set as my default player and when I inserted an audio CD it would start KsCD automatically and play.

Today when I went to play one I got errors about KDE mediamanager not running and nothing would play. There are a couple of things I don't understand ...

Under my / directory I have an entry for  *cdrom* (listed in italics in that directory). If I click on that there is nothing in the folder.  Under /media I have entries for cdrom and cdrom0 (no italics) Both of those folders are empty too. In the past my CD drive has shown up under at least one of those folders (cant remember which one right now).

I was under the impression that the lastest version of KDE auto mounted the CD drive so that one didn't have to ever mount it manually. Was I dreaming that? All I want to be able to do is stick a CD in the drive and have it automatically open/play in KsCD.  What do I need to make that happen? I would have though setting KsCD as my default player would have achieved this, but it seems not.

The other thing I can't seem to alter is that when I insert the CD - firstly I get a dialogue box asking me what I want to do with it - I've already told this box a zillion times that I want it to play CDs with KsCD and to please remember that for all audio CDs.  Then I get Konqueror opening to the media directory with an executable file and an uninstall file in it. Why does Konqueror always open like that and how can I stop it from doing that?

Sorry for all the questions but this is making me nuts. How can it be so complicated to simply play an audio CD and have it remember what you told it to for the next time you play one? What the heck am I "missing" here? :-|

---

### Post by chandra on 2006-02-05
I think this may be a KDE bug and I have filed a bug report at KDE:

Bug 121405 - KsCD stops randomly while playing a track
[http://bugs.kde.org/show_bug.cgi?id=121405](http://bugs.kde.org/show_bug.cgi?id=121405)

You may wish to vote for this bug so that it gets a higher priority for solution.

Thanks.

---

### Post by seakiwi on 2006-02-05
[QUOTE=chandra]I think this may be a KDE bug and I have filed a bug report at KDE:

Bug 121405 - KsCD stops randomly while playing a track
[http://bugs.kde.org/show_bug.cgi?id=121405](http://bugs.kde.org/show_bug.cgi?id=121405)

You may wish to vote for this bug so that it gets a higher priority for solution.

Thanks.[/QUOTE]

Actually I think maybe you mis-read my post as your bug doesn't describe my problem. My problem is that I can't play CDs at all - not in any player, so it's obviously not a KsCD problem.

Thanks anyway and I hope they fix your bug for you!

---

### Post by Neo Ex on 2006-02-05
To access your audio CD you don't have to go in /media/cdrom0, but you have to write 'audiocd:/' in Konqueror.
For make KsCD always play an audio CD when you instert it, try KControl -> 
Devices -> Media storage -> Audio CD.
Now you are still unable to play audio CDs? Also if you reboot?
If KsCD doesn't work, try Kaffeine or amaroK (yes, I know KsCD is better, but if it doesn't work... reinstalling the whole OS just for the audio CDs is not the best solution, I think...).

---

### Post by vivedekananda on 2006-03-21
I also had a problem (after some accidental kde reinstallation) that "kmediamanager was not running" and no automount. The reason was that kded was not running, I started it manually and everything works fine again, hopefully it will work after reboot.

I any case I would try looking to kcontrol->kde components->service manager; that the configuration of kde control manager I guess.

---

### Post by sdr_ar on 2006-03-27
I can add that activating the check box "Using Direct Digital Playing" in KsCD almost mends the problem at all. The cuts continue existing, but the cd doesn't stop at all, they present as a very short interruption. I tried this with DMA activated.

---

