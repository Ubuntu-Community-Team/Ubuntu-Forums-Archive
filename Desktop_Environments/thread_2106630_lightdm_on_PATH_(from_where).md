---
title: "lightdm on PATH (from where)?"
date: 2013-01-19
forum: Desktop Environments
---

### Post by noloader on 2013-01-19
Hi All,

I'm trying to track down where lightdm is added to my PATH:

```
$ echo $PATH
/usr/lib/lightdm/lightdm:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
```I checked in /etc/environment, and its not there. I also checked in ~/.profile, and it not there.

Am I the only guy who thinks letting a window manager be a security manager is a bad idea? We've already seen its incompetence. Confer: [https://bugs.launchpad.net/linuxmint/+bug/967938](https://bugs.launchpad.net/linuxmint/+bug/967938) and[ https://bugs.launchpad.net/linuxmint/+bug/967935]("https://bugs.launchpad.net/linuxmint/+bug/967935").

Where is lightdm added to PATH?

Jeff

---

### Post by dgharmon on 2013-01-19
> **noloader said:**
> I'm trying to track down where lightdm is added to my PATH:

[lightdm question]("http://ubuntuforums.org/showthread.php?t=1937283&ei=BT_7UMf9N4HA0QXLwoDQDA&usg=AFQjCNG_EmJ0UsjuEk4EW6kQMcK6fsZdOA")

---

### Post by noloader on 2013-01-20
> **dgharmon said:**
> [lightdm question]("http://ubuntuforums.org/showthread.php?t=1937283&ei=BT_7UMf9N4HA0QXLwoDQDA&usg=AFQjCNG_EmJ0UsjuEk4EW6kQMcK6fsZdOA")
Thanks dgharmon. So, I see it was added somewhere. That answers the "WHY". Next is the "HOW".

How do I remove it from my PATH? It does not appear to be added in the ways I know.

Jeff

---

### Post by noloader on 2013-01-21
> **dgharmon said:**
> [lightdm question]("http://ubuntuforums.org/showthread.php?t=1937283&ei=BT_7UMf9N4HA0QXLwoDQDA&usg=AFQjCNG_EmJ0UsjuEk4EW6kQMcK6fsZdOA")
Related question: I'm using gnome-session-fallback (and not the netbook/tablet stuff) for the desktop.

Why is it even running in Gnome Classic mode?

Jeff

---

