---
title: "Not booting to GUI! Command only"
date: 2008-01-08
forum: Desktop Environments
---

### Post by curtis1552 on 2008-01-08
After trying to get my sound working I must have edited something I shouldn't have.

Now my computer goes directly to the command line login without going to the GUI login at all. It starts Gnome fine [using startx]. I'm running 7.10 Gutsy. I just want it to load the GUI again; any help would be appreciated.:confused::confused:

---

### Post by reckless2k2 on 2008-01-08
try this and then reboot:

```
sudo chmod +x /etc/init.d/gdm
```

---

### Post by curtis1552 on 2008-01-08
I get no such file or directory.

---

### Post by sonofabics on 2008-01-08
I have a similar problem, while trying to get my ati 9600 work :(
I put back the xorg-ati driver package after i failed with the restricted and the one provided by ati.
At the login screen everything looks fine after i give the password the environment starts up and after 10-15 seconds i get back to the login screen again:(
in recovery mode i can log in only.

i am newbie with ubuntu every help is apritiated

---

### Post by reckless2k2 on 2008-01-08
sounds like you removed gdm. how about just reinstlal it and you should be fine then.

```
sudo apt-get install gdm

```

reboot and you should be fine.

---

### Post by curtis1552 on 2008-01-08
that did it, thanks.
(and I thought it was something else)

---

