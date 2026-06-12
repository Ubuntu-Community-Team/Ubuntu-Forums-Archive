---
title: "Printer doesn't work in Jaunty"
date: 2009-06-18
forum: General Help
---

### Post by whiskyprajer on 2009-06-18
My HP LaserJet 6P, which worked fine in previous Ubuntu versions, does not work in Jaunty (fresh install). The first page prints a single line of strange, then the printer runs one blank page after another until the tray is empty. I've tried System > Administration > Printing > Delete, Reinstall and I get the same results.

---

### Post by whiskyprajer on 2009-06-18
Update: I tried the hplip package from the HP site. No good, as it does not want to recognize USB ports.

Any ideas why this isn't working in Jaunty, but works fine in older editions?

---

### Post by whiskyprajer on 2009-06-19
Bump.

---

### Post by 73ckn797 on 2009-06-19
Maybe try here: [http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareIndex.jsp?lang=en&cc=us&prodNameId=14980&prodTypeId=18972&prodSeriesId=25477&swLang=8&taskId=135&swEnvOID=2020](http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareIndex.jsp?lang=en&cc=us&prodNameId=14980&prodTypeId=18972&prodSeriesId=25477&swLang=8&taskId=135&swEnvOID=2020)

How old is that printer?

None of the HP drivers from synaptic will work?

I do not know what else to tell you but figured that asking a few questions may help.

---

### Post by whiskyprajer on 2009-06-20
Thanks, but it looks like the HP guys are stymied, too. It's a strange occurrence, because I've worked around the issue by disc-booting an old copy of Hardy. No problems there. I'm really puzzled by what's going on here.

---

### Post by 73ckn797 on 2009-06-20
Doing some looking around found many who have had some difficulty with installing this printer but several have made it work. Google was my source. My search was for "hp 6P printer in Ubuntu". One of the findings was from someone who had to try the 15 drivers listed but found one that did work. 

Have you gone to Launchpad? Here is the one I found related to your issue: [https://bugs.launchpad.net/ubuntu/+source/system-config-printer/+bug/371306](https://bugs.launchpad.net/ubuntu/+source/system-config-printer/+bug/371306)

I assume you have tried removing the printer then reboot and go through the installing new printer in System/Administration/Printing ?

OFF topic: I had to replace my printer yesterday. Was running a HP Officejet 5610 with no problems. Suddenly all of the lights on the printer console starting flashing and freaking out. Then I started getting cartridge error messages. Changing print cartridges did not solve the problem. I bought a HP Officejet J4580 and it was immediately recognized and is working great. I was not sure if such a new printer would work but it works great and only cost $99.

---

### Post by wpshooter on 2009-06-20
> **whiskyprajer said:**
> Thanks, but it looks like the HP guys are stymied, too. It's a strange occurrence, because I've worked around the issue by disc-booting an old copy of Hardy. No problems there. I'm really puzzled by what's going on here.

Have you tried ALL of the available HP drivers that are listing in the System/Administration/Print setup section.  Sometimes it is a matter of just trying all of the listed drivers until your find the one that works (or works the best).

---

### Post by DonThompson on 2009-06-20
No-one should be stymied:  The problem is the printer is recognized as a Laserjet 6P/6MP and the two are different.  The 6MP is PostScript (which is the funny page you are getting starting out %!PS-Adobe-3.0 and wandering off from there) and the 6P is not [PostScript].

Now that I started so well, I have to let you down because mine doesn't work either...

Off to search for HP PCL 6.0 drivers because despite its age (or maybe because of its age) my 6P is a happy little work horse printer that may have been pricey to buy compared with today's stuff, but is fairly inexpensive to run, quite quick, fits on the shelf with front access to just about everything and I like it!

---

### Post by whiskyprajer on 2009-06-21
D'oh! I did NOT make that connection! That is indeed a bummer to try to work around. And I like the 6P for precisely the reasons you gave.

---

### Post by DonThompson on 2009-06-22
This may or may not help, but I am now printing...

Firstly:  I have a tiny machine that I just installed as a print server - basically using it as a JetDirect card because it's all I've got with a parallel port.  It is, I believe running Jaunty server without a GUI but using Webmin.  It cannot print itself - the test pages are blank.  Under Webmin, my printer driver is None (remote or raw printer).  If I try a test page, choosing ASCII gets me a blank page, choosing B&W PostScript gets me a page that starts "%!PS-Adobe-2.0" and a bunch of blanks.  prior to that, using the PostScript choices available to Webmin, I got w-a-y more blank pages.  

I reinstalled the printer drivers on two servers (that have GUIs) using System > Administration > Printing then selecting the printer using the Wizard (first HP, then 6P, avoiding the two 6MP alternatives) and test pages work.  Then I reinstalled on my workstation, but the GUI did nothing so I had to copy the GUI's command 'sudo system-config-printer' from a terminal.  I don't think the Jaunty GUI forwards the password.

Now the test page works, but I cannot print directly to the little print server because it says there have been too many previous errors, and I have no clue how to reset them.  (A pop-up appears with the red wrong way symbol and "Failed to print document" in bold and the explanation "Too many failed attempts".  BUT my servers that can print also share the share and so I print to one of them that in turns sends it on to the little guy and he responds well.

---

### Post by whiskyprajer on 2009-06-24
That is simply not satisfactory. I would drop back down to Intrepid before I performed those sorts of pretzels. Here's hoping the team gives this a little proper attention.

---

