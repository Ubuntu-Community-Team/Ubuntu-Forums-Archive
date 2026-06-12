---
title: "Fixing laserjet 1020 not printing"
date: 2009-01-22
forum: General Help
---

### Post by Sprax on 2009-01-22
I thought this was worth a repost so people don't miss it since it's currently buried deep in a thread.

Credit to **markovg** for the solution

> HP lasterjet 1020 only working if turned on when Ubuntu starts
While simply plugging in my HP 1020 seemed to detect it and set it up fine. It did not respond to any print jobs, though CUPS showed the jobs as completed.

I was able to get my HP 1020 to print on xubuntu intrepid with the following process:

1) $ sudo apt-get install hplip-gui

2) Remove the printer via [http://localhost:631](http://localhost:631) or (xubuntu settings->printing)

3) Install the printer with
$ hp-setup

4) Run the HPLIP toolbox in Admin or Settings menu

5) Go to the actions tab for your printer and "Download Firmware"

The printer awoke, and would print test pages.

The HPLIP toolbox claims that "Download Firmware" is "required on some devices after each power-up".

Perhaps a firmware download would help to get your 1020 working if turned on after Ubuntu startup?

---

### Post by mdurham on 2009-03-02
Thanks for that Sprax, it now works on Intrepid amd64. I can't make it work on Jaunty though, it just reports 'communication error', but it's early days yet I suppose.
Cheers, Mike

---

### Post by princeza on 2009-03-10
Thank you so much! I was exhausted with googling the issue.

---

### Post by cephlon on 2009-03-14
I tried this in 8.10 but I still get a Device Communication Error.

---

### Post by ozPATT on 2009-04-23
I have just tried this in Jaunty, and it just required me to turn off the printer then back on again, and it is working great now :) thanks for the above!

---

### Post by mdurham on 2009-04-24
Still doesn't work for me on Jaunty 32.
CUPS reports:
>  HP_LaserJet_1020 (Default Printer) "/usr/lib/cups/filter/foomatic-rip failed"
Any ideas?

---

