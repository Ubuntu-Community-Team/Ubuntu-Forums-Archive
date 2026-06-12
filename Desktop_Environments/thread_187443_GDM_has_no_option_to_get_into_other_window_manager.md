---
title: "GDM has no option to get into other window managers"
date: 2006-06-03
forum: Desktop Environments
---

### Post by Zeroedout on 2006-06-03
Hello, I just did a fresh install of dapper. I got everything up and running, but when I installed flwm, there was no option in GDM. I installed it through Synaptic, and in Breezy there was an option in GDM's session menu. Is this a bug in dapper, or am I doing something wrong? To make sure it was not just the flwm package, I also installed twm, and the same thing happened, installed fine, but no option in GDM. Any help would be appreciated. Thank you.

---

### Post by bluevoodoo1 on 2006-06-03
Easy to fix. Many WMs don't create an entry in the GDM, but you can do it manually, it's very easy.

To create the flwm.desktop entry...
```
sudo gedit /usr/share/xsessions/flwm.desktop
```

then paste the following, making sure the path to Exec=flwm is correct!!! (it's probably /usr/bin/flwm or simply flwm)

```

[Desktop Entry]
Encoding=UTF-8
Name=flwm
Comment=flwm window manager
Exec=flwm
TryExec=flwm
Type=Application
```

logout and it should be a session to login to. 

Follow similar steps for other window managers that do not automatically create sessions.

---

### Post by Zeroedout on 2006-06-03
Hi, thank you for the info, but that was not the intention of my post. I am wondering why the package did not create the option in GDM. If it did so in Breezy, then it should do so in Dapper, unless the admins of the distro had good reasons to remove the feature. If they did not intentionally do that, then I need to file a bug report as they may not be aware of the issue. If it is just my setup that is being affected, then that would be relevent info for a bug report. So back to the question, Has anyone else had this same issue?  My apologies for the ambigious first post.

---

### Post by tript on 2006-06-03
[QUOTE=bluevoodoo1]Easy to fix. Many WMs don't create an entry in the GDM, but you can do it manually, it's very easy.

To create the flwm.desktop entry...
```
sudo gedit /usr/share/xsessions/flwm.desktop
```

then paste the following, making sure the path to Exec=flwm is correct!!! (it's probably /usr/bin/flwm or simply flwm)

```

[Desktop Entry]
Encoding=UTF-8
Name=flwm
Comment=flwm window manager
Exec=flwm
TryExec=flwm
Type=Application
```

logout and it should be a session to login to. 

Follow similar steps for other window managers that do not automatically create sessions.[/QUOTE]
I have tried this after installing pekwm...with no success.  Any other suggestions would be appreciated.  thanks.

---

### Post by Zeroedout on 2006-06-04
[quote=tript]I have tried this after installing pekwm...with no success.  Any other suggestions would be appreciated.  thanks.[/quote]

Well, it's good to know my situation is not unique, perhaps a post to ubuntu's bugzilla or whatever form of bug tracking they use is in order. Out of curiousity, did it automatically create an option in GDM when (if) you installed it in breezy?

---

