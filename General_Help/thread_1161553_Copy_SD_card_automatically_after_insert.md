---
title: "Copy SD card automatically after insert"
date: 2009-05-16
forum: General Help
---

### Post by Xyphoid on 2009-05-16
Hya,

I'm working on a photoframe made of an old laptop. I installed Ubuntu.
How can I copy an SD card automatically after insert?

I have a USB cardreader. If I insert a card then it gets mounted ok. But the mount point keeps changing to the name of the card. So if a card is called "card" the mountpoint will be /media/card and if its called "MSC" the mountpoint is /media/MSC.

I think the reader is /dev/sdb and the slot where I insert the card in is /dev/sdb1

---

### Post by Xyphoid on 2009-05-19
I found a solution. Well, a half solution really.

I made a new rule in **/etc/udev/rules.d/81-local.rules**

The rule looks like this:
[I]ACTION=="add", KERNEL=="sd*", RUN+="/usr/bin/startpicframe.sh"
[/I]

This is my startpicframe.sh:
[I]#!/bin/bash

killall feh unclutter

feh -zZFr -D 10 /media
unclutter

echo "Test" >> /tmp/log.txt[/I]

**/tmp/log.txt** is being filled with "Test" when I insert a SD card in my
USB cardreader. But feh is not running. What am I missing here???
When I execute startpicframe.sh from the commandline, feh is starting normal.

---

