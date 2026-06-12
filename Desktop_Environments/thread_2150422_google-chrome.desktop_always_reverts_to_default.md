---
title: "google-chrome.desktop always reverts to default"
date: 2013-06-01
forum: Desktop Environments
---

### Post by session13 on 2013-06-01
I want Chrome Browser open a window by every computer start. There is the file *~/.config/autostart/google-chrome.desktop *where I can change option
```
Exec=/opt/google/chrome/google-chrome --no-startup-window
``` by removing *--no-startup-window *parameter. After first reboot it works as expected, a new browser window is open automatically. But after next restart, the file *google-chrome.desktop *always returns to its default state. 

What can I do to edit this file permanently?

Thanks

---

### Post by vasa1 on 2013-06-01
Hi could you please explain what you want? Do you want Chrome to start automatically each time you log in?

---

### Post by session13 on 2013-06-02
ASAIK Chrome Browser is starting up each time I log in, thanks to the file*~/.config/autostart/google-chrome.desktop. *What I want is to permanently remove the *[COLOR=#000000][FONT=Ubuntu Mono]--no-startup-window [/FONT][/COLOR]*parameter, because I want Chrome Browser not only start at log in but also open a new window, so that I won't have to do in manually.

---

### Post by deadflowr on 2013-06-02
You can try setting the file as immutable.

edit/save your file to your liking, and then run

```
sudo chattr +i filename
```
change filename to the actual path and file name.
This will make the file unchangeable, hopefully.

---

### Post by session13 on 2013-06-05
It works, thanks :)

---

