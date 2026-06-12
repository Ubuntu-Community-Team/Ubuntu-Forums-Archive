---
title: "Drive configuration needs to be changed for dual boot"
date: 2010-03-29
forum: Dell Ubuntu Support (CLOSED)
---

### Post by waterlogged on 2010-03-29
Hi all, I'm not a total beginner with Linux, but I'm no where near advanced. I've searched around a decent amount and have yet to find an answer to my problem. If it is out there, I apologize for the double post.

I'm having a small, annoying problem with my new computer, a 64 bit Dell Studio. I'm attempting to dual boot Hardy with Windows 7, and pretty much everything is working very well, with one exception. Every time I need to boot Linux, I need to change the hard drive configuration from ATA to RAID. It doesn't seem like Hardy likes ATA. To make my life fun, Windows 7 doesn't like RAID, and will only boot in ATA. I've tried reinstalling both, but neither will install correctly unless the drive configuration is the one it likes.

Is there any way around this problem? Can I somehow setup grub to change BIOS configurations depending on the OS I select, or is there some other way around this?

Thanks all for the help, and I'll be watching closely in case there is anything necessary I didn't include.

---

### Post by gbrainin on 2010-03-29
Try adding the all_generic_ide switch to the menu.lst.  See: [http://en.community.dell.com/wikis/linux/ubuntu-8-04-known-issues.aspx]("http://en.community.dell.com/wikis/linux/ubuntu-8-04-known-issues.aspx")

---

### Post by waterlogged on 2010-03-29
[COLOR=Black]gbrainin - That worked perfectly, thank you very much.
[/COLOR]

---

