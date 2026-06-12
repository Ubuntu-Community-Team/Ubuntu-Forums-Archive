---
title: "lxde cpu usage"
date: 2010-11-21
forum: Desktop Environments
---

### Post by kardhal on 2010-11-21
Hi

I've installed lxde desktop enviorement on ubuntu today because gnome was too slow for my old laptop. Since than, system monitor shows that cpu usage is at constant 100% even if nothing else is running. Can someone explain this to me? Is system monitor bugged in lxde or will my cpu melt?

---

### Post by mikewhatever on 2010-11-21
Does the System Monitor show which process uses cpu the most? If not, run **top** in Terminal and post the output.

---

### Post by buckley310 on 2011-11-08
i know this thread is almost a year old but i figure since its google result #1 for "lxde cpu usage 100" ill post this... i ran into this issue and what fixed it was enabling dbus. i had the daemon disabled because nothing was using it before. lxde tries to launch "/usr/lib/policykit-1-gnome/polkit-gnome-authemtication-agent-1" but it fails because it requires dbus and lxde keeps restarting it. either way if CPU is 100% and no process is high just watch the PIDs in top (or even better htop) and see which process keeps changing PID. that will point you to the problem.

---

### Post by rojaasensei on 2011-11-08
could this be the "fuser" bug?

---

