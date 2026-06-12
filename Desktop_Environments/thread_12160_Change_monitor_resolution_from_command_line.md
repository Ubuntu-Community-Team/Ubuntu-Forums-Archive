---
title: "Change monitor resolution from command line"
date: 2005-01-22
forum: Desktop Environments
---

### Post by AndyL on 2005-01-22
I am a complete newcomer, so please bear with me!. I have installed Ubunutu at work, with a monitor that supports high resolution. Bringing the PC home, my monitor doesn't support the resolution that it's now set to. How can I change the default resolution from the command line?

---

### Post by Ste on 2005-01-22
[QUOTE=AndyL]I am a complete newcomer, so please bear with me!. I have installed Ubunutu at work, with a monitor that supports high resolution. Bringing the PC home, my monitor doesn't support the resolution that it's now set to. How can I change the default resolution from the command line?[/QUOTE]
 You can edit your XFConfig86-4 file with gedit or if you insist on using command line try
```
 sudo pico /etc/X11/XF86Config-4
```

Think that's the command. You are using warty right ?
Maybe someone else can concur my command ?
Also make a backup of the file before editing just in case.

```
sudo cp /etc/X11/XF86Config-4 /etc/X11/XF86Config-4.bak
```

Best of luck.

---

