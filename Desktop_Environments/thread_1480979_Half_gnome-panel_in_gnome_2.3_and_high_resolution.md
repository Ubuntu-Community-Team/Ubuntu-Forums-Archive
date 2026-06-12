---
title: "Half gnome-panel in gnome 2.3 and high resolution"
date: 2010-05-12
forum: Desktop Environments
---

### Post by LinuxDOG on 2010-05-12
I've installed Ubuntu 10.4 and the gnome-panel appears half, as you can see in the attached picture, if I try resolutions over 1024x768.

If I kill the gnome-panel and it restarts, or if I change its properties, it became OK, but in startup it appears like the image.

I've tried other Gnome 2.3 based distributions and occurs the same issue. With Gnome 2.28 it doesn't occurs. Then ii seems a gnome 2.3 problem.

Anybody has the same problem?

PD: My grafic card is a Matrox G550.

---

### Post by jjduncan on 2010-05-15
I have the same problem on mine, after an upgrade from Karmic to Lucid (never had this problem on Karmic). No power button, no notification area, no running applications, no desktops. I've tried resetting the panels, which works until the next time I log on. I've reset the Gnome settings; no help there. A white rectangle (window? panel?) briefly appears and then disappears on the right side of the screen at logon, in the same place where the panels are cut off. If I right-click in the blank space where the panels would be, the context menu shows it to be the desktop, not a panel.
 
The easiest way I've found to bring them back to normal is to toggle "Show hide buttons" in the panel properties, which you have to do on both the top and bottom panels. But that only works until the next time I log on, and it doesn't matter whether that setting is on or off--either way, the panels are cut off at logon. It happens on both my main account and my guest account. Karmic was a clean install; I think the only package I added was restricted-extras.

---

### Post by tonus on 2010-05-16
This is [bug #572550]("https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/572550").

---

### Post by qwerty74321 on 2010-05-16
How do you install gnome 2.28? Because whenever i try through the  package manager it sends me it wants me to install swfdec-mozilla, and  then, epiphany-extensions. But they both want to remove each other. and I can't get any farther than that. gnome says it needs both of them to install it.

---

### Post by cariboo on 2010-05-16
> **qwerty74321 said:**
> How do you install gnome 2.28? Because whenever i try through the  package manager it sends me it wants me to install swfdec-mozilla, and  then, epiphany-extensions. But they both want to remove each other. and I can't get any farther than that. gnome says it needs both of them to install it.

Lucid comes with gnome 2.30 installed by default, why do you want to downgrade?

---

### Post by soltanis on 2010-05-17
Probably because the latest version has a bug.

When you are trying to downgrade your Gnome version, try first installing the two packages you mentioned with

```

apt-get --nodeps
# or if that doesnt work
apt-get --ignore-missing

```

To get it to stop doing dependency resolution.

---

### Post by qwerty74321 on 2010-05-17
All right I tried to use the --nodeps and --ignore-missing.

--nodeps gave me this.
```

$ sudo apt-get install gnome --nodeps
E: Command line option --nodeps is not understood

```--ignore-missing gave me this
```

$ sudo apt-get install gnome --ignore-missing
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  gnome: Depends: epiphany-extensions but it is not going to be installed
E: Broken packages

```sudo apt-get install gnome gives me the same message with or without ignore missing.and when i try to install epiphany it removes the other dependency, swfdec-mozilla.

@cariboo907: I have this problem if linuxdog says 2.28 works, then I want it so I can use gnome without seeing 1/3 of the panels.

---

