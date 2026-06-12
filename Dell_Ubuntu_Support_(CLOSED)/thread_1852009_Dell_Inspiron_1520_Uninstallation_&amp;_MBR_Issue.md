---
title: "Dell Inspiron 1520: Uninstallation &amp; MBR Issue"
date: 2011-09-29
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Mihael Keehl on 2011-09-29
Basically, I followed this guide on uninstalling Linux 11.04 but here's a short version:

[LIST=1]
[*]Deleted Linux Partitions in Windows 7
[*]Popped in Windows 7 Upgrade Disk (Recovery Options)
[*]Went to the Command Prompt and typed the following things in:
[LIST=1][*]bootrec /fixmbr
[*]bootrec /fixboot [COLOR="Red"]**(DID NOT WORK)**[/COLOR]
[*]It gave me an error stating "The volume does not contain a recognizable filesystem. etc.."[/LIST]
[/LIST]

And now it always takes me to some MemoryTest program, something I noticed that was one of the options when I was using the Grub (Purple) but I never paid any attention to it.

Afterwards, I decided to use the command prompt to figure out what was going on. I was able to jump into DISKPART and I've attached what I have at the moment, perhaps someone more knowledgeable than me can actually help me out.

---

