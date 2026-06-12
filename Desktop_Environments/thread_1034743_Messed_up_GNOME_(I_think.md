---
title: "Messed up GNOME (I think"
date: 2009-01-09
forum: Desktop Environments
---

### Post by paradoxic on 2009-01-09
I was messing around earlier today trying to install a program called autodock (a scientific program used for working with protein models). I used aptitude to install a version of autodock which I tried to install from a repository for an older version of ubuntu (intrepid) I currently have hardy. When I ran aptitude to install autodock it listed a bunch of dependencies and things and also 3 packages to remove, the only one I can remember was ubuntu-desktop. I was searching the net and somewhere I read that it would be ok to let it remove that, but I think I made a bad move by accepting to go forward with install. After the install all my folders changed from the regular blue to brown and I couldent get them to go back. After I restarted my system and logged in nothing would load. I could only see my background image and nothing else. No icons, no menus, nothing. 

What can I do to reinstall ubuntu-desktop or something to get my system working again? Thanks a lot!

---

### Post by adamlau on 2009-01-09
You do not need ubuntu-desktop installed on Hardy. Drop into the root shell from GRUB and: 

```
apt-get remove autodock && apt get autoremove
```

This will remove autodock and its dependencies (hopefully). Restart:

```
shutdown -r now
```

---

### Post by paradoxic on 2009-01-09
I tried that and it said that autodock wasn't installed :confused:

When I tried to load nautilus in the terminal it gives this error:
```
No display specified
```

I also tried to run firefox and got a similar error:
```
Error: cannot open display
```

---

