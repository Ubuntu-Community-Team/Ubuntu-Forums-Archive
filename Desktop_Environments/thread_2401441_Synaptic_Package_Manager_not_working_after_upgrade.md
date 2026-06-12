---
title: "Synaptic Package Manager not working after upgrade to from 16.04 LTS to 18.04 LTS"
date: 2018-09-18
forum: Desktop Environments
---

### Post by FourFourSeven on 2018-09-18
Like it says in the title, I upgraded Lubuntu from 16.04 LTS to 18.04 LTS. Now, Synaptic Pkg. Mgr. doesn't work from the GUI.
But oddly enough, it will work from the command terminal (with sudo, of course).

Any ideas?

---

### Post by Adam_GUI on 2018-09-18
Are you trying to launch Synaptic with gksu synaptic or synaptic-pkexec?

---

### Post by FourFourSeven on 2018-09-18
According to the icon, it's synaptic-pkexec

---

### Post by Adam_GUI on 2018-09-19
Hmm...  Are you running Gnome?

[https://ubuntuforums.org/showthread.php?t=2401518]("https://ubuntuforums.org/showthread.php?t=2401518") This thread may be related.
I could swear I've seen more than that of users posting issues with launchers not working.

Possibly a Gnome issue?

I mean...  If you can launch Synaptic from term and it run, but not from the launcher, it looks related to me.

---

### Post by FourFourSeven on 2018-09-19
Yeah, I noticed that, too. I wasn't *entirely* certain if they were related, so I posted anyway to see whether or not it was specific to Synaptic, or if simply any program was affected (according to the alignment of the planets)

---

### Post by Adam_GUI on 2018-09-20
I found a Fedora user with similar problems here:
[https://ask.fedoraproject.org/en/question/89877/gnome-apps-launchers-not-working/]("https://ask.fedoraproject.org/en/question/89877/gnome-apps-launchers-not-working/")

The marked fix on the page is:
```
Got it solved by editing /etc/gdm/custom.conf and uncommenting the #WaylandEnable=false line.
```

Looks like a fix to GDM.  May be no good of you've got LightDM.  Is there an option to disable Wayland on your login screen?

---

### Post by FourFourSeven on 2018-09-22
I don't think I have Wayland at all. I checked Synaptic (by running via CLI, of course) and saw that it wasn't installed. I do have LightDM, however.
Plus, I don't have /etc/gdm/custom.conf

---

