---
title: "Dell 1320c Printer ---Again"
date: 2009-03-29
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ikkepjo on 2009-03-29
Hi all,

I followed the instructions in

[http://ubuntuforums.org/showthread.php?t=783346&highlight=1320c](http://ubuntuforums.org/showthread.php?t=783346&highlight=1320c)

including the changes to lpd ...

Alas, nothing works. My printer insists to print only max 3 pages of a document and then the error light starts to blink ...

Using the web interface, I see that the printer thinks the tray is empty (it is not, opening and closing the tray relaunches the job ... up to 3 pages)
The manual says that when the tray and the error light blink orange, it is the wrong paper size ... but it is A4, as set up and as present in the tray (and anyway it is ok for the first 3???)

In my frustration I reinstalled XP on another PC, and there the same docs print completely normally and fine ...

Help, anybody?

Regards,

Peter

---

### Post by ikkepjo on 2009-03-30
Nobody?

Peter

---

### Post by ytsejam1138 on 2009-03-30
Can you post some screenshots of your Printer setup?  I have the same printer and it works perfectly in Ubuntu 8.10  It's probably just one of the settings that is just a little off.

---

### Post by ikkepjo on 2009-03-31
here they are:

---

### Post by ytsejam1138 on 2009-03-31
Thanks,  okay the only thing that is different with my setup is on the Printer Options tab:

Media Size:  Letter 8.5" x 11"

and under Detailed Settings:

Substitute Tray:  Use Printer Settings

Try the above settings and see if that makes a difference.

---

### Post by ikkepjo on 2009-04-01
Nope, no success, could it be that 8.04 is not ok?

Peter

---

### Post by ytsejam1138 on 2009-04-01
I'm not sure.  It might also be Xubuntu.  Have you tried to configure the printer in CUPS?  You should be able to access it by typing this in your web browser:  [http://192.168.2.60:631](http://192.168.2.60:631)

---

### Post by ikkepjo on 2009-04-02
yep, the setting is reflected exactly in cups ...

trying to migrate to 8.10, we'll see if that helps

Thx,

Peter

---

### Post by ikkepjo on 2009-04-02
odd ... I have exactly the same behavior in 8.10, a brandnew clean install, the only thing is that I brought all packages up to date ...

3 pages and then stop ...

opening and closing the tray reprints the 3 pages 

pressing X on the front rather unsurprisingly cancels the job

I am totally running out of ideas here, anybody a clue ?

Regards,

Peter

---

### Post by ikkepjo on 2009-04-07
Found it ... it is indeed Xubuntu: a clean install of Ubuntu (regular version) removed the issue ...

Drat ... now I'll have to put up with the bloat ...

Oeter

---

### Post by ytsejam1138 on 2009-04-07
Glad you got it sorted out.

---

