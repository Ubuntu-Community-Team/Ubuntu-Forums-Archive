---
title: "Windows as default OS in grub"
date: 2006-09-25
forum: Desktop Environments
---

### Post by SirOracle on 2006-09-25
Hi
I dual-boot Windows XP and Ubuntu, but since I have problem getting my wlan-card (D-link DWL-G650) to work as it should, I mostly use Windows XP (until I get the wlan-card to work). Therefore I want GRUB to choose Windows XP as default.

I found this guide:
[http://ubuntuguide.org/wiki/Dapper#How_to_change_default_Operating_System_boot-up_for_GRUB_menu](http://ubuntuguide.org/wiki/Dapper#How_to_change_default_Operating_System_boot-up_for_GRUB_menu)
But I must admit that I dont understand what they mean. I did try to change the 'default 0' line to 'default X_sequence', although I cant understand why it should work. But as I guessed nothing changed.

Can someone please explain to me what they mean, or tell me how I can do this.

---

### Post by Henry Rayker on 2006-09-25
they were using X_sequence as a variable. If you could paste the contents of your menu.lst, maybe i can get this up and working for you :)

---

### Post by andypaxo on 2006-09-25
Yep, Henry is right - just to clarify...
The guide means for you to type a number in place of 'X_sequence'. So if Windows is the 5th on your list it would be 'default 4'.
(This is because the numbering starts at 0)

Hope this helps

---

### Post by SirOracle on 2006-09-26
Ahh, thanks, now it works.
I did try this some time ago, but nothing happened. Perhaps I started counting from 1, and counted 'out of bounds', then it defaults to the first.

But again, thanks guys!

---

### Post by Zeedok on 2006-11-02
I can't seem to find the line:

default 0

Therefore I can't edit it appropriately. I think I've opened the right file. Is it possible the file has changed in Edgy?

Will post my actual file here tonight.

---

### Post by Herman on 2006-11-03
Zeedok, [click here]("http://users.bigpond.net.au/hermanzone/p15.htm#osprefernc") to see where the 'default' line is in your /boot/grub/menu.lst file.

A simpler and better way is to edit the line from 'default 0' to 'default saved', then Grub will remember the last operating system you booted and boot that one again by default.
That way is better because when you receive a kernel update and your list changes you won't have to edit your menu.lst file right away.
...Unless you also edit your 'howmany=' line to '1', [click here]("http://users.bigpond.net.au/hermanzone/p15.htm#_howmanyall") to see what I mean by that. Then your OS preference number will stay the same, plus your grub menu won't get full of extra lines of ugly text you are never likely to need anyway.

;)  Regards, Herman

---

