---
title: "Problems with CF card as OS drive"
date: 2009-03-27
forum: General Help
---

### Post by Esvandiary on 2009-03-27
Apologies if this is a known problem; it's not the easiest thing to search for, although I did have a good go.

Basically, I've had a fileserver running on Intrepid (originally Hardy, upgraded) for about the last 8 months. Originally the OS was on an IDE hard disk, which had problems. However, the partition with the OS on was intact and I copied all the files off it onto a CompactFlash card on EXT3, which is now what's running the OS via a CF-to-IDE converter.

It's been running for a few days, and everything was fine - I had one or two problems, the sudo binary no longer being setuid etc, but once I sorted those out it was all settled down and working.

Then, samba started playing up, I couldn't sudo (it segfaulted no matter what), and su wouldn't work either.
I soon realised that I had no disk access to anything on the CF card (even ls just generated a bunch of Input/output errors), and no way to do anything about it.
Once restarted, the OS is completely back to normal. The suggestion to just reboot came from a friend who experienced the same situation, on a USB hard disk, on an Intrepid box upgraded from Hardy. (I was happy to accept it was just my "special" installation up until that point).

Since the OS was only running for a few days (with no major drive activity to the card in that time), I can only assume this could happen again at any time, leaving me with no way to do anything about it unless I have physical access (or run sysrqd, which I don't particularly want to do).

Is this a known problem (rather than just me being stupid), and if so, is there a way to work around it?

Thanks in advance,
Andy

---

