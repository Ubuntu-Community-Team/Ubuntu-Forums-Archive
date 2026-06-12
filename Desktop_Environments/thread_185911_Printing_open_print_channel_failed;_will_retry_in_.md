---
title: "Printing: open print channel failed; will retry in 30 seconds..."
date: 2006-06-01
forum: Desktop Environments
---

### Post by speedy78 on 2006-06-01
I have a laserjet 4050, Dapper see it, all seems ok but on the printer properties -> status i find: "Printing: open print channel failed; will retry in 30 seconds..." and the printer will not print :)

I think it is the same problem listed previously here: [http://ubuntuforums.org/showthread.php?t=176780](http://ubuntuforums.org/showthread.php?t=176780)

---

### Post by mindwarp on 2006-07-07
Same problem with Laserjet 1100.  Worked in breezy.

---

### Post by mindwarp on 2006-07-08
This is somewhat odd, but after unplugging the printer from the wall and plugging it back in, everything worked.  I have a bug report detailing my exact problems: [https://launchpad.net/distros/ubuntu/+source/cupsys/+bug/52277/+index](https://launchpad.net/distros/ubuntu/+source/cupsys/+bug/52277/+index)

---

### Post by wolfchri on 2006-07-08
On my mothers PC, this error message went away when I turned the Parallel Port BIOS setting to EPP / ECP . 

Maybe you check that in your BIOS.

However, it still does not print reliably - sometimes, it does, sometimes not :-(

Printing seems to be messed up in Ubuntu, at least via Parallel Port.

---

### Post by cheesecake on 2006-08-12
I had the same problem with an HP1100 laserjet.

I got it to work by going to 

printer properties 
> Connection

then selecting "Use another printer by specifiying port" and choosing "Parallel Port #1" from the drop down list.

Hope this helps.

---

### Post by floydwilde on 2006-09-28
> **cheesecake said:**
> I had the same problem with an HP1100 laserjet.

I got it to work by going to 

printer properties 
> Connection

then selecting "Use another printer by specifiying port" and choosing "Parallel Port #1" from the drop down list.

Hope this helps.

Hey this worked for me as well, I have a lj 4000 got the same error mentioned above, when I selected LPT #1 in the connection tab, it worked fine.  Thanks!

---

### Post by WayneSchuller on 2006-10-30
> **speedy78 said:**
> I have a laserjet 4050, Dapper see it, all seems ok but on the printer properties -> status i find: "Printing: open print channel failed; will retry in 30 seconds..." and the printer will not print :)

I think it is the same problem listed previously here: [http://ubuntuforums.org/showthread.php?t=176780](http://ubuntuforums.org/showthread.php?t=176780)

I have this problem on a usb HP laserjet 2300.

Distressing, I can't print!

---

### Post by miggl on 2007-07-19
> **WayneSchuller said:**
> I have this problem on a usb HP laserjet 2300.

Distressing, I can't print!

Same issue, but only since upgrading to Feisty!

---

### Post by obryant on 2007-07-26
Same problem with usb HP laserjet 2420. Only tried with Feisty...

I tried a manual install of HPLIP, but it didn't change the outcome.

Any help out there?

---

### Post by spiderman1369 on 2007-07-29
I also have an HP LaserJet 1100A. When I installed Feisty for the first time, I had no problems printing. Then within the last week, I started to get the "Printing: open print channel failed; will retry in 30 seconds..." message.

I tried unplugging the printer and then plugging it back in after 30 seconds. That didn't help.

But when I went to select "Use another printer by specifiying port" and choosing "LPT #1" from the drop down list, it worked. I have no idea what happened within a week to make it do that.

I noticed that under the "use a detected printer" it has HP LaserJet 1100 (HP LaserJet 1100 LPT parport0 HPLIP). I'm a *nix newbie, but why is it listed at partport0? Shouldn't is be parport1 for LPT#1????

---

### Post by 1/0 on 2007-09-02
Same thing for me with a LJ 1320. When I try LPT #1 I get:"Parallel port busy; will retry in 30 seconds..."

I wonder what update might have done this. When did it start occuring for you guys?

---

### Post by miggl on 2007-09-02
Well, unfortunately since it wasn't my computer, and I was unable to find a decent work-around, I was forced to install Windows XP again (the user had some other issues with running Linux as well).

I have never run into this problem on my other machines because I have always done a clean install of new versions. You may end up having to do just that.

---

### Post by 1/0 on 2007-09-03
It seems to me like a Ubuntu problem and not a GNU/Linux problem. I've never had this on the other distros (10+) so I think its something with the new packages in Ubuntu. Maybe its time to repost it as a bug?

---

### Post by 1/0 on 2007-09-04
Errr... or not. I restarted the computer (yes I know I fscked up my uptime but hey...) restarted the printer, switched usb port and that took care of it. Maybe its one of the billion other things I did that finally got initialized but it works for now.

---

