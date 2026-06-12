---
title: "Ubuntu 9.1 login screen changing problem"
date: 2010-01-25
forum: Desktop Environments
---

### Post by borowitch on 2010-01-25
hey people,

Ubuntu 9.1 is installed on my pc and I want to change my login screen. How can I do this?

---

### Post by byStanderone on 2010-01-25
...ok, take a look at this thread: [http://ubuntuforums.org/showthread.php?t=1340526](http://ubuntuforums.org/showthread.php?t=1340526)

---

### Post by borowitch on 2010-01-26
> **byStanderone said:**
> ...ok, take a look at this thread: [http://ubuntuforums.org/showthread.php?t=1340526](http://ubuntuforums.org/showthread.php?t=1340526)


Thanks but it didn't work.

---

### Post by VCoolio on 2010-01-26
[This]("https://launchpad.net/gdm2setup") works beautifully for me on karmic.

---

### Post by borowitch on 2010-01-26
> **VCoolio said:**
> [This]("https://launchpad.net/gdm2setup") works beautifully for me on karmic.

Alright. Thanks a lot. It works perfectly now.

---

### Post by markrocha on 2010-04-25
everything in the tool works fine, except for the decoration and icon themes - nothing seems to change. any ideas?

---

### Post by Timmer1240 on 2010-04-25
Heres what I do to change it go to terminal enter this command; gksudo -u gdm dbus-launch gnome-appearance-properties

---

### Post by VCoolio on 2010-04-25
> **markrocha said:**
> everything in the tool works fine, except for the decoration and icon themes - nothing seems to change. any ideas?

Are those in /usr/share/{themes,icons}? I don't think it'll work if they are in ~/.themes or ~/.icons.

---

### Post by jonny163 on 2010-04-27
Do you, by any chance, know a way to do this in Lucid?
I will try the method linked by VCoolio but I have low hopes, it seems Lucid is not up for it :(

---

