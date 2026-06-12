---
title: "Questions on Synce"
date: 2009-03-11
forum: General Help
---

### Post by yankeeDDL on 2009-03-11
Hello,

I have a Dell Axim (Windows CE 6.0) and trying to see if it's of any use for me to install Synce.
I'm getting there after following countless treads and guides, but it occurred to me reading this one: 
[http://ubuntuforums.org/showthread.php?t=136257](http://ubuntuforums.org/showthread.php?t=136257)
that Synce can be used only for Backup and remote file manipulation.

If that's the case, then it seems quite useless. I mean, if you just need to do a backup and manipulate files, just plug in the SD card in a USB card reader.
The huge benefit of syncing in Windows, once you figure out how to use the worst program ever written: ActiveSync, is that you can SYNC the data between a PC and the PDA. Sync means that if newer data is on the PC, then it gets updated on the PDA. Typical example: calendar. If I enter something on my PDA I want the calendar on the PC to be sync'd so I get a reminder also from the PC (and viceversa).
Now, I do realize that (luckily) we don't have Outlook on Linux, so I was expecting that Synce would provide the files in an editable form so I can update them from the PC if I want to (for example, adding contacts via a text editor, or something like that).

Am I missing something?

One might ask: why don;t you use Activesync in a VirtualBox? Actually, I've tried, but miserably failed. It took me a long time to get USB working in the VirtualBox. I know it does (I can print), but for the life of me I cannot get ActiveSync to "see" the Axim.
Perhaps is because my CPU does not support virtualization (there are all sort of limitations documented on Virtualbox's forum, including your insane CPU usage for no reason at all). In any case, Either I dual boot in "Wintendo" or I need to use Synce.

Thoughts?

---

### Post by yankeeDDL on 2009-03-12
Anybody?

---

### Post by wildman4god on 2009-03-12
try this:

[http://www.ubuntugeek.com/pocket-pc-syncing-with-evolution-in-ubuntu.html](http://www.ubuntugeek.com/pocket-pc-syncing-with-evolution-in-ubuntu.html)

I know its a little old, but it should still work.

---

### Post by yankeeDDL on 2009-03-15
> **wildman4god said:**
> try this:

[http://www.ubuntugeek.com/pocket-pc-syncing-with-evolution-in-ubuntu.html](http://www.ubuntugeek.com/pocket-pc-syncing-with-evolution-in-ubuntu.html)

I know its a little old, but it should still work.

Alright. I got synce to work with my Axim x51v (win Ce 6.0)
Some remarks, just for the records:
1) Synce can sync only with Evolution (I was using Thunderbird). EVO is nice, but I would have preferred to stick to TB for several reasons. I do see that EVO is more complete, but TB has other advantages in my case.
2) I cannot sync the notes. Synce and the plugins seem to support note syncing ... but it just ain't happening.
3) Getting Synce to work is easier than it seems. Nice, for something so ... experimental, at least according to Synce and Opensync websites :)
4) To answer my own question above ... it's _not_ true that SynCe is only good for backup. Synce+Evolution works (almost) as well as Activesync and Outlook.

---

