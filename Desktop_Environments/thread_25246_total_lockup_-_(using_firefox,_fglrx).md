---
title: "total lockup - (using: firefox, fglrx)"
date: 2005-04-09
forum: Desktop Environments
---

### Post by mangar on 2005-04-09
my machine get stuck when using firefox.
the problem is similar to the one described at the following thread:

[http://ubuntuforums.org/showthread.php?t=24672&highlight=lockup](http://ubuntuforums.org/showthread.php?t=24672&highlight=lockup)

(the difference is between the video card - the poster have a nvidia card,
i have an ati card)

problem description:

1. multiple tabs are open.
2. the pages viewed are (probably) plain html. (i was browsing the 
    blizzard.com art and mp3 sections)
2.1 happened once while playing wolfenstein: enemy territory.
      i think that firefox was opened at the background.
3. the screen freezes, can't use ctrl+alt+del, can't use ctrl+alt+backspace,
    can't use ctrl+c. (the screen stop being updated, the keyboard isn't responding)
4. the mouse pointer is still active.
5. the computer fans get their rpm's up.
6. it happens at irregular intervals: the machine worked for 36+ hours, 
    i've rebooted into windows, shut down the computer for several hours,
    booted back to linux, at after 3+ hour the machine got stuck while using 
    firefox.

software + software/drivers settings:
1. latest hoary (at post time). plus marillat, sun-java repositories.
2. fglrx from the ubuntu repository.
2.1 fastwrites turned off,
2.2 useInternalAGP "no", 
2.3 xorg.conf attached,
2.4 linux-686 metapackage

hardware:
1. compaq Presario x1400 (x1020us)
2. ati radeon 9200
3. pentium m-1.6ghz, dothan chipset.

can this problem be solved? it seems to affect not only me, but several other
people as well.

thanks in advance,
mangar 

.
.
.

(mongar!!! (internal joke))

---

### Post by mangar on 2005-04-09
after following the thread, that the thread i'm refering to had refered to,
(at rage3d forums), and because it happens on two different families of
video cards, i think that the problem is with the x.org x-server itself..

which is bad.

(attached is the xorg.conf, that i seem to have forgoten to attach -
 renamed to xorg.conf.txt)

can anybody shed some light on the issue?

mangar.

---

### Post by rosslaird on 2005-04-09
I can't shed any light, but I can confirm that this problem has happened to me twice (both times with Firefox running). I have an nvidia card and the latest xorg.

This is tough to crack (i.e. with log files) because the whole system hangs -- no ctl-alt-f1, no ctl-alt-bksp, nothing but the big 'ol power button.

---

### Post by mangar on 2005-04-09
i've sent it to bugzilla : it's bug #8861

i've got the following response:

------
Unfortunately, as this is an upstream problem in a binary-only driver, there's
nothing we can do except send this one up to ATI.  If you don't use 3D
acceleration often, I strongly recommend using the 'radeon' driver.
------

i'll add your reply to the bugzilla, as it shows the problem to be of a wider scope.
(i think)

mangar

---

### Post by danpre on 2005-05-04
[QUOTE=mangar]i've sent it to bugzilla : it's bug #8861

i've got the following response:

------
Unfortunately, as this is an upstream problem in a binary-only driver, there's
nothing we can do except send this one up to ATI.  If you don't use 3D
acceleration often, I strongly recommend using the 'radeon' driver.
------

i'll add your reply to the bugzilla, as it shows the problem to be of a wider scope.
(i think)

mangar[/QUOTE]

I have the same problem on MAXDATA laptop with Intel 845GV chipset. Makes me nuts... going for Opera or something...

DANIeL

---

### Post by alastair on 2005-05-04
Some log files might be worth checking for messages e.g.

/var/log/syslog
/var/log/Xorg.0.log

Also :

try turning off the "with composite" options perhaps. 
Or the video "overlay" perhaps.

Try the "ati" driver.

Lastly - for lock-ups, look to using the "SysRq" key i.e.

ALT+SysRq +

  - s = emergency sync
  - u = unmount disks
  - b =  reboot

You can also print memory (m), tasks (t) to the log file etc. - perhaps see what process is running or causing the problem.

There is a text file doc with the Linux kernel docs about this (or google search).

---

### Post by Golgoth on 2005-10-19
ALT+sys+t print tasks to which log file?

I update the bugzilla...

I have the same in hoary or breezy...

---

