---
title: "[xfce] command works from terminal, not from menu"
date: 2008-04-01
forum: Desktop Environments
---

### Post by liniaal on 2008-04-01
Hi people,

i'm trying to embed this command in my brand new xml'ed xfce menu:
```
exo-open `zenity --file-selection --directory`
```
however it does not launch any file selection window, it just keeps quiet :(
how can it be that i can run this from off the terminal but not from the menu??

also, this command here does launch correctly from the menu:
```
ssh -X <user>@<host> `zenity --entry`
```

any help is much appreciated.

---

### Post by mali2297 on 2008-04-02
**exo-open** will only open one of the Xfce preferred applications, that is: WebBrowser, MailReader or TerminalEmulator.

Try with the shortened command
```

zenity --file-selection --directory

```

Slightly off-topic, [Xdialog]("http://xdialog.free.fr/") is an alternative to Zenity with fewer dependencies, it might be interesting if you don't use Gnome.

---

### Post by liniaal on 2008-04-02
> **mali2297 said:**
> **exo-open** will only open one of the Xfce preferred applications, that is: WebBrowser, MailReader or TerminalEmulator.

Try with the shortened command
```

zenity --file-selection --directory

```

Slightly off-topic, [Xdialog]("http://xdialog.free.fr/") is an alternative to Zenity with fewer dependencies, it might be interesting if you don't use Gnome.

nice, thank you. but the point is really that after selecting, i want to open the folder in thunar. now i realize that putting thunar in front, in stead of exo-open, would do better.
EDIT: and thanks for the tip, but i seem to already have some apps in use that can't do without some gnome libs, plus i think i like the gnome file selector better (bookmarks etc!)

---

### Post by liniaal on 2008-04-02
> **liniaal said:**
> nice, thank you. but the point is really that after selecting, i want to open the folder in thunar. now i realize that putting thunar in front, in stead of exo-open, would do better.
EDIT: and thanks for the tip, but i seem to already have some apps in use that can't do without some gnome libs, plus i think i like the gnome file selector better (bookmarks etc!)

but, my problem is still not fixed. zenity doesn't even give a window, it doesn't seem to show up.

---

### Post by liniaal on 2008-04-11
so now i'm down to writing my own window in pygtk. it's lots of fun :D now just find out how to start a new task/process from within python code.

---

