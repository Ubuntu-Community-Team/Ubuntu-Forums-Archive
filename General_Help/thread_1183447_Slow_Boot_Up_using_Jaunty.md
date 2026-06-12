---
title: "Slow Boot Up using Jaunty"
date: 2009-06-10
forum: General Help
---

### Post by Bunsen on 2009-06-10
My netbook is very slow to boot using Jaunty.

The pro'g opens OK and I get my desktop on the screen but nothing works. The icons on the top of the screen are all inactive.  After a wait of between 2.5 and 3 minutes everything " comes to life" and the computer runs OK.

Any ideas why the delay between boot up and the computer being usable

---

### Post by pagis on 2009-06-11
I have the same problem.
I'm using an HP laptop with 1.86GHz CPU and 1.5GB RAM.
I never had a problem with past releases of ubuntu.

Anyone know what I should check or try?

tnx

---

### Post by blueridgedog on 2009-06-11
Right after booting, run:

```
dmesg
```

An post the output.  Perhaps it will give us a clue as to what the issue is.

Also, is the boot to the xwindows system normal...ie it gets to the graphical part as fast as you would expect or is that slow as well?

---

### Post by Bunsen on 2009-06-11
My boot up seem normal.  Everything runs OK.  The desktop opens and the tool bars appear at the top of the screen. The rotating cursor is replaced with the arrow pointer so " to look at" the computer is ready to go.  I've checked the hard disk light and there is not any disc activity.  When you put the cursor on any of the icons on the tool bar and either click or double click the mouse nothing happens. No windows will open.etc. the computer is running but nothing works.  
If I leave the computer alone after 2.5 to 3 minutes the tool bar starts to work. I can open programs and everything runs just as it should.

If i do a restart I then get the 3 minute wait again before anything will run.  It looks as if some sort of process is running on startup that stops the computer form responding. The delay is always the same length of time so it must be a programme that is running BUT there is not any hard disc activity so if something is running it must only be in RAM and not on the hard disc.

I'm confused:(:(:(

---

