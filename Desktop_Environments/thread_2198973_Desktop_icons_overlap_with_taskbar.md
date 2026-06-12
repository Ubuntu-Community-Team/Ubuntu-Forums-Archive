---
title: "Desktop icons overlap with taskbar"
date: 2014-01-11
forum: Desktop Environments
---

### Post by Previous1 on 2014-01-11
After boot, desktop icons overlap with the top taskbar. Opening the taskbar preferences sets it back to the correct position; I haven't found specifics to this, but the "reset" may be similar to an earlier [issue]("http://ubuntuforums.org/showthread.php?t=2194400").

A workaround may be to start/stop the preferences at boot, but I was hoping to solve the underlying issue (especially when it's a recent one). Using Xubuntu 12.04 with XFCE 4.8

---

### Post by Toz on 2014-01-11
Looks like struts may be disabled (though I'm not sure why open the taskbar preferences resets it). What does the following command return?
```
xfconf-query -c xfce4-panel -lv | grep struts
```
...it will display whether struts are enabled and what setting its at.

---

### Post by ajgreeny on 2014-01-11
Have you got a selection tick in the "Don't reserve space on borders" in your panel Preferences -> Display tab?

---

### Post by Toz on 2014-01-11
> **ajgreeny said:**
> Have you got a selection tick in the "Don't reserve space on borders" in your panel Preferences -> Display tab?

I don't believe 4.8 has this option visible in the preferences dialog. To manage this setting you had to use the hidden struts property. 
I don't have a 4.8 install handy to check.

---

### Post by Previous1 on 2014-01-12
xf-conf didn't return an entry, and indeed, I don't have an option for "[COLOR=#000000]Don't reserve space on borders". I've tried adding "disable-struts" and setting it to "false", but it still needs a refresh.[/COLOR]

---

### Post by Toz on 2014-01-12
> **Previous1 said:**
> I've tried adding "disable-struts" and setting it to "false", but it still needs a refresh.
How did you try adding it? Which channel/property did you use?

Does clearing your saved sessions cache help? To clear your sessions cache (in 4.8), delete the ~/.cache/sessions directory while _not_ logged in (from the first virtual console - Ctrl+Alt+F1).

---

### Post by Previous1 on 2014-01-12
I've used this command: xfconf-query -c xfce4-panel -p /panels/panel-0/disable-struts -n -t bool -s false

Clearing sessions didn't help but, oddly enough, changing the theme from Bluebird to Greybird did..

Thanks for the help.

---

### Post by ajgreeny on 2014-01-12
Another alternative is to use the ppa for xfce 4.10 which works faultlessly in 12.04
[https://launchpad.net/~xubuntu-dev/+archive/xfce-4.10?field.series_filter=precise](https://launchpad.net/~xubuntu-dev/+archive/xfce-4.10?field.series_filter=precise)
You will then find that you have the option for reserving space on borders.  Sorry, I forgot I was on 4.10, and didn't really notice you are using 4.8.

---

