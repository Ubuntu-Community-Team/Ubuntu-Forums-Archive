---
title: "aMule uses 100% cpu"
date: 2005-10-16
forum: Desktop Environments
---

### Post by Alibloke on 2005-10-16
Just upgraded to Breezy on my desktop, I've been running Breezy on my laptop for about a month now and have the same problem on both machines with aMule.  Once I set it going after a while the CPU usage of xorg goes to near enough 100% and after another while aMule crashes.  Then when I xkill aMule the CPU returns to normal.

Does anyone have an idea on why this is so?

---

### Post by ow50 on 2005-10-16
Start aMule from the terminal and attach the output.

---

### Post by Alibloke on 2005-10-17
There is no real output to attach I'm afraid.....

I might add that it takes a while for this oddity to happen, like a couple of hours.

Anyone got an idea, this is really bugging me.

---

### Post by ow50 on 2005-10-17
If you haven't already, try the [aMule's crash forum](http://forum.amule.org/board.php?boardid=67&sid=848c8c4fdaf6bc25631874b2e2f69fb7). They'll probably want a proper backtrace of the crash.

---

### Post by Alibloke on 2005-10-17
It seems the amule wiki is down....anyone know how to run a backtrace?

---

### Post by Alibloke on 2005-10-18
Installed the CVS version instead, still seems to use more cpu than I would expect it to....but at least it doesn't crash now.

---

### Post by doc_holiday on 2005-11-18
I have the same problem, aMule doesn't crash but uses lots and lots of cpu.

---

### Post by megamania on 2005-11-18
What version of aMule are you using? I remember that one of the old versions had such a problem (not crashing but using 100% of CPU resources)...

---

### Post by pixatintes on 2005-12-04
I have the same problem. I used amule 2.0.3 from the official repositories, cpu usage very high and amule very slow.:( 

Now I use the amule CVS but the problem continue.. Maybe a little quickly but not works good. In hoary it worked perfect.. :confused:

---

### Post by megamania on 2005-12-05
[QUOTE=pixatintes]I have the same problem. I used amule 2.0.3 from the official repositories, cpu usage very high and amule very slow.:( 

Now I use the amule CVS but the problem continue.. Maybe a little quickly but not works good. In hoary it worked perfect.. :confused:[/QUOTE]

I have amule running on a separate computer, a P2 600mhz with 128mb ram. Definitely not a workstation. :-)

It's been running for 4 days now without a single problem. Currently, it is using 10% of CPU and 20% of memory. From time to time (every week, more or less - especially when I'm downloading from a lot of sources) memory usage goes to 70%, and I have to quit and restart it. Besides that, everything is fine - I even take the liberty to have folding at home running in the background... :-)

---

### Post by pixatintes on 2005-12-05
I have amule running for a few days too. In the first the amule works fine, in the second slow, next day very slow.. I don't Know.. ](*,)

Yesterday I compiled amule from tar.gz ([HowTo Compile In Debian - From AMule Project FAQ]("http://www.amule.org/wiki/index.php/HowTo_Compile_In_Debian")) and now I'm testing it..
It have more fast and better performance, but it's only the first day.. :(

If this soluton don't work, I will try Debian packages from  'deb [http://amule-debian.dyndns.org/](http://amule-debian.dyndns.org/) debian/'. Debian package in ubuntu don't work with wxWidgets 2.6, it's more ugly but maybe it works fine.
Has somebody tested debian packages?

---

### Post by pixatintes on 2005-12-05
Test amule compiled from tar.gz --> Negative

Now testing --> aMule from Debian packages from 'deb [http://amule-debian.dyndns.org/](http://amule-debian.dyndns.org/) debian/'.

---

### Post by Alibloke on 2005-12-05
I found that even with a new computer (barton 2.5 to a dual core athlon), fresh install and the cvs version I still get 100% cpu usage if I leave the program running undocked.  If I leave it docked then everything is ok.

After installing Azereus I have none of these issues, cpu usage is a bare minumum and I get a faster download rate....

---

### Post by theFallen on 2005-12-05
I also had a very slow Computer after using aMule a certain time, but I changed the location of the tmp and output files folder to another hard disk than the system disk and it did wonders.
Perhaps this could help some of you.

---

### Post by pixatintes on 2005-12-06
:KS  aMule from Debian packages from 'deb [http://amule-debian.dyndns.org/](http://amule-debian.dyndns.org/) debian/'. is the solution. 

:D :D :D  It works perfect...!!!  :p :p :p

---

