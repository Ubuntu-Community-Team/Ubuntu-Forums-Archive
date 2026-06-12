---
title: "Cups problems"
date: 2009-06-19
forum: General Help
---

### Post by steve97usa on 2009-06-19
Hi

I really hope somebody can give me some help.
I have a strange problem with Cups on three machines, a fourth one is working.
On all the machines is installed Ubuntu 8.04 lts and kept update.
Two machines are even identical.
The printer is a remote one on Samba, physically on a Win machine.
It's  a Canon Pixma 1500. I read almost all the possible threads about how to install this printer so I'm quite sure the procedure I follow to install and use the printer is correct.
Actually on one machine is working as supposed.

On the machines where is not working, the CUPS system recognize the printer and no errors are issued. Checking the jobs the status is always completed but simply no print happens.
Also attaching the printer in local (only USB) give the same identical problem.
The systems recognize the printer, can even test if is online or offline, if you print no errors and the status on the jobs is "complete" but no print happens.
The printer is working and the  HW (/cable/USB/ecc.) is verified.

So why CUPS seems happy with the printer but no print (every application included the test page of Cups) ?
Where I can start to find the problem ?

Thanks for any help !!

C'ya
  STeve

---

### Post by steve97usa on 2009-06-23
Well, I did some tests and I discovered that the drivers for the Canon Pixma 1500, described in this article ([http://ubuntuforums.org/showthread.php?t=56725](http://ubuntuforums.org/showthread.php?t=56725)) that worked well for many time, with the latest 8.04 are not working anymore.
Simply CUPS print in the void. No errors, no nothing.
I was able to have the printer work again using Turboprint, the latest version.
So it seems I have to pay again Turboprint in order to have the printer working or change printer.

This is the dark side of Linux ... sometime what was working just perfect, cease to work.

There is somebody else with a Pixma 1500 and Ubuntu 8.04 with problems ?

C'ya
  STeve

---

