---
title: "Skype not showing windows"
date: 2018-05-13
forum: Desktop Environments
---

### Post by grefa on 2018-05-13
Hi everybody,

I'm trying to get Skype to work in Ubuntu 18.04. I installed it and started it.
The Skype status appears in the upper right corner and the big blue Skype icon
appears in the dash; however, when I click on it, nothing happens. No windows
or login dialogs, nothing. What can I do to resolve this problem?

---

### Post by ajgreeny on 2018-05-13
Try disabling the "Launch Skype in the background" setting and starting it with a full window which you can possibly then minimise to the panel icon as usual;  It works for me this way but if I use the "Launch in the background" setting it does exactly what you see.

This appears to be a known problem if you read the Skype forums; see [https://answers.microsoft.com/en-us/skype/forum/skype_linux-skype_startms-skype_installms/upgraded-to-the-latest-skype-linux-version-but/34553112-f42c-4740-a435-a64ddf3ad89f](https://answers.microsoft.com/en-us/skype/forum/skype_linux-skype_startms-skype_installms/upgraded-to-the-latest-skype-linux-version-but/34553112-f42c-4740-a435-a64ddf3ad89f) plus a number of other threads there.

---

### Post by monkeybrain20122 on 2018-05-13
Try start it in the terminal and see if there is any error, the command to type in the terminal is

```
skypeforlinux
```

(not skype)

---

### Post by grefa on 2018-05-15
I tried that and I couldn't see any errors.

---

### Post by grefa on 2018-05-15
> **ajgreeny said:**
> Try disabling the "Launch Skype in the background" setting and starting it with a full window which you can possibly then minimise to the panel icon as usual;  It works for me this way but if I use the "Launch in the background" setting it does exactly what you see.



How can I get to settings? Even if I right click the upper-right icon, I don't see a "Settings" option.

---

### Post by grefa on 2018-05-15
To be more precise: when I click on the Skype icon on the upper-right corner, I get the following options:

-Status
-Open Skype
-Sign Out (grayed out, since I cannot sign in)
-Quit Skype

If I click "Show Skype", I get the Skype icon in the Activities panel (I use Gnome).
However, if I click that icon, I only get the "Quit" option. What am I doing wrong?

---

### Post by astralspark on 2018-10-23
Had the same problem and the fix is very easy. Windows is actually showing, but out of monitor screen. Open skype and then just press **ALT+F7** (to catch and move window) and then use arrow keys, most certainly **left arrow**, to move Skype window, so You can see it (hit it few times). When it will be visible, press **Enter** ;)

---

### Post by amarnadh-janaswamy on 2018-12-27
> **astralspark said:**
> Had the same problem and the fix is very easy. Windows is actually showing, but out of monitor screen. Open skype and then just press **ALT+F7** (to catch and move window) and then use arrow keys, most certainly **left arrow**, to move Skype window, so You can see it (hit it few times). When it will be visible, press **Enter** ;)


Thanks AstralSpark this worked for me Thanks for your simple catch:D:D:grin:

---

