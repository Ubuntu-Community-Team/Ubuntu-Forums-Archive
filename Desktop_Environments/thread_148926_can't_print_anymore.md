---
title: "can't print anymore"
date: 2006-03-22
forum: Desktop Environments
---

### Post by dabraham on 2006-03-22
Hello,

   A few weeks back I installed Ubuntu, set up a local printer (hp deskjet 890C (printer setup identified it correctly, and suggested the hpijs driver, which I accepted)), printed, and all was good with the universe.

   A few days ago I went to print something, and it just didn't print.  I didn't get any error messages, nothing shows up in the printer queue, nothing.

   Looking in /var/log/user.log I was getting 
localhost hpiod: unable to ParDevice::Open hp:/par/ANY?device=/dev/parport0: No such file or directory: io/hpiod/ppdevice.cpp 827
which I think might be relevant.

   I tried deleting the printer and creating a new one and while it seemed to work judging by the GUI, it added
localhost python hpssd [WARN] Inrecognized URI: parallel:/dev/lp0
localhost python [ERROR] No devices found.
localhost python [ERROR] Error occured during interactive mode. Exiting.
to the log.

   The things that I've done between printing & not printing seem to me to be things that shouldn't affect the printer (getting my extra mouse buttons to work, installing kpilot...).

   If anyone has any ideas, I would very much appreciate it.  Thank you very much.

   Be well.
                                       Daniel Abraham

---

### Post by yager on 2006-03-22
I am in the exact same boat with my HP G85.  The printer was working a few days ago and now does not work.  In my log file I found this entry which is identical.

localhost hpiod: unable to ParDevice::Open hp:/par/ANY?device=/dev/parport0: No such file or directory: io/hpiod/ppdevice.cpp 827

What is strange is that the printer is a USB printer and I have no problem adding the local printer.  It shows this device as being found so I know that Ubuntu can see the printer.

I went through just about every post here about printer problems and nothing has worked.  I have deleted and re-added a printer, reset the HP image system and restarted CUPS.  The test print pages just disappear out of the queue like they are going somewhere but the never come out of the printer.

Update:
I gave up waiting for an answer, sooo............
I reinstalled Ubuntu from scratch and put all of the files back in place.  The printer is now working so I guess we will never figure out what caused that problem.  If it comes back, I will be back with another update.

---

### Post by dabraham on 2006-03-26
I think I'm going to try asking again.  Thanks for the update.

Be well.

---

### Post by Sef on 2006-03-27
You can use the HPLIP driver, so follow this by wondering_jew:

hey I just got my psc 1610 working for both scanning and printing (yay me!)...
first I did

sudo apt-get install hplip gtklp xpp hpijs python-qt3-doc libqt3-mt-mysql hplip-ppds

I don't know if you need all those packages they were all reccomended or suggested and I hate going back and adding things later... then I went to system->administration->printing > printer> add printer and in step 2 I selected psc 1600 from 'HP (HPLIP)' in the manufacturer drop down menu (as opposed to just 'HP' which did make a difference for me ) this got the printing part working.

---

