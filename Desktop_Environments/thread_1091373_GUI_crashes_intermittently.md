---
title: "GUI crashes intermittently"
date: 2009-03-09
forum: Desktop Environments
---

### Post by inselaffe on 2009-03-09
For a few months now, every once in a while, my GUI will crash. The screen goes black after a few moments the log on prompt is shown.

This doesn't seem to correlate to - well anything.

I can be typing or just reading from the screen. It has happened between installing updates and rebooting, and when there are no updates open. It has happened whilst various applications are open or not.

This can happen several times a day or once a fortnight. You can appreciate this can be a huge pain the the backside when it means I loose work - maybe it detects that I've not saved anything for a while!?

I'm at a bit of a loss as to how to troubleshoot this. Any ideas where anything useful might be logged?

---

### Post by ddrichardson on 2009-03-10
Theres information [here]("https://wiki.ubuntu.com/DebuggingXorg") but its very debug heavy. I would kill gdm and run from a terminal by running startx for a while. When it bombs you should see why.

You can also check its log:
```

cat /var/log/Xorg.0.log | grep EE
```

---

### Post by beardie on 2010-12-17
Hi 

I am experiencing the same issues. Cant seem to track the cause down in the logs or find a solution.

Any more ideas?

---

