---
title: "dell mini10 annoying shutdown when ac mains disconnected-battery critically low"
date: 2012-02-04
forum: Dell Ubuntu Support (CLOSED)
---

### Post by NevadaHack on 2012-02-04
A year ago, I put 10.10 on my wife's mini10, as she was having real issues with Win7/Home.  I made it a dual boot machine.   She really liked it, and was really starting to be able to navigate and do things as desired. Well ever since the 11.10 update, she's been fed up, and has switched back to Windows (SIGH...The Horror of it all.....), so I decided that it's (finally) time to try to resolve the issue.

I'm new to this forum, but not new to PC's.  (Have done hardware/software design validation on new PC hardware).  I am sure this is a bug in 11.10, as it was not occurring with 10.10 (Maverick Meerkat).  I would appreciate a pointer to any updates, and/or how to get this reported as a bug to the appropriate developer(s).

Problem:  as soon as AC power is disconnected, the mini10 immediately posts a battery critically low error and shuts down.  I have determined that if I SUSPEND the system, then disconnect the AC mains, and RESTART, I can run for several hours. I've checked battery settings, by clicking on battery icon, and all appears as it should.  

 I have noted in another (old) post, in a different forum, a procedure to fix this issue on a MSI wind (whatever that is) as follows:
Ctrl+A+F2 (**gconf-editor**)
Navigate to** Apps/gnome-power-manager/general**
**De-select** the option **use_time_for_policy**

1)  I couldn't get the the gconf-editor, from desktop, using keystroke combo above.
     What am I doing wrong?
2)  Will this work on a mini10?
3) Is this a fix, or just a workaround?

Thanks,
Still Hacking in Nevada
======

Q) Are you old enough to recall when being a Hacker wasn't a bad thing ?!?

Dell Inspiron mini10 1.6GHz Atom / 1GB Ram / 60 Gb HDD

---

### Post by BC59 on 2012-02-04
gconf-editor isn't installed by default - you'll need to install it. Open the Ubuntu Software Center and install the Configuration Editor. Then try again.

---

### Post by ugm6hr on 2012-02-05
I suspect this is the same issue I had with Gnome 3:
[http://ubuntuforums.org/showthread.php?t=1916674](http://ubuntuforums.org/showthread.php?t=1916674)

---

### Post by mikewhatever on 2012-02-05
First, gconf-editor is installed by default in 10.10. Either launch it from a terminal window by typing **gconf-editor** and hitting Enter, or press alt+f2, type **gconf-editor** and hitting Enter. The key combination you've tried is obviously incorrect.

---

