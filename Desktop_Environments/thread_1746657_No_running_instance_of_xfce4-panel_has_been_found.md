---
title: "No running instance of xfce4-panel has been found"
date: 2011-05-02
forum: Desktop Environments
---

### Post by LarsKongo on 2011-05-02
I have an annoying little problem. When I installed xfce4 and logged on for the first time it asked me to setup my panels. I selected to use a blank panel. I placed it at the bottom, but for some reason it crashed. No big deal, it asked me to create another panel with the message "no running instance of xfce4-panel has been found."

Now every time I login I get this message: "no running instance of xfce4-panel has been found." A panel settings window also opens.

After the message everything seems to be working fine. The panel seems to save my settings every time I log-off etc, but the message won't go away every time I login.

I've tried to reset (delete) *~/.config/xfce4*
I've tried to delete everything in *~/.cache/sessions/*
I've tried to manually save my session.
I've tried to disable xfce4-settings-helper in autostart.
I've checked the *~/.config/xfce4-session* folder which is empty.

Nothing works. :/

---

### Post by ownaginatious on 2011-05-13
Not sure if this matters to you anymore, but I figure I'll mention it just in case someone has this issue in the future.

Anyway, to fix the problem - you have to do everything you mentioned, but _**while logged out of xfce4**_.

Do it in a different desktop-manager or from the console.

---

### Post by tvdkolk on 2011-08-22
> **ownaginatious said:**
> Anyway, to fix the problem - you have to do everything you mentioned, but _**while logged out of xfce4**_.

Do it in a different desktop-manager or from the console.

Pardon my ignorance, but how do I log out of xfce4?

I'm quite new to xubuntu...

Thank you for your help.

---

### Post by ownaginatious on 2011-08-22
Sorry, I should have been more specific. What you have to do is kill the xserver (so that you drop to the console) and then run the commands.

You restart the xserver (to get back to the GUI) with

```
startx
```

once you're done entering the commands there.

Now I *think* the way you kill the xserver on Ubuntu is holding CTRL-ALT-Backspace.

If that doesn't work, you can open a terminal and do 

```
sudo kill -9 processnumber
```

Where process number is the process ID (PID) of the xserver.

You should be able to find that by doing

```
sudo ps aux | grep xserver
```

Hope that helps!

---

### Post by tvdkolk on 2011-08-22
> **ownaginatious said:**
> Hope that helps!
It sure did! Thanks!

---

