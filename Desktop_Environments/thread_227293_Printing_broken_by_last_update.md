---
title: "Printing broken by last update"
date: 2006-08-01
forum: Desktop Environments
---

### Post by Unconscious on 2006-08-01
I just installed the most recent slew of updates this morning, and now I cannot print. 

Originally (after installation, back in June) printing, from firefox, worked with all of the CUPS printers on my department's network. Now I can't print from firefox or any other application. When I try to configure printing, from the menu under System>Administration>Printing, I get the little arrow timer showing for awhile, but then it stops and nothing happens.

This is an up to date dapper installation on an old compaq P3. I don't even know where to start with this.

Thanks, in advance, for your help.

---

### Post by Unconscious on 2006-08-02
Ok. so far no replies here. Everybody seems to be too busy finding out why people haven't yet abandoned M$. I would like to, but now my printing is borked, so I'm forced to use my M$ box, whcih I hate, but it works.

Printing here is so badly broken that lpstat just hangs and [http://localhost:631/](http://localhost:631/) just hangs too.

Won't somebody please help me?!? Don't make me go back to M$, or even worse, Redhat.

---

### Post by Unconscious on 2006-08-02
Also /var/log/cups/error_log is empty.](*,)

---

### Post by Unconscious on 2006-08-05
Ok. So I filed a bug report, [https://launchpad.net/bugs/55205](https://launchpad.net/bugs/55205), and I got this response.

> I doesn't works, please remove (with --purge) printer daemon (cups i 
think) and reinstall it .


This is almost totally uintelligible to me. Does anybody know what this means?

It sounds like a reasonable approach. How would I go about removing and reinstalling the printer daemon, or sub-sytem, or whatever it is that has broken?

---

### Post by Johan! on 2006-08-05
Open Synaptic, search for "cups"
Mark all cups packages for reinstall

---

### Post by Unconscious on 2006-08-06
Thanks. I'll try that.:)

---

### Post by Unconscious on 2006-08-07
I tried re-installing cups and it's libraries, and a whole bunch of related stuff.  ...still no printing.

Poking around a little more I found something posted on this forum that suggested removing and reinstalling when just a reinstall doesn't work. So, I tried removing cups, it's libraries, and a whole bunch of related stuff. There were tons of things that were removed with it. Things that seemd unrelated, but synaptic removed them. Then I did a fresh install of cups, gutenprint, hplip, the cups libraries, ... Still no printing. 

At this point, I'm getting ready to do a fresh install of the whole OS, since I don't know what else to do.

---

### Post by cfischer on 2006-08-07
I lost my printing capabilities on my laptop when I did the last upgrade to dapper. I reinstalled the samba printer so I can print to the windows machine, and the ubuntu (cups) printer would not work until I upgraded that machine. 

Now, how to fix suspend and hibernate ...

good luck!

---

### Post by Unconscious on 2006-08-08
I went ahead and reinstalled from the CD, reformatted and partitioned the disk, brought the system up to date, and installed all the extra packages I  use, and lo and behold, printing now works.

Is that what you meant by update?

BTW: My bug report was rejected. I guess that means I didn't have a bug, even though everything on the system was installed by the system updater or synaptic. 

:-({|=

---

### Post by tagra123 on 2006-08-27
Here's a workaround until it gets fixed:


[http://ubuntuforums.org/showthread.php?p=1428724#post1428724](http://ubuntuforums.org/showthread.php?p=1428724#post1428724)

---

### Post by mediocre on 2006-08-27
Unconscious--I wonder if your problem and mine are related--see the thread "kprinter/cups woes". The thing is, I don't recall any updates between the time that my printer WAS working and the time it WASN'T. 

Nick

---

### Post by leemckusic on 2006-09-06
I upgraded to 6.06 LTS and my printing is broken. 

Everything worked in Breezy Badger 5.whatever.

I already dealt with xorg not starting by pushing the xorg package back to the "10" version.

On my system I see cups running, [http://localhost:603](http://localhost:603) brings up everything as usual, The "lpq" command shows files queued to print and the first file shows "active". the printer is an Epson Stylus attached by USB cable.

Could you please point me to insstructions to migrate back to Breezy Badger?
Just the printing and whatever else must be migrated back also?

This failure feels like a compiler problem or a changed system call that will take a while for the knowledgable systems people to resolve.

Perhaps another sticky thread would help out? Thanks so much for guidancel

---

### Post by leemckusic on 2006-09-07
My printing broke after updating from Breezy Badger to 6.01 LTS
------------
Reinstall of cupsys programs fixed nothing.
-----------
[SIZE="5"]Solution for me was to remove the existing printer and add the printer back in. The new cupsys software does not like to run with the previous printer configuration.[/SIZE]

Get at the printer configuration AS ROOT like this from a terminal:

sudo gnome-cups-manager

Then... follow the menus to "remove" the printer (or printers) then "add"

Print test page. Bingnnnnnn Yay!

---

