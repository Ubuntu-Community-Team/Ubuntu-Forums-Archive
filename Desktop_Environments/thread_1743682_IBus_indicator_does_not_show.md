---
title: "IBus indicator does not show"
date: 2011-04-29
forum: Desktop Environments
---

### Post by hongquan1987 on 2011-04-29
In my Ubuntu 11.04, the IBus Indicator does not show. How to correct it?
Thanks in advance.

---

### Post by distrachi on 2011-05-31
I had the same problem.

to fix it, I entered "ibus-daemon -rd" into terminal.

The 'r' restarts ibus-daemon and the 'd' lets it run in the background.

To make this automatically run everytime I start Ubuntu, i used "Startup Applications" program, clicked on Add, entered "ibus" for name, "ibus-daemon -rd" for command, then clicked on Add.

does anyone else know a better way?

---

### Post by hongquan1987 on 2011-05-31
> **distrachi said:**
> 
to fix it, I entered "ibus-daemon -rd" into terminal.

The 'r' restarts ibus-daemon and the 'd' lets it run in the background.

I think setting ibus as input method system in Language Setting has made ibus-daemon run aleady. But the problem is that it does not show in the top panel.

I now found the reason: The Unity's panel by default hide most of notification icon, including IBus'. You just do as [here]("http://www.webupd8.org/2011/04/how-to-re-enable-notification-area.html") to make it show again.

---

