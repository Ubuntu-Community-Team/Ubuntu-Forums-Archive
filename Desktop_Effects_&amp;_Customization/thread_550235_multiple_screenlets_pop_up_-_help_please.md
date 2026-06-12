---
title: "multiple screenlets pop up - help please"
date: 2007-09-13
forum: Desktop Effects &amp; Customization
---

### Post by 71CH on 2007-09-13
hi all
my issue with screenlets is that too many of the same one pop up.  i have a few set as widgets which are fine but then the same exact ones pop up in a corner of my screen (not as widgets).  i'm not sure why i have multiples of the same one.  btw, i have a script running as a startup in sessions which starts up my compiz fusion, avant-window-navigator, and my screenlets.  also, my calculator screenlet doesn't pop up at all.  a little help please :)

---

### Post by smartboyathome on 2007-09-13
Try running the screenlets manager in a terminal and posting the results here (I can't remember the command, and am not at a computer with screenlets right now).

---

### Post by richbl on 2007-12-02
I've been having the same problem.

The solution, for me, was to identify those screenlet ini (configuration files) files that were bad (screenlets instances that you *don't* want to run), and delete them.

To do so:

0) open terminal or Nautilus and navigate to /home/username/.config/Screenlets (where username is your username)
1) navigate into the screenlet folder that you want to edit
2) delete the appropriate screenlet ini file

For example, to remove the multiple instances of the ClearCalendar screenlet, I navigated into the ../.config/Screenlets/ClearCalendar/default folder and deleted all ini files found (I had three ini files: one for each of the instances that were run at startup).

It was then a matter of restarting the offending screenlet, and reconfiguring it as appropriate.

Best of luck.

rich

---

### Post by thebigkevdogg on 2008-05-02
> **richbl said:**
> I've been having the same problem.

The solution, for me, was to identify those screenlet ini (configuration files) files that were bad (screenlets instances that you *don't* want to run), and delete them.

To do so:

0) open terminal or Nautilus and navigate to /home/username/.config/Screenlets (where username is your username)
1) navigate into the screenlet folder that you want to edit
2) delete the appropriate screenlet ini file

For example, to remove the multiple instances of the ClearCalendar screenlet, I navigated into the ../.config/Screenlets/ClearCalendar/default folder and deleted all ini files found (I had three ini files: one for each of the instances that were run at startup).

It was then a matter of restarting the offending screenlet, and reconfiguring it as appropriate.

Best of luck.

rich

thanks a ton...worked for me!

---

