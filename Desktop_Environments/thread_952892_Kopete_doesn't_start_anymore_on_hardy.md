---
title: "Kopete doesn't start anymore on hardy"
date: 2008-10-19
forum: Desktop Environments
---

### Post by kirys on 2008-10-19
[EDIT
Since latest update I did with adept kopete (kde 3.5.10 kopete 0.12.7) doesn't seem to work well anymore.
It "starts" but the interface shows after a lot of time (more details in the following post).
I tried to remove all the config files but the problem stays.
Any solution?

Thank you

---

### Post by kirys on 2008-10-19
ok actually it does eventually start it just takes 3' 10'' (always this exactly amount of time) O_O.
cpu is 0%, the hdd is idle, the only reported message is:
VIDIOC_ENUM_FMT: invalid argument.

This behavior started after I've updated kubuntu yesterday.

I think is a kind of timeout for something
any guess?

---

### Post by SuperSonic4 on 2008-10-19
What happens if you drag and drop the kopete icon from the menu to ~/.kde/Autostart

(It (the file) should be something like kopete.desktop)

---

### Post by kirys on 2008-10-20
I'll check it as soon as i'm at my pc.
But I don't want to start it at boot :) the problem is that it takes 3 minutes to start, that's weird :D
Cya

---

### Post by kirys on 2008-10-20
OK putting it in autostart make kopete start after about 3 minutes since the login is complete so the problem stays.

I've discovered something weider, if I logout before the 3 minutes elapses (example start kopete and logout) kopete shows just after the kde desktop was closed (when the screen is all black).

So I've disabled the firewall using guarddog and kopete now starts in a couple of seconds.
It also start just as fast if the firewall is on and the network cable is detached!
So it seems that when there is a connection kopete tries to connect to something on launch and that is blocked by iptables.
I'm sure that this didn't happen on previous release.

Do you know how to solve my little problem?
Thank you

---

### Post by Cato2 on 2008-10-20
You might also want to start kopete from the command line (shell window), to see if it gives any useful error messages.

---

### Post by kirys on 2008-10-20
it the first thing i do when something behave wrongly
the only error reported is:
VIDIOC_ENUM_FMT: invalid argument.

---

