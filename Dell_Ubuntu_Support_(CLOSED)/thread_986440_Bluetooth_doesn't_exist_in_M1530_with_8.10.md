---
title: "Bluetooth doesn't exist in M1530 with 8.10"
date: 2008-11-18
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Jracing on 2008-11-18
Hi all!

Despite I'm very surprised with the big performance of the intrepid ibex on my XPS M1530, I can't use his bluetooth features, because there isn't any bluetooth device (Obviously it has a bluetooth module that works perfect on windows vista).
What can I do to get it working? I'm LOST in this issue, but it's a necessary step to my final migration windows to GNU/LINUX...

Many thanks in advance.

---

### Post by superm1 on 2008-11-18
There's three solutions to try in this order:

1) Make sure the setting in the BIOS for switch control is enabled.  Also make sure that it's flipped on *while you boot up*.  In vista it might work without the switch, but you'll need to turn it on for linux.

2) Try this command:

sudo dellWirelessCtl --sw_bt 1 --bt 1

3) Try turning it on in vista and restarting.

---

