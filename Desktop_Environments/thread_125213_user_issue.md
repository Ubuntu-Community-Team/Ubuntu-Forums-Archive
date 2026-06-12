---
title: "user issue"
date: 2006-02-03
forum: Desktop Environments
---

### Post by chollenbeak on 2006-02-03
I just upgraded from hoary to breezy.  During the upgrade I lost the ability to sudo.  In addition, I can't open a root terminal.  Can someone tell me how I can log in as root so I can change my user settings?

---

### Post by rjwood on 2006-02-03
LOL---your kidding---right?????

---

### Post by carlosqueso on 2006-02-03
When you GRUB comes up, choose to boot into recovery mode.  This will make you root and able to do anything you want (kinda scares me that that is the case, but I guess it makes sense).  Then you can use visudo and edit your sudoers file, or add yourself to the admin group.  Good luck.

---

### Post by Mustard on 2006-02-03
[QUOTE=carlosqueso]When you GRUB comes up, choose to boot into recovery mode.  This will make you root and able to do anything you want (kinda scares me that that is the case, but I guess it makes sense).  Then you can use visudo and edit your sudoers file, or add yourself to the admin group.  Good luck.[/QUOTE]

It is a security issue, but GRUB also comes with the option to have a password on it.

---

### Post by 504harry on 2006-02-03
[QUOTE=chollenbeak]I just upgraded from hoary to breezy.  During the upgrade I lost the ability to sudo.  In addition, I can't open a root terminal.  Can someone tell me how I can log in as root so I can change my user settings?[/QUOTE]
/
General comment:
I'm surprised you managed to get that far.
When I received Breezy-CD's it is well-nigh impossible to work out what you need to do (to update) - do I shove 'em in and hope? 
[[They appear to assume that this is your first install - it could have an option "You can update an earlier version" - but I wonder why this isn't done over the internet - Ubuntu supplies a simple CD to set-up a working system, then you update the applications you need (or have space for!). This would reduce costs no end. i.e. the CD is a loader/taster a bit like the "live" but allows the HDD to be ready to accept downloads.]]

No, it seems. - as it will try to reformat the HDD as it doesn't like to keep the partitions as they were (so it says)...
- Just how many different scenarios are there?
1) update with the same partitions
2) update moving the partitions/ create a Data area
3) Update to separate HDD (ie leaving existing OS intact)
4) update afresh leaviing only data files
5) fresh install clearing the whole HDD
6) fresh install leaving some partition(s) for Windows.
-yet the option list presented is like a take-off schedule for a Mars mission.
=Hugely confusing. 
Why no Partition graphical interface? Primary colours for "existing partitions" pale colours for "Is this your choice?" with winking sectors showiing deleted areas and ripling-areas showing retained files.....by clickiing on a partition it will tell you what is there/proposed....

Today I tried to read the Instructions both  "pre-release" and stable - these I can't read - parts of the text is minute - why?
(Google is a decent size, easy to navigate etc) - but these instructions are a real pain - the information is 100% I'm sure, but it keeps jumping about so you end up wanting to tear-up TFM. 

At least, I would like my Ubuntu to work as well as Win98SE.
It doesn't - because there is no Java in Firefox - easy enough to up-date you'd think - but don't even think of it. My Ububtu has be installed four weeks and still Java is a source of wonderment - so I'm back to Win98SE - it just does the business.
It would be nice to have .PDF (acrobat)...ditto agro...
No! I don't want Flash (and probably not pdf of it is coupled to flash, now Adobe owns both.).
Realplayer would be nice also.
/
Why are thse semi-essentials so difficult?  I read that I have to fiddle with sources.list, synaptic, (or an easier one, that needs synaptic anyway) and grief upon grief. It's like sitting an exam to get into the Inteligence Corps....all I want to do is use the PC and save a few files, photos etc. Printing would be nice, but I resolved to using my Lexmark printer under Win98SE.
/
If I need  extra programs/repositories, why cant they be clicked-on - "Click here for essential plug-in menu" ?  - - - Too darn easy huh?
- Ubuntu should run a wizzard prompt - "When you are on Java.com site, ...look for the file xxxxx click on it to download, after you agree their terms......"
The Java website is a nightmare in itself and when you download whatever Sun suggest it just sits there - no self-extraction that I could work.
/
However, It really has come a long way from 10 years ago 
my modem installs itself,
USB is just "there".... but Win98se still has it beat.
Harry
PS twice this session it tells me I'm not logged in  - why does it say I am and then argue about it?

---

### Post by chollenbeak on 2006-02-03
Just wanted to say thanks, carlosqueso, for your patience with such a noob issue.  I'm up and running.  And rjwood, your spelling is as advanced as my linux skills.

---

