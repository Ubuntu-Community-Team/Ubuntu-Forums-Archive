---
title: "very wired issue with my desktop after gdm login"
date: 2005-10-21
forum: Desktop Environments
---

### Post by paxmaster on 2005-10-21
yesterday my ubuntu breezy working fine, until now when the gdm screen come it ok, when i login my mouse and my desktop look funy such as my screen resolution comes up very big,

---

### Post by akseli on 2005-10-21
[QUOTE=paxmaster]yesterday my ubuntu breezy working fine, until now when the gdm screen come it ok, when i login my mouse and my desktop look funy such as my screen resolution comes up very big,[/QUOTE]

This is most probably just an error in your xorg.conf file.
You should boot into a command or simply pull up a terminal window once you are in ubuntu and type in:

```
sudo gedit /etc/x11/xorg.conf
```

then you should look for your "Screen" section and there substitute the present values for the ones that you should have.
If this does not work, get back to me and I'll see what else I can figure out

---

