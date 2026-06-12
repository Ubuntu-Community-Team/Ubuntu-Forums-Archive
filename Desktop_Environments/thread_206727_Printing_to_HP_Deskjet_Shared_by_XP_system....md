---
title: "Printing to HP Deskjet Shared by XP system..."
date: 2006-06-30
forum: Desktop Environments
---

### Post by elbowgeek on 2006-06-30
I have set up a Deskjet 3650 under XP and have shared it.  I managed to connect to it from Dapper and I'm able to send jobs to the queue on the XP machine.  However the printer merely makes a couple of noises as if getting ready to print but then nothing, and the job remains stuck in the queue.

I did check to see if the printer would print when connected via USB to the Dapper machine and it works fine, so there appears to be a problem with the network side of things, or else the the XP printer queue doesn't like something about the data sent from Dapper.

Any help would be most appreciated.

Cheers

---

### Post by DarkaOnLine on 2006-07-01
Hi,
When you add the printer in Ubuntu,

1. Choose &#8220;Network Printer&#8221; and &#8220;Windows Printer (SMB)&#8221;
2. put your Workgroup in the Host field
3. Put &#8220;guest@<host>/<printer>&#8221; in the Printer field (replacing <host> and <printer> with your host & printer names)   (if needed)

So, for example, if your Windows machine was called &#8220;Dozer&#8221; and your printer was called &#8220;LaserPrinter&#8221;, you would put &#8220;guest@Dozer/LaserPrinter&#8221;.

You should not need a name and password for the Windows machine for this to work.

More over you will need HP drivers. You can get them trom: [http://hplip.sourceforge.net/](http://hplip.sourceforge.net/)

Download them. Tar it then go to the System ->Administration -> Printing. Select your new printer in the Properties menu klic Drivers and the Install Drivers. Open your extracted folder then prnt->phijs->ppd and from the list chouse your printer.
FINISH

good luck:)

---

### Post by delfick on 2006-07-13
My deskjet 3650, also on a shared windows XP computer, also doesn't work

It used to make noises as if it's about to start printing and then do nothing, followed by me restarting the computer several times just to get rid of the damn job from the queue.

Just today i decided to see if it would work....Now it does nothing. The job doesn't even appear in the queue on the computer connected to the printer.
I followed what DarkaOnLine said just above this post, but it still doesn't work...

Also i noticed that everytime i add a new job, the job number in the queue on my computer keeps rising, and restarting the computer doesn't reset the job numebr to one....

thnx for help

---

### Post by delfick on 2006-07-15
anyone?

---

### Post by delfick on 2006-07-17
i'll take that as noone

---

### Post by boterbram on 2007-10-21
Hello

I am sorry I can't help you two, but I've just got the exact same problem. I had two computers (1 ubuntu, 1 xubuntu) and both did the same thing. Could it be that windows xp has got problems "reading" the printjob from linux? Maybe a windows-side configuration/installation will solve this?

gr Bram

---

### Post by boterbram on 2007-10-21
I have solved the problem I think

In XP go to control panel --> printers --> Right click: Hp deskjet 3650 (in my case) --> Properties. Choose the tab Ports. Uncheck the first checkbox at the bottom of the screen. In Dutch it says "Ondersteuning in twee richtingen inschakelen", which freely translated means "Approve support in 2 directions" (may have something with bidirectional in it). I think this has something to do with windows getting a print job, trying to acces the source of the job, which would probably work if the source was a windows computer, but which doesn't work now because the source is linux. I haven't found any problems because of disabling this function, yet.

Hope it works:D
Good luck
Bram

---

### Post by lucidv01d on 2008-04-22
Turning off the bidirectional support worked for me. Thanks for the help!

Gutsy
HP Deskjet 3650

---

