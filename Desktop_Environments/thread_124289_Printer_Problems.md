---
title: "Printer Problems"
date: 2006-02-01
forum: Desktop Environments
---

### Post by syklitengutt on 2006-02-01
Hi.
Cant get my printer to work?
I have a HP Descjet 720C printer.
I use CUPS and it finds the printer and the drivers.
But when I try to print nothing happens.

any ideas?

---

### Post by Vulpus on 2006-02-01
[QUOTE=syklitengutt]Hi.
Cant get my printer to work?
I have a HP Descjet 720C printer.
I use CUPS and it finds the printer and the drivers.
But when I try to print nothing happens.
[/QUOTE]

Have you tried switching off your PC?  I had a similar problem and nothing I did would make it work.  I gave up in disgust and went to bed, the next morning when I switched on the printer was working!  

It probably isnt that simple but it worked for me!

---

### Post by Vulpus on 2006-02-01
Another point.  Are you printing a 'test' page from CUPS or an actual document.  I had a problem where test pages would not print but everything else would.

---

### Post by syklitengutt on 2006-02-01
tried to reeboot, tried to print ordinary pages and test pages.
Nothing happens

---

### Post by ipp3l1 on 2006-02-01
I have the same problem with HP Deskjet 840C. When I installed the printer for the first time, it worked and then it just sudennly stopped working. But the problem might be an empty color cartridge. dunno.:confused:

---

### Post by Why Not on 2006-02-01
I have the same problem with my HP Deskjet 895Cse The PC also has Windows XP installed and my HP printer (Deskjet 895Cse) works great in Windows. The printer is connected via a parallel port. In Ubuntu when I clicked on System->Administration->Printing->Add New Printer, my Deskjet showed up as a "Detected Printer". I followed all the prompts and selected the correct driver (hpijs). The printer icon shows up in the print manager box. When I send a test page to the printer the job shows up in the printer que and the status says "printing". After about ten seconds the job closes but the printer doesn't print! The printer is ON and I have booted back into Windows and tested the printer without touching any cords or switches and it works fine.

---

### Post by ipp3l1 on 2006-02-01
Hmm... This seems to happen quite lot. Wonder what's in it then...

---

### Post by eradusfalk on 2006-02-09
I am having a problem too with the HP deskjet 895Cxi. It worked fine in Kanotix and Knoppix, older versions like 3.2. Got very nice colorprints too, (better than in Windows) but now it does not print black in 600 dpi mode. In normal mode, 300 dpi, it works fine: I get black and color, but that is not good enough for a good print. Besides hpijs prints much too light now. Before it printed great pictures without changing anything.
I tried all versions of hpijs, but nothing changed. Even tried hpijs-rss, a patched version of standard hpijs, from Linux Printing Org. Reinstalled cups, hpijs, hplip, foomatic etc. But still got the same effect. It is very anoying because it worked perfectly under Kanotix and Knoppix. So what has changed since then?
You can get black and color using foomatic with gimpprint, but the photo's are too dark then. But at least it works. I have searched on the internet for a solution for weeks now, but still can't find one. Is this a bug of what?
Who can help?

Eradus

---

### Post by JLDT on 2006-02-15
I also experienced the same problem.
I am instaling an Epson EPL-6200L laser printer. The printer is detected but printing a test page or an actual document doesn't produce any print outs, any idea what is wrong with this? Is there any other driver I should use to make it work?

---

### Post by pito on 2006-02-16
Hello, I am too stack in the printer problem.
I run on U-5.10, while using Fedora Core3 Printers worked.

I have tested 2 parallel printers Xerox M750, HP Deskjet 695C and one USB HP PSC2355. The USB printer works fine in U-5.10.

My setup as well detects the printers, but not able to print.
I have looked at
/var/log/cups/error_log and found some strange things indicating that the PC talks to the printer but there are somm missing parts.
The Log suggest to run in "debug mode" for more extensive information, but I do not know how to enable it.

Next week I will try to look at both ppd and xml files for my printers that are on a Fedora C3, a friend of mine still use it.

Any one with a good idea ?

PiTo

---

### Post by JLDT on 2006-02-17
any solution to this problem? I tried searching in both this forum and lin linuxprinting.org but stil can't get my printer to work. I've tried swotching to parallel cables as well. No print outs coming out. I hope someone could help.

---

### Post by spookygeek on 2006-02-20
Add me as someone else who is having printer problems.  As somone else mentioned, i had the printers working fine before, but now - nothing.  It seems to be recognizing, but then nothing will print.

Let me know if someone gets a fix for this.  I have a HP Deskjet 3320.

Thanks,

-Brent

---

### Post by r.stan on 2006-02-22
Hi,

I have the same problem : my hp 3420 worked fine and now I get only a blank page (it still works on XP).

stan

---

### Post by syklitengutt on 2006-02-23
bump

---

### Post by pyrforos on 2006-02-23
same here...The printer(epson stylus photo 830) seems to de recognised but no output...

---

### Post by JLDT on 2006-02-23
I have tried using the live cd as well just to check if i have probelms with my installation. Same thing happened, printer was installed but no print out. can anyone help us? I guess this is one reason why some of us still cant leave windows. I still have to switch to windows just to print. it is such a hassle.

---

### Post by PaDV on 2006-02-28
The solution for your HP Deskjet 720C printer problem is already on the forum: [http://www.ubuntuforums.org/showthread.php?t=87164&highlight=hp+printer](http://www.ubuntuforums.org/showthread.php?t=87164&highlight=hp+printer)

---

### Post by Swiss on 2006-02-28
My HP Officejet G85 doesn't print from Ubuntu, is Ubuntu Plug & Play (silly question)?

---

### Post by facefur on 2006-02-28
I had problems with my HP DesignJet 100 with almost every version of Linux before Breezy came along.  It now includes the driver and PPD's for it. I also use an Epson Stylus Photo R200.

Now, I admit, both printers are USB, and they work fine, so I can't be much help with parallel units.  There are, however, inexpensive cables that convert from USB ports to parallel inputs for printers.  If the parallel ports are causing problems, you might try that.

I have also found that the people at [http://linuxprinting.org](http://linuxprinting.org) are remarkably helpful.  There is a forum there specifically for HP printers.

---

### Post by 11hjpphty76lkjj on 2006-02-28
If you are using an HP printer, I'd suggest taking a look at the [http://hpinkjet.sf.net](http://hpinkjet.sf.net) website and application.  HPLIP 0.9.8 is the newest version and it works great with a ton of printers with scanning/printing/fax support, depending on what your printer supports.

Aaron

---

