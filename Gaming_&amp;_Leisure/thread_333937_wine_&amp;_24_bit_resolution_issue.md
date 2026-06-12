---
title: "wine &amp; 24 bit resolution issue"
date: 2007-01-08
forum: Gaming &amp; Leisure
---

### Post by Totzo on 2007-01-08
Hi,

I've just been trying to run an old game on wine which requires very little in the way of graphics processing but fails to run in 24 bit mode. It complains about needing either 16 bit or 32 bit screen depth. I ran it on 16 bit and it worked fine but I don't want to have to change to this every time I run it. (editing xorg.conf and restarting x is a bit of a hassle, no pun intended)

From what I understand, 24 bit is the same as 32 bit under windows so is there a way to trick wine into recognising this? Thanks in advance.

PS. Is there a wine specific forum anywhere, I couldn't find one at winehq.com?

edit:
if anyone else is interested check [this]("http://appdb.winehq.org/appview.php?iVersionId=5137") out

---

### Post by Enverex on 2007-01-10
Bit-depth messages are merely warnings, they wont prevent a game from running or working, it just tells you that as Wine is rather verbose with it still being under very heavy development. The issue causing it to crash or break will be something else (well, I should say "shouldn't" heh). I'd try with Wine 0.9.29 and see if that helps, lots has been re-written. Paste on bugs.winehq.org with an output of the terminal messages attached.

---

