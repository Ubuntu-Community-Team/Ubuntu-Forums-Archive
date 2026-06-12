---
title: "Disabling auth dialog for cpu freq scale applet"
date: 2009-10-31
forum: Desktop Environments
---

### Post by letronje on 2009-10-31
I just did a fresh install of Ubuntu 9.10 and added the cpu freq scale applet to my panel. 

I regularly change my cpu frequency and its annoying when it asks me to authenticate each time i try to change the freq. Is there a way to disable it? I tried reconfiguring gnome-applets using "sudo dpkg-reconfigure gnome-applets" but that didn't work(nothing happens). This trick had worked for me in 9.04 i think. 
Please Let me know how i can fix this.

Thnx in advance.

---

### Post by azerty88 on 2009-11-21
Here is what you need to do:

sudo gedit /var/lib/polkit-1/localauthority/50-local.d/01-cpufreq.pkla

and paste this:
```

[cpufreq policy for admin group]
Identity=unix-group:admin
Action=org.gnome.cpufreqselector
ResultAny=no
ResultInactive=no
ResultActive=yes

```

---

### Post by purduepilot on 2009-11-22
I was having the same problem.  This solution seemed to work.  Thanks

---

### Post by letronje on 2009-11-22
worked for me too, thnx

---

