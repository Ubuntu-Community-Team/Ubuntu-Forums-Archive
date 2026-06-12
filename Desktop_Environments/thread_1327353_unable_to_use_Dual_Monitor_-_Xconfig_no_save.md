---
title: "unable to use Dual Monitor - Xconfig no save"
date: 2009-11-15
forum: Desktop Environments
---

### Post by putz3000 on 2009-11-15
I am using a Dell XPS M1530 and would like to use an external display with it to create an extended desktop.  My video card is an nVidia card.  I can go into the nVideia card settings and select seperate "X" session, but when I try to save and merge the settings to the xconfig file, it says it is unable to save the backup so to date I have been unable to use the external monitor.  

Anyone else deal with this and have you figured out how to make it work?

Thanks

---

### Post by unamanic on 2009-11-15
It can't save the backup because you don't have sufficient privileges as a normal user.  From the command line try:
```

sudo nvidia-settings 

```or if you prefer pointy clicky interaction you can hit alt-f2 and enter:
```

gksu nvidia-settings

```

---

### Post by melcgy on 2009-11-15
try using the terminal as root, su then password when prompted. Then type in "nvidia_settings" when it opens make your changes and save.

---

