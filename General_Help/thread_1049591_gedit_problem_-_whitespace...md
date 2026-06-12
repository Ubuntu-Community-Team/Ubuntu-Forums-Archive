---
title: "gedit problem - whitespace.."
date: 2009-01-24
forum: General Help
---

### Post by tiger.woods on 2009-01-24
This is a fresh install of 8.10 and when I try to open a text file with gedit the application comes back blank and won't open the file.

The files Im trying to open are .conf files or text files. Is this a know issue or is something else going on here?

I've attached a print screen of my xorg.conf as an example..

Strangley enough gedit will work a couple of times after a reboot and then stop...

TIA

TW,

---

### Post by cmnorton on 2009-01-25
Can you create, save, and re-read any file, like temp.txt in your home directory?

What happens if you go to an X-term (terminal), and enter:

vi temp.txt
Press the "i" key.
Enter some words.
Press ESC.
Press the colon key (':') followed by x
to save and quit.

Try reading this file with gedit.

Offhand, this sounds like graphics. 

I would also look in your logs:

sudo tail /var/log/syslog
sudo tail /var/log/messages

right after using gedit.

---

### Post by tiger.woods on 2009-01-25
I just installed an updated driver for NVIDIA and you might be right the problems seems to have gone away at the moment... I'll post back if it comes back.

Thanks,

---

