---
title: "[SOLVED] Setting hibernation/shutdown action on unity"
date: 2016-02-15
forum: Desktop Environments
---

### Post by christian-vanet on 2016-02-15
Hi all,
I'm using Ubuntu 14.04 in my laptop.
So, I followed several guides concerning how to enable hibernate option...
So, the command "pm-hibernate", executed by terminal, works well and the system also resume in the correct mode. ;)
But, when I select in Unity power management menu, the hibernation doesn't work (the option "hibernate" in unity menu is enabled!). For 3 seconds the monitor become dark and after this period, the system return as before... so nothing happens...
"sudo pm-hibernate" command doesn't  require the password, I previously edited visudo.

I checked with dconf-editor, in org>gnome>settings-daemon>plugins>power and everything is setting correctly...

So, it seems that the command for hibernation in unity isn't correct.
How I can set the correct command (sudo pm-hibernate) in order to execute a correct hibernation?
Is there a file or a location where I can found some configuration (over dconf-editor) for this workaround?

Thanks a lot in advance.

---

### Post by ian-weisser on 2016-02-15
Is your system capable of properly supporint hibernation?

```
me@mine:~$ pm-is-supported --suspend
me@mine:~$ echo $?
0                                                 ## 0 means supported, 1 means non-supported
me@mine:~$ pm-is-supported --hibernate
me@mine:~$ echo $?
0

```

---

### Post by christian-vanet on 2016-02-15
Yes, man!
Both are supported... but nothing happens...

---

### Post by christian-vanet on 2016-02-16
I found the problem.
The issue is in the kernel... 
With a different kernel, the button works well.

---

