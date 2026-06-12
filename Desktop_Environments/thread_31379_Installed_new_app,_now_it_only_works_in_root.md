---
title: "Installed new app, now it only works in root"
date: 2005-05-03
forum: Desktop Environments
---

### Post by davefr on 2005-05-03
Hi,
I installed a simple app to show network traffic in an icon.  It's called Knemo.

I installed it using sudo apt-get install knemo.  Now it only works when I log in as root.  When I log in as a regular user it's running under KDE processes but won't show the icon.  (I think it's a process vs. an app but it doesn't want to configure in user mode).

I've tried uninstalling and re-installed but it won't work in user mode.

Any ideas???

TIA

---

### Post by lao_V on 2005-05-03
Can you confirm it says "Running" under KDE processes in Kcontrol rather then just being listed?

---

### Post by davefr on 2005-05-03
Yes, it's definately a running process in std. user mode.  I just can't get the icon to come up or get to any configuartion screen.

However all is fine in root.

[QUOTE=lao_V]Can you confirm it says "Running" under KDE processes in Kcontrol rather then just being listed?[/QUOTE]

---

### Post by Takis on 2005-05-03
[QUOTE=davefr]Yes, it's definately a running process in std. user mode.
[/QUOTE]

You mean under your (i.e. non-root) user id? Can you kill it, and restart it?

---

### Post by davefr on 2005-05-04
Yes, in non-root I could stop and start it and remove it and uninstall it and still the only place it would show the icon is in root.  (I had previously enabled root login capabilty).

For some reason this app. seems to default to root.

I reverted back to a previous image backup I had made and it now installs and shows up just fine.  I think enabling root login got it confused. 

[QUOTE=Takis]You mean under your (i.e. non-root) user id? Can you kill it, and restart it?[/QUOTE]

---

