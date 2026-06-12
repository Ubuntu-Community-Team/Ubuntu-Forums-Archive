---
title: "problem with [gk]su[do] nautilus"
date: 2007-10-20
forum: Desktop Environments
---

### Post by jnylen on 2007-10-20
I just upgraded from Feisty to Gutsy (nice job with the drag and drop from File Roller to Nautilus, I was very glad to see that working).

However, sometimes I find myself needing to run Nautilus as root.  Normally I can do this just fine with the command "gksudo nautilus."

Ever since I upgraded to Gutsy (or maybe just today? I'm not sure, but I haven't installed any upgrades or anything), when I close the nautilus window, the nautilus process itself does not die, and it immediately starts using 100% of my CPU and I have to kill it manually.  The same thing happens if I use sudo or gksu or whatever.

Is there either a way to fix this problem, or an alternative command line I can use to launch nautilus as root?  I also tried "sudo bash -c nautilus" but that does the same thing.  Nautilus does not give any errors in the terminal, except an occasional "metafile hashtable not empty" (paraphrased) that is probably not related.

This exact same problem was also posted at [http://ubuntuforums.org/showthread.php?t=517122](http://ubuntuforums.org/showthread.php?t=517122) but that's in the archives in the Gutsy pre-release development forum.

---

### Post by jnylen on 2007-10-21
Bump....
> **jnylen said:**
> 
Ever since I upgraded to Gutsy, when I close the "gksudo nautilus" window, the nautilus process itself does not die, and it immediately starts using 100% of my CPU and I have to kill it manually.  The same thing happens if I use sudo or gksu or whatever.

---

### Post by darkazurka on 2007-10-22
Really? I managed to open the nautilus as root, a few times. After that it doesn't want to open as root anymore, after it generated a file called "nautilus-debug-log.txt" full of messages. Now it only opens nautilus when I type in a terminal "nautilus". If I type "gksudo nautilus" it doesn't give any error, but it doesn't start anyway! :\

What I typed to open nautilus as root was: (now it never accepts that command again, or any similar, like yours)
```
gksu -u root /usr/bin/nautilus
```

---

### Post by jnylen on 2007-10-22
This is all very odd behavior.  I don't think we are experiencing the same problem.  My problem seems to be related to some service that nautilus needs running in the background - I get hung nautilus processes that use up 100% of the cpu in 2 cases:[LIST]
[*]when I run nautilus as root (but I'm logged in as me)
[*]when I log out (I "fixed" this by installing the pstools package and adding the line "pkill nautilus" to the file /etc/gdm/PostSession/Default)
[/LIST]

---

### Post by darkazurka on 2007-10-22
I also run nautilus as root (but I'm logged in as me), maybe that's the only thing in common.

---

### Post by JAyes on 2007-12-07
I get exactly the same problem on Debian (Lenny/Sid) and have filed a bug report:
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=454764](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=454764)

Maybe a solution will pop up there....

- Jayes

---

### Post by jnylen on 2007-12-07
> **JAyes said:**
> I get exactly the same problem on Debian (Lenny/Sid) and have filed a bug report:
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=454764](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=454764)

Maybe a solution will pop up there....

- Jayes

Apparently the bug has been fixed for Ubuntu Hardy.  You might want to point the folks on the Debian tracker to here: [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/150471](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/150471)

(There's also information there about a hack/fix that involves adding "killall nautilus" to /etc/gdm/PostSession/Default - this worked fine for my purposes, along with just running sudo nautilus in a terminal whenever I need a root nautilus window.)

---

