---
title: "Terminal Profile"
date: 2008-08-09
forum: Desktop Environments
---

### Post by Robertg007 on 2008-08-09
Hi list,
I was playing around with the Terminal Profile and screwed it, how do I get the default profile?

Thanks in advance
Robert

---

### Post by pauper on 2008-08-10
Are you referring to gnome-terminal?

Edit--Current Profile

Profile name: [highlight]Default[/highlight]

```
:~$ ls $HOME/.gconf/apps/gnome-terminal/profiles
Default  %gconf.xml
:~$ rm $HOME/.gconf/apps/gnome-terminal/profiles/[highlight]Default[/highlight]/%gconf.xml
```

Restart gnome-terminal--it should load the original profile--or reboot. Unless
you do any changes to profile %gconf.xml won't be created.

Some settings may be left behind:

```
gedit $HOME/.gconf/desktop/gnome/applications/terminal/%gconf.xml
```

---

### Post by Robertg007 on 2008-08-11
I removed %gconf.xml and rebooted the system still getting same gnome-terminal, it created an emtpy %gconf.xml file after reboot.


> **pauper said:**
> Are you referring to gnome-terminal?

Edit--Current Profile

Profile name: [highlight]Default[/highlight]

```
:~$ ls $HOME/.gconf/apps/gnome-terminal/profiles
Default  %gconf.xml
:~$ rm $HOME/.gconf/apps/gnome-terminal/profiles/[highlight]Default[/highlight]/%gconf.xml
```

Restart gnome-terminal--it should load the original profile--or reboot. Unless
you do any changes to profile %gconf.xml won't be created.

Some settings may be left behind:

```
gedit $HOME/.gconf/desktop/gnome/applications/terminal/%gconf.xml
```

---

### Post by sayakb on 2008-08-11
Goto Edit->Profiles press New and create a profile. The new profile has default settings. You may remove the default profile and use the new one.

---

