---
title: "Firefox freezes laptop"
date: 2009-11-15
forum: Desktop Environments
---

### Post by cmittle on 2009-11-15
The last couple of days when I go through my Gmail on firefox it has started locking up my computer.  It locks it up so much that using ctrl+alt+bksp, or alt+sysreq r s e i u b don't actually do anything.  I have to use the hard shutdown to get my system to reboot.  I'm using Konqueror right now with no problems, but I would like to be able to get back to using firefox.  Are there some logs that I need to post the output from that would be helpful?

---

### Post by utnubuuser on 2009-11-15
i've found that ctrl+alt+sysreq h e b will unlock my frozen laptop.

---

### Post by lovinglinux on 2009-11-16
Start Firefox in safe mode, if it doesn't lock up, then is probably an extension causing the problem.

```
firefox -safe-mode
```

If that doesn't help, create a new profile and check if it locks up too.

```
firefox -P
```

The command above will start the profile manager, from where you can create and launch a new profile.

If that helps, then it's probably some settings or perhaps database issues.

I recommend trying **Solution** [*[COLOR="Red"]**FOT010**[/COLOR]*] from the Troubleshooting section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT010). Disabling Java (not javascript) might help too. Also see the Database Optimization section from the same tutorial.

---

### Post by cmittle on 2009-11-16
Safe mode didn't work, and I just tried only running konqueror for an entire session and it still locked up on me.  Does anybody have any ideas or can you point me to some log files that may help us determine what is causing this?

---

### Post by cmittle on 2009-11-17
If I launch firefox from a terminal I get a whole lot of these:
```
Gdk-WARNING **: XID collision, trouble ahead
```

Any idea what that means or if it's related?  It sounds bad enough.

---

### Post by ColdLunch on 2009-11-17
What version of Firefox are you running?

---

### Post by cmittle on 2009-11-17
```
cory@cory-laptop:~$ firefox -v
Mozilla Firefox 3.5.5, Copyright (c) 1998 - 2009 mozilla.org

```

---

### Post by cmittle on 2009-11-20
I updated again just a couple of days back and this seems to have fixed my problem.  I noticed a gtk update not sure if that had something to do with it.  I've been running firefox from the terminal the last couple of days and haven't seen any errors at all.

---

