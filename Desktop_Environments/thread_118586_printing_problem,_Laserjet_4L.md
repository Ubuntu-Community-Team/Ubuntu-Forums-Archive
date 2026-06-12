---
title: "printing problem, Laserjet 4L"
date: 2006-01-17
forum: Desktop Environments
---

### Post by Ameet on 2006-01-17
I had my HP Laserjet 4L working just fine for over a month with Ubuntu 5.10 ... then, I think I did something foolish, like trying to install gcc and then uninstalling it.  I don't know if that is what messed up my printing capabilities.

Now, under System>Administration>Printing, I still see "Laserjet-4L, Ready".  The driver is listed as "hpijs" (which I believe I had to manually download and install at one time ... or was that for 5.04?).

But when I try to print a test page, I get nothing out of the printer.  Not even a blinking green light.  In the print queue, I briefly see "Test page" show up, then it disappears within 2 seconds, and the queue is empty.  But no test page out of the printer.

Oh, the printer prints out its own test page fine when I use the button on the printer.  So I am presuming the problem is on my computer somewhere.

If it matters, I have a Gateway 600YGR laptop.

Help!  Please know I am not a big Linux expert but I can use a command line fine if you specify exactly what to do!  Thanks,
Ameet.

---

### Post by Ameet on 2006-01-17
Oh, one other detail about this problem.  When I try to print a page from a document -- or to print a test page from the printer preferences window -- my printer's "Ready" light, which is usually a steady green, blinks briefly, then goes back to steady green. 

So, the printer **is** receiving **something.**  It's just not doing anything with it.

Oh, if I wanted to reinstall the driver... how exactly do I do that?  Remember, relative newbie to linux here.

---

### Post by Sef on 2006-01-17
"sudo apt-get install hplip"  for installing the driver (without the quote marks.)

The HPLIP driver includeds the hpijs driver.

---

### Post by Ameet on 2006-01-19
[QUOTE=Sef]"sudo apt-get install hplip"  for installing the driver (without the quote marks.)

The HPLIP driver includeds the hpijs driver.[/QUOTE]

Ok, I did that in a command shell.  The behavior hasn't changed.  I try to print a test page from the printer window, and the green light on my laserjet blinks once, briefly, then goes solid again.  No test page comes out, nothing in the printer queue.

Other thoughts?  Could CUPS be a problem?  How can I check if it is running ok?

---

### Post by happyponcho42 on 2006-01-20
I am also suffering from the same problem, except with my HP Laserjet 6P.  What once worked perfectly, now does nothing except flash a green light.

Anyone out there have a solution to this?

---

### Post by UphillSkier on 2006-01-20
just a thought - have you tried deleting and re-adding the printer using the system | administratrion | printing tool?

---

### Post by happyponcho42 on 2006-01-20
I tried that multiple times with no luck.  I've installed so many new packages since I first installed 5.10 that I don't know where to begin to look for the cause of this problem.

---

### Post by Ameet on 2006-01-25
Well, I solved the problem my way :cool:  ... I backed up /home onto a CD-R, and reinstalled Ubuntu 5.10.

Problem solved.  The right drivers got installed from the beginning and everything works.  My guess is that, for my system, I had somehow trashed some critical libraries for the printer driver or for CUPS to function smoothly.  Not knowing which ones they were, well, reinstalling seemed the simplest approach.

---

