---
title: "root.disk not found. really."
date: 2009-01-08
forum: General Help
---

### Post by apcfreak on 2009-01-08
I've been using Wubi since last January sucessfully (a few hiccups here and there), but now, I think I might've lost all of my data. 
One night, I had to do a hard reboot because I had tried all of the key commands that I knew.
I booted up as usual next time, selected Ubuntu, got a busybox prompt. Thinking it was the usual, I rebooted into Windows, did chkdsk /r , and rebooted and it still gave me busybox. Same with the Recovery Mode. The error message was "root.disk does not exist". I can't find it in the usual folders, nor in a found.000 folder.

Could I get any help here? This is a year's amount of personal data.

Thanks.

---

### Post by Jammanuser on 2009-01-08
> **apcfreak said:**
> I've been using Wubi since last January sucessfully (a few hiccups here and there), but now, I think I might've lost all of my data. 
One night, I had to do a hard reboot because I had tried all of the key commands that I knew.
I booted up as usual next time, selected Ubuntu, got a busybox prompt. Thinking it was the usual, I rebooted into Windows, did chkdsk /r , and rebooted and it still gave me busybox. Same with the Recovery Mode. The error message was "root.disk does not exist". I can't find it in the usual folders, nor in a found.000 folder.

Could I get any help here? This is a year's amount of personal data.

Thanks.

This is one of the reasons why I chose to upgrade my Wubi install to a dedicated partition with LVPM. Now i no longer have such issues with Wubi, because I don't use it anymore! :P But seriously, if you lost your root.disk, its pretty much over...you will need to reinstall unfortunately. :( The root.disk is the most important part of a Wubi install, and if you lose it, you will always need to reinstall (unless of course you happened to back it up somewhere...which i will advise you to do next time, in case it happens again!), because its the Wubi equivalent of a real partition with Ubuntu installed on it, with all your files and data stored within the root.disk itself.

Sucks that you lost it, but unless someone else comes forward with a different solution, i guess you will have to reinstall Wubi. :(

Good luck, and i hope this helps.

-Jam man

:guitar:

---

### Post by x22 on 2009-01-08
maybe not so bad: you should find what partition scheme the HD uses,
and then use "mount" command to access them.

suggest "knoppix" or "cdrescue"--they boot frm CD, use ramdisk, not HD
once up, in a terminal: "fdisk /dev/hda" or sda or whatever: keep trying
'til you find it.

---

### Post by apcfreak on 2009-01-09
Jammanuser: Yep, that's pretty much what I've deducted. Weird feeling, losing *everything*. I was going to move it to a full install last summer, but for some reason or another, never got around to it. Oh well. Really needless to say, my next install will be partitioned, not to diss on Wubi (I used it for a year without any major problems, just a bad luck bug it seems), but I don't want to ever go through this again.

x22: I don't really understand what you mean. It looks like the space that i allotted to Wubi has been put back into Windows, so there shouldn't be much trace on the HDD. Could you please elaborate? 

All-in-all, this is just a really crappy experience, though not fully quite un-expected. Thanks guys for your posts.

---

### Post by Jammanuser on 2009-01-09
> **apcfreak said:**
> Jammanuser: Yep, that's pretty much what I've deducted. Weird feeling, losing *everything*. I was going to move it to a full install last summer, but for some reason or another, never got around to it. Oh well. Really needless to say, my next install will be partitioned, not to diss on Wubi (I used it for a year without any major problems, just a bad luck bug it seems), but I don't want to ever go through this again.

x22: I don't really understand what you mean. It looks like the space that i allotted to Wubi has been put back into Windows, so there shouldn't be much trace on the HDD. Could you please elaborate? 

All-in-all, this is just a really crappy experience, though not fully quite un-expected. Thanks guys for your posts.

*shakes head sadly* Sorry, man...i understand how it must feel for this to happen, really i do. :( I only wish there had been a a way to recover your root.disk, as i would have most certainly came forth with the solution...but unfortunately, AFAIK, there is no way to recover your root.disk once losing it...:(

As for what x22 wrote, i will let him answer for himself, but i think he was referring to mounting the root.disk with the LiveCD (if possible) and recovering your files that way...but anyhow, too late for that now, since according to this comment 

*[COLOR="Red"]It looks like the space that i allotted to Wubi has been put back into Windows, so there shouldn't be much trace on the HDD.[/COLOR]*

it sounds like you already fully removed the whole Ubuntu folder. And anyway, how could you possible mount your root.disk if it doesn't exist...? ;)

I am very sorry for your loss, and i wish there was something i could do...:( Next time, i would suggest (especially on a Wubi install, but even on a real install, as there's always a chance of something happening...) making sure to regularly backup all of your data to somewhere else than the computer that Wubi is installed on, so if you lose Wubi, you will still have all your files.

-Jam man

:guitar:

---

