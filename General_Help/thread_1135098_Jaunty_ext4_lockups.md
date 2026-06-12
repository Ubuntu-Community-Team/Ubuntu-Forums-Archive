---
title: "Jaunty ext4 lockups"
date: 2009-04-24
forum: General Help
---

### Post by hellfeuer on 2009-04-24
The release notes for Jaunty mention the possibility of soft lockups when deleting files. But from the launchpad bug it appears that it only happens to some people. My question is - how common is this bug in practice? There's some indication that the lockups might be more likely on nearly full hard drives. Anyone with nearly full drives who *hasn't* been affected? (I ask because I almost always have a nearly full drive)


Of course I could try it out for myself, but installing Jaunty, testing and then possibly reinstalling is painful (and unreliable) so I thought I'd ask here first :P

I really want to try out ext4 and this is the only thing holding me back.

---

### Post by ubu-for on 2009-04-24
I had one lockup within eight weeks because I've moved two folders.

---

### Post by Arup on 2009-04-24
None so far on my system.

---

### Post by Ravernomina on 2009-04-24
really their is more good then bad..... Great system proformance over a little FS lock up when emptying trash hey what comes good their has to be some bad No?

---

### Post by benmoran on 2009-04-24
I've had two lockups in 2 days since installing Jaunty with ext4. I don't think they are related to this bug, since the second one happened when I was switching programs. No drive access as far as I know. My drive is pretty full though.

---

### Post by Glugglug on 2009-04-24
Have I done it wrong  when I partitioned my hard disc to install jaunty I used ext3:redface:

---

### Post by cysn06 on 2009-04-26
As far as I have seen the lockups are associated with heavy disk I/O. Cut and pasting files. Anything that involves frequent deletions when there is a heavy load on the disk

I get very very frequent lockups when using KLIBIDO. This usenet client creates many little files that it downloads, then combines them later, deleting the old files in bulk. Hellanzb does the samy thing, but I get MUCH less lockups.

Investigating the difference in how klibido and hellanzb handles io operations could help pinpoint the cause of this problem.

I was just cut and pasting a large amount of data, and i had an other lockup, and lost a lot of files, im moving back to xfs+ext3, althou I really enjoyed the fast boot times :S. Hopefully this can be resolved soon. Im not sure if its a deadlock or what.

---

### Post by andyhumphries on 2009-04-26
> **Glugglug said:**
> Have I done it wrong  when I partitioned my hard disc to install jaunty I used ext3:redface:

This isn't wrong at all, ext3 is still a tried and tested, stable filesystem with good performance. If you're asking this question, I wouldn't worry about too much about ext4 yet. :)

I've not used ext4 yet myself, going to wait until its a little more stable and I've read more into it.

---

### Post by iMerlin on 2009-05-03
I've just reinstalled Ubuntu on my machine with ext4, because I wanted to try it. My computer has locked up three times in 2 days; mostly with high disk i/o but sometimes just out of the blue.

The machine was perfectly stable before (with 8.10 x64 reiserfs), syslog reveals nothing.

---

### Post by drezha on 2009-05-11
Suffering fairly frequent lockups.

All I'm doing is using Opera, with maybe Pidgin and Rhythmbox playing and Mediatomb in the background.

As it appears to be common, looks like a reinstall onto ext3. ext4 seems nice but I cant afford the lock ups.

---

### Post by slashdotfx on 2009-05-24
past couple of weeks, I got report of system I've install
got locked up frequently, I dunno what makes it lock up.
just about couple of minutes a go, I was deleting a directory
which holds 1.5Gb of files and folders, and suddenly system freeze
happen. at that moment my system is quite loaded with users
(it's a ltsp server).

they said it fixed in 2.6.30, but something about how ltsp
system depends on some compression algorithm not yet included
in kernel above 2.6.28 makes my kernel upgrade impossible at
the moment... :(

I guess the choice is reverting back to ext3...

---

### Post by fillintheblanks on 2009-05-24
occasional lockups when building software from sources like wine

or doing svn update..

---

### Post by slashdotfx on 2009-05-24
now I've successfully upgraded my jaunty to 2.6.30rc7
from the PPA builds, running ok, will report soon if
the crash and data corruption occurs.

---

### Post by ginjabunny on 2009-05-25
I have 2 Jaunty PCs, one at work the other at home, both have had quite a few lockups.
Just installed Mint 7 today on my laptop and have had 2 lockups already.

I think I may go back to ext3 and wait until ext4 is more stable.

---

### Post by rumplestilts on 2009-05-25
I've had a lockup every time I've let the system sit for a period of time. I'm running on an Acer Aspire 3070z with an ext4 main partition.

However, I think I found a solution (in my case, anyway): I set the Power settings to *never* let the screen go into its sleep/blank mode and restarted. I then let the system remain on overnight unattended while my Mac was logged into one of the Acer's shared folders (via smb). No lockup.

I should note that, in spite of the setting, the screen still goes blank after a period of time but dragging along the touchpad or hitting a key brings the screen up again, and the lockups seem to have gone. I'll watch for this post again in a week or so.

---

### Post by utkjamie on 2009-05-26
> **slashdotfx said:**
> now I've successfully upgraded my jaunty to 2.6.30rc7
from the PPA builds, running ok, will report soon if
the crash and data corruption occurs.

Which repository are you using?

---

### Post by mkvnmtr on 2009-05-26
I reinstalled one system to ext3 using a  minimal install. Really like the system with no problems. The other system still has a few lockups and I had problems with Thunderbird. Moved Thunderbird to the other system and no problems. I will shortly replace ext4 on the second system. I think I will use a minimal install again. It just seems more stable if it doesn't have a lot of stuff I don;t use.

---

### Post by Soul-Sing on 2009-05-26
so far so good here....

---

### Post by Seventh Reign on 2009-08-01
Forget the stupid paper cuts .. somebody FIX THIS!!!

200+ lock ups and counting since April

---

### Post by okubax on 2009-08-10
> **Seventh Reign said:**
> Forget the stupid paper cuts .. somebody FIX THIS!!!

200+ lock ups and counting since April


I second that !

---

### Post by Post Monkeh on 2009-08-10
i reinstalled to an ext4 / partition 2 or 3 weeks ago, and haven't had any lock ups.

my home partition was ext3 but i converted it yesterday and have had no problems as of yet.

---

