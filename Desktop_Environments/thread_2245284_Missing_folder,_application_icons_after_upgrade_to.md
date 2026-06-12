---
title: "Missing folder, application icons after upgrade to 14.04"
date: 2014-09-22
forum: Desktop Environments
---

### Post by qianian2 on 2014-09-22
I did a clean install and upgrade to 14.04. I noticed some apps, like the sound monitor in the panel, are missing its icon and folders in Nautilus display as a blank rectangle. The panel icon looks like a terminal rectangle with the corner folded and the folders are a white rectangle with corner folded. I haven't been able to find help elsewhere.

What can I try?

---

### Post by ibjsb4 on 2014-09-22
What were you running before?

14.04 (Unity) requires a lot of resources; is your computer up to it?  Whats your specs (cpu. ram, graphics)?

Maybe this is just a case of needing an updated video driver.

You could also try running this command in terminal, see if your missing any packages.
```
sudo apt-get -f install
```
[https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands](https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands)

Just fishing :)

---

### Post by grahammechanical on 2014-09-22
You can also reset Compiz with this

```
dconf reset -f /org/compiz/
```

and restart Unity with

```
setsid unity
```

and may be this

```
unity --reset-icons
```

Regards.

---

