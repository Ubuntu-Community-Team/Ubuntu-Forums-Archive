---
title: "Gwibber configuration window keeps appearing"
date: 2010-09-17
forum: Desktop Environments
---

### Post by scorchgeek on 2010-09-17
Okay, this is a pretty unusual problem. About every ten minutes (I haven't timed it exactly, and I'm not sure if it always happens at the same time), the Gwibber account information dialog box appears. This happens regardless of the active window or whether Gwibber is open or not. That dialog is mapped to Ctrl-Shift-A, but pushing this key combo when Gwibber isn't the active window does nothing. I certainly don't know about anything that would be executing a key combo on a schedule.

The problem seemed to start after I connected a device called the StealthSwitch II, which allows you to program keystrokes to be executed by pushing a foot switch. However, it works just like a keyboard, and the problem persists with the device disconnected. (Another odd problem: the system won't POST with it plugged in, but it seems to work just fine when connected after booting.) None of the buttons are programmed for Ctrl-Shift-A, I don't recall installing any drivers, and, like I said, the issue persists with the device unplugged. 

The only other thing I added lately was an SCSI card and tape drive (yes, a tape drive), which didn't cause any problems for at least a week and also worked out-of-the-box (well, I bought it used without a box, but you get the idea.)

It's starting to really drive me crazy--any ideas?

---

### Post by texastrey1836 on 2010-09-18
I, too, have been having the same problems. I have looked under Gwibber to try to switch something off to eliminate the configuration window from popping up. And mine started with nothing new attached to my computer.
So, no, you're not the only one having this problem.

---

### Post by scorchgeek on 2010-09-18
In that case, I expect it was an update.

Hmm, would you be willing to make a list of all your packages? Maybe we could figure out what software we had in common that might be causing the problem. If it's a non-Gwibber package, that is.

```
dpkg --get-selections > {output file}
```

Sorry about the TAR, the forum for some reason puts a 19.5K limit on text files. It's just a TXT inside.

---

### Post by roignac on 2010-09-20
This is an issue in Gwibber - [https://bugs.launchpad.net/ubuntu/+source/gwibber/+bug/632965](https://bugs.launchpad.net/ubuntu/+source/gwibber/+bug/632965). Yet, there are no reliable steps to reproduce or find out, what might cause the issue. I hope, this will be fixed before 10-10-10

---

### Post by scorchgeek on 2010-09-20
Thanks! No help in solving the problem, but at least I know what's wrong. I might just raise the update frequency to lower the annoyance.

---

