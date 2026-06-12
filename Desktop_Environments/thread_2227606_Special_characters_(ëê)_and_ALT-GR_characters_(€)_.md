---
title: "Special characters (ëê) and ALT-GR characters (€) settings gone after reboot"
date: 2014-06-03
forum: Desktop Environments
---

### Post by rvdmeijden+launchpad on 2014-06-03
Hi,

Since I upgraded to 14.04 I have the problem that after a reboot I have to re-configure the keyboard to get special characters like ëéèê and € (ALT-GR+5). There are so many places that have settings about the keyboard layout that I do not know which is "the boss". There are settings in the Gnome Tweak tool, in the settings and keyboard layout, modifier-key short-cut in the keyboard short-cut list and via "dpkg-reconfigure keyboard-configuration"


 To get these characters I have to run the following command after each reboot.

```
sudo dpkg-reconfigure keyboard-configuration
```

Where should I change what and how can I make this permanent (again)?

Thanks in advance for the help, for this is driving me crazy ;)

---

### Post by TheFu on 2014-06-03
**sudo dpkg-reconfigure console-setup**
That is the granddaddy of them all. Should work across local, remote and X/windows ... unless you've overridden input methods in those separately.

---

### Post by rvdmeijden+launchpad on 2014-06-07
> **TheFu said:**
> **sudo dpkg-reconfigure console-setup**
That is the granddaddy of them all. Should work across local, remote and X/windows ... unless you've overridden input methods in those separately.

Thanks TheFu, your command was what I was missing. The combination of both commands have finally fixed my issues.

```
sudo dpkg-reconfigure keyboard-configuration
sudo dpkg-reconfigure console-setup


```

This did the trick

Thanks again

---

### Post by rvdmeijden+launchpad on 2014-06-22
Quick update. The problem re-creates itself when gnome shell restarts itself or when I execute
gnome-shell --repace

After a reboot all is well.

---

### Post by rvdmeijden+launchpad on 2014-06-22
I have set-up an extra keyboard layout. and have changed the short-cut combination to change the layout to ctrl+alt+space (super+space did not work) and by switching layouts after a shell restart I get my special keys back. 

Not a solution but a workable workaround.

---

