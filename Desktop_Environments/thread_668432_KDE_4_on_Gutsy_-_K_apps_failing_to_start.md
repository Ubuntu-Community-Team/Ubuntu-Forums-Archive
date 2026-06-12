---
title: "KDE 4 on Gutsy - K apps failing to start"
date: 2008-01-15
forum: Desktop Environments
---

### Post by dshuck on 2008-01-15
I installed KDE4 on Gutsy last week and while it is pretty and all, it appears to be fairly useless with my particular configuration.    I can open apps that I have had all along, but when trying to open Dolphin, I get the little waiting bouncy icon and you see "Dolphin KDE" on the task bar, but it gives up after about 20 seconds and dies a quiet death.  The same behavior happens when I try to click "System Settings KDE4", "Find FIles/Folders", or pretty much any application that was installed with KDE4 as far as I can tell.

Does anyone have any suggestions for being able to open the new KDE4 programs?

Thanks!

---

### Post by OffAxis on 2008-01-15
try starting dolphin from a command prompt. When it fails, it'll print an error message to the terminal. Please post that error message.

---

### Post by dshuck on 2008-01-15
duh.... not sure why I didn't try that.  It is definitely clear what the error is, but I sure couldn't say why at this point. 

Here is kde4-dolphin
```
$ kde4-dolphin
bash: kde4-dolphin: command not found

```

It should be noted however, that I can run "$dolphin" and get a file manager.

kde4-konqbrowser
```
$ kde4-konqbrowser
bash: kde4-konqbrowser: command not found

```

Finally when trying to run systemsettings-kde4 I get a slightly more interesting error.
```
$ systemsettings-kde4
export: 5: bin:/sbin:/bin:/usr/bin/X11:/opt/e17/bin: bad variable name

```

I was wondering if perhaps it is something as simple as a problem where whatever bin directory KDE uses for its apps just didn't get added to the path variable properly, but when doing a locate on those files returned no matches.  

I can obviously apt-get them, but if things that are that essential to KDE didn't get installed, who knows?  And, I have no idea what is going on with that systemsettings-kde4 error.

Any advice would certainly be welcomed.  I am not ready to throw KDE out just yet. :)

---

### Post by GeneralZod on 2008-01-15
What is the output of

```

echo $PATH

```

and have you set it manually in .bashrc or .bashprofile? If so, check the syntax.

---

### Post by clau85 on 2008-01-16
> **dshuck said:**
> 
Here is kde4-dolphin
```
$ kde4-dolphin
bash: kde4-dolphin: command not found

```


on my system it's:
```

dolphin-kde4

```

---

