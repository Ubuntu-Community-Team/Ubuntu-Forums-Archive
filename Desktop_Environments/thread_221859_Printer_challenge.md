---
title: "Printer challenge"
date: 2006-07-24
forum: Desktop Environments
---

### Post by jzelliott on 2006-07-24
I am new to Ubuntu and just installed Version 6.06 LTS for PC's on my machine.

When I went to Add Printer it located and identified my printer correctly as being a Minolta QMS 1200w and the installation seemed to go smoothly.  The only problem is that nothing will print on my printer, not even a Test Page from Printer Porperties.

If any of you can point me in the right direction I would be very much obliged.

Many thanks,  James

---

### Post by philippe_carlo on 2006-07-24
Printing in Linux is still **very** tricky. Especially with uncommon printers, as in your case. Even if you get printers to work, unless they are postscript printers, quality will usually be only average at best. Usually HP printers have the best support in Linux, but for printing pictures and other high-demand material, the quality usually just won't do.

My recommendation would be to use windows or MacOS for printing. I'm a linux fan, but printing is a sad story in Linux. (People who have other experiences, feel free to comment on this!) This is not due to lazyness of the open source community, but rather due to an attitude problem of hardware producers.

---

### Post by jzelliott on 2006-07-24
Thanks for your advice Phillipe.
What confuses me is that Ubuntu identified my printer correctly;  it suggested installing one of the "identified" printers and my Minolta 1200w was on the list.  If you look in Printer Properties, Ubuntu had identified the printer, its properties, and even the port it is connected to, correctly In fact, everything in the installation was simple and perfect, but I can not get any reaction our of the printer at all! - not even blink or make a sound when something is sent to it.

During the installation process, if your printer is on the list, does the driver install automatically or do you have to tell Ubuntu to install it?

I hear what you say about using Windows etc. to print.  However, it defeats the purpose of using Linux if you have to copy everything you want to print to a disk and then fire up Windows to print it.

What does everyone else think about Ubuntu printing?

Kind regards,  James

---

### Post by dasyar613 on 2006-07-24
I do not know if I had a printer mishap, or is it something else. I have a local printer setup, a brother hl-1240, and a couple of old lexmarks, optra r, and optra l network printers. The brother was found during initial setup with no problems whatsoever, the lexmarks took some time to get them up and running. They all had no problem printing out the test page, in fact a normal straight foreward printing job causes no problems.

But, yesterday, I tried printing a small .pdf file in landscape mode, which I selected within the pdf program, none of my printers could do the job. So, now I do not know if the failing was in the pdf program, or the printer driver itself. So, I guess for just the simple straight foreward stuff, ubuntu is just fine, but if I want to use some other options I may be in trouble.

On the subject of printer install, ubuntu people should talk to the kubuntu people, and use their printer install program, I had a heck of an easier time finding the network printers with kubuntu.

---

### Post by wpshooter on 2006-07-24
I think printing in Ubuntu/Linux is one of their very weak points.  I have been trying for about a month now to get my HP printer setup so that it can be **SHARED** (printed to from other workstations on my network) and I have had no success so far.

But as far a your problem is concerned, have you tried all of the available drivers that are shown in the listing for your particular printer.  When I was trying to install my HP Laserjet 2100 as a local printer on the system to which it is physically attached, it would either not work at all on some of the listed print drivers (including the one that was listed as RECOMMENDED) or it would print but not exactly correctly.  However, in my case I found that if I choose the second driver on the listing, it seemed to work just fine.

So if you have not done so, go back and try every driver that is listed for your printer.

Good luck.

---

### Post by Ron Byers on 2006-07-24
I am having exactly the same problem with my printer. The printing manager sees the device, (an old Cannon) recommends a driver (the correct driver according to everyhing I have read) and everthing is hunky dory. It just won't print. I had the same problem with a New HP Deskjet. I am just about to chuck Ubuntu. Printing should be a given. It souldn't be a problem at all.

---

### Post by Aggienator on 2006-07-24
> **wpshooter said:**
> I think printing in Ubuntu/Linux is one of their very weak points.  I have been trying for about a month now to get my HP printer setup so that it can be **SHARED** (printed to from other workstations on my network) and I have had no success so far.


I too had this problem printing from an XP PC and found the solution on the forums. At work now but will try to find the solution post this evening. For me the issue was using the destination IP (not server name) in the url when setting up the printer on XP. Also, need the drivers for XP, XP can't acquire them from Ubuntu.

---

### Post by Aggienator on 2006-07-24
> **Aggienator said:**
> I too had this problem printing from an XP PC and found the solution on the forums. At work now but will try to find the solution post this evening. For me the issue was using the destination IP (not server name) in the url when setting up the printer on XP. Also, need the drivers for XP, XP can't acquire them from Ubuntu.

Answer to my problem was in Post 19 in [this thread]("http://www.ubuntuforums.org/showthread.php?t=205011&page=2")

Hope it works for you!

---

