---
title: "Gnome-Shell Broken After Update and Extensions Install"
date: 2011-12-24
forum: Desktop Environments
---

### Post by Elie-M on 2011-12-24
hello my gnome-shell isnt loading, no panels, no alt+f2, no terminal, nothing works, I only see the wallpaper.

I deleted dconf to reset the user settings, didnt work
I deleted the gnome-shell personal user configuration files (the one that takes me back to the stock gnome-shell desktop), that didnt work too
I purged gnome-shell then re-installed it, didnt work.

I log into gnome classic and do some commands I saw elsewhere and get:


```
elie-m@elie-m:~$ sudo apt-get remove gnome-shell-extensions-*
[sudo] password for elie-m: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package gnome-shell-extensions-*
E: Couldn't find any package by regex 'gnome-shell-extensions-*'
elie-m@elie-m:~$ DISPLAY=:0 gnome-shell --replace &
[1] 4854
elie-m@elie-m:~$ 
GLib-GIO-ERROR **: Settings schema 'org.gnome.shell.extensions.musicintegration' does not contain a key named 'musiclabel'
gnome-shell-calendar-server[4864]: Got HUP on stdin - exiting
```

anyone can help with this? I can provide any information needed.. I'm on ubuntu 11.10 fully updated.

---

### Post by hhh on 2011-12-24
I had gnome-shell crap out on me a couple of times after installing a bad extension, I solved it by deleting one of the hidden folders in my home folder (I think it was .local).

BTW, the command you're looking for is...```
sudo apt-get purge gnome-shell-extensions*
```

---

### Post by lolpenguin on 2011-12-25
org.gnome.shell.extensions.musicintegration breaks GNOME Shell in your case. If an extension is faulty, it will cause GNOME Shell to crash in its entirety (like Firefox).
Delete the extension folder from /usr/share/gnome-shell/extensions/musicintegration@*. If it isn't there, check ~/.local/share/gnome-shell/extensions/musicintegration@*.

---

### Post by Elie-M on 2011-12-25
> **hhh said:**
> I had gnome-shell crap out on me a couple of times after installing a bad extension, I solved it by deleting one of the hidden folders in my home folder (I think it was .local).

BTW, the command you're looking for is...```
sudo apt-get purge gnome-shell-extensions*
```

```
elie-m@elie-m:~$ sudo apt-get purge gnome-shell-extensions*
[sudo] password for elie-m: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package gnome-shell-extensions*
E: Couldn't find any package by regex 'gnome-shell-extensions*'
```


and /usr/share/gnome-shell/extensions/musicintegration@* doesnt exist, and I already deleted all the extensions from ~/.local/share/gnome-shell/extensions/

---

### Post by Elie-M on 2012-01-07
Innocent bump :wink:

---

### Post by lolpenguin on 2012-01-07
Make sure there is NOTHING in /usr/share/gnome-shell/extensions/ AND ~/.local/share/gnome-shell/extensions/, if it still doesn't work, reinstall gnome-shell.

---

### Post by Elie-M on 2012-01-08
> **lolpenguin said:**
> Make sure there is NOTHING in /usr/share/gnome-shell/extensions/ AND ~/.local/share/gnome-shell/extensions/, if it still doesn't work, reinstall gnome-shell.

did not solve it, and nothing really is. so, im formatting and abandoning this thread, i've had enough of linux ****.

thanks all for helping. :)

---

### Post by rudihawk on 2012-01-25
> **lolpenguin said:**
> org.gnome.shell.extensions.musicintegration breaks GNOME Shell in your case. If an extension is faulty, it will cause GNOME Shell to crash in its entirety (like Firefox).
Delete the extension folder from /usr/share/gnome-shell/extensions/musicintegration@*. If it isn't there, check ~/.local/share/gnome-shell/extensions/musicintegration@*.

This response helped me solve my Gnome-Shell issues. Thank you! :) 

I didn't have the exact same problem, but you helped me find a solution. ;)

---

