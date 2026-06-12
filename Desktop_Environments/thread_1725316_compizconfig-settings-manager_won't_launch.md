---
title: "compizconfig-settings-manager won't launch"
date: 2011-04-09
forum: Desktop Environments
---

### Post by jeremyjjbrown on 2011-04-09
I can't seem to launch compizconfig-settings-manager. Compiz is running because I get the effects I set up last time I used it. 

If I try to launch to from the terminal I get.
```
compizconfig-settings-manager: command not found

```

I tried to enter just "compiz" into the terminal to see if description text would come up and my whole windows manager went crazy and I lost window borders. It threw this error.

```
WARNING: Application calling GLX 1.3 function "glXCreatePixmap" when GLX 1.3 is not supported!  This is an application bug!
```

If I reinstall it with aptitude will I loose my settings?

---

### Post by Enigmapond on 2011-04-09
You won't lose any settings. The only way  that would happen is if you purge the config file. Just remove it first (not purge) and reinstall.

---

### Post by matty abbo on 2011-04-09
are you sure you have installed all the correct packages for compiz, if not it won't run, try looking on synaptic

---

### Post by jeremyjjbrown on 2011-04-09
Well I removed and reinstalled compizconfig-settings-manager with both aptitude and synaptic and it still will not launch via the terminal or System>Preferences.

Does anyone have an idea what is going on here?

---

### Post by jeremyjjbrown on 2011-04-10
Now I have backup up my compiz-config file and purged compizconfig-settings-manager. I reinstalled and found the following errors

```
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
Rebuilding /usr/share/applications/desktop.en_US.cache...
WARNING: System locale is invalid
```

So I purged again and ran...

```
sudo apt-get locale-gen
sudo apt-get clean all
sudo apt-get update
```

And then reinstalled. But I still have the same errors and compizconfig-settings-manager will not launch.

---

### Post by stinkeye on 2011-04-10
> **jeremyjjbrown said:**
> I can't seem to launch compizconfig-settings-manager. Compiz is running because I get the effects I set up last time I used it. 

If I try to launch to from the terminal I get.
```
compizconfig-settings-manager: command not found

```

I tried to enter just "compiz" into the terminal to see if description text would come up and my whole windows manager went crazy and I lost window borders. It threw this error.

```
WARNING: Application calling GLX 1.3 function "glXCreatePixmap" when GLX 1.3 is not supported!  This is an application bug!
```

If I reinstall it with aptitude will I loose my settings?

compizconfig-settings-manager is launched from the terminal with
```
ccsm
```

or
from Menu > preferences > CompizConfig Settings Manager.

---

### Post by jeremyjjbrown on 2011-04-10
I've discovered that my issue is due to a locale setting issue so i'm opening a different thread with an appropriate title and marking this one as solved.

ubuntuforums.org/showthread.php?t=1726022

---

