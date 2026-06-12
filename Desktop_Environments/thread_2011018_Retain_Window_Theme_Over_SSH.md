---
title: "Retain Window Theme Over SSH"
date: 2012-06-26
forum: Desktop Environments
---

### Post by spartan21 on 2012-06-26
When executing SSH with the -Y option and opening a file or program from the remote system, is there any way to have the appearance theme from the remote system display on the local system?  Currently, the local theme is applied regardless of original domain.

I am using 11.1.0 on both systems and am only dealing with built-in themes.

Thanks for your help!

---

### Post by spartan21 on 2012-06-26
I found a suggestion to create ~/.gtkrc-2.0, and in it write:

```
include "/usr/share/themes/THEME/gtk-2.0/gtkrc";
```

Unfortunately this doesn't do anything.  Does anyone have any other ideas?

---

### Post by spartan21 on 2012-06-27
bump

---

### Post by spartan21 on 2012-06-28
any ideas?

---

### Post by DorianX on 2012-09-06
I'm having the same problem. By copying the contents of /usr/share/themes between machines, I was able to resolve it when forwarding X windows from my lucid server to my precise workstation, but that isn't working between my two precise machines -- which surprises me quite a lot. The two systems have all the same themes installed and most of the same packages, but any forwarded X apps from the one to the other look like something out of 1994. 

Let's try a different tack: is there something I can do that will produce some kind of log message that might indicate what sort of failure it's having while trying to apply the theme?

---

