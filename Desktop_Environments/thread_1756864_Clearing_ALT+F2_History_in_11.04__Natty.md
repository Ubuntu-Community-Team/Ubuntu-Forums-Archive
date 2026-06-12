---
title: "Clearing ALT+F2 History in 11.04 / Natty"
date: 2011-05-12
forum: Desktop Environments
---

### Post by magicalplug on 2011-05-12
Hi.

How do I clear the ALT+F2 'run a command' history that appears in Ubuntu Natty? The Terminal command I used to use in 10.10 to clear the history no longer works in the new Unity command launcher. I've tried searching within files on my hard drive to see if I can find where the data is stored, but no such luck. Any help appreciated!

Cheers

---

### Post by mc4man on 2011-05-12
Most likely in gconf-editor 
apps/gnome-settings/gnome-panel/history-gnome-run 
R. click > edit on history-gnome-run
(you could also work out a terminal command to clear or unset

to clear
```
gconftool-2 -s -t string  /apps/gnome-settings/gnome-panel/history-gnome-run  []
```

A log out/in to realize

---

### Post by magicalplug on 2011-05-12
That's the one! Thank you :)

---

### Post by mc4man on 2011-05-13
Just as an aside to this - 
if one had a some commands they'd like to always be shown in the history but still clear out any other accumulated ones then instead of the [] in above command you could go 
gconftool-2 -s -t string  /apps/gnome-settings/gnome-panel/history-gnome-run  [command,command]

That would clear out all but whatever was put into the []

From the current unity side (natty, 11.10+ may bring changes, other interesting things), this could also be done from a launcher icon quicklist entry, just expose it, (r. click on icon, select.

So I might add to something like shown  [here, ( a utility menu icon]("http://ubuntuforums.org/showthread.php?p=10778758#post10778758")) as such

```
[ClearRun Shortcut Group]
Name=Clear Run History
Exec=gconftool-2 -s -t string  /apps/gnome-settings/gnome-panel/history-gnome-run  []
TargetEnvironment=Unity

```

or 
```
[ResetRun Shortcut Group]
Name=Reset Run History
Exec=gconftool-2 -s -t string  /apps/gnome-settings/gnome-panel/history-gnome-run  [command,command,command]
TargetEnvironment=Unity
```

---

### Post by joopbraak on 2011-11-09
In Oneiric you have to install dconf-tools, then open dconf-editor, then  go to "/desktop/unity/runner/history", then click on "Set to Default",  then logout, log in again, and then you're done !!!
 
 I can't believe how easy everything has become with Unity !
 
 Good job, Canonical !

---

