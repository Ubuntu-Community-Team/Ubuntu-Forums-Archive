---
title: "[SOLVED] A stupid question --  Compiz :s"
date: 2008-03-14
forum: Desktop Environments
---

### Post by alberto ferreira on 2008-03-14
I'm running Ubuntu Gutsy with gnome and compiz fusion, and sometimes compiz crashes.
I want to restore it from the console and then close the console and I've searched in the net for  a solution and what i get is:

compiz --replace &

after that command it launches compiz perfectly, but with or without the &, when I close the terminal (gnome-terminal), compiz shuts down. How do I replace compiz from terminal, and then close the terminal without killing compiz??


Thanks

---

### Post by luisromangz on 2008-03-14
That's the way Unix processes work. When the parent process is killed, its children processes are killed too. The & only forces a new process not to block the shell.

So you can't do that from a terminal window, although you can use that command from the run command dialog of your desktop environment, for example.

---

### Post by alberto ferreira on 2008-03-14
Thanks, is there a script that when run will do that for me?

---

### Post by luisromangz on 2008-03-14
Well you can't make an script use a graphical window as is the run command dialog (easily).

Are you just looking for a way to launch compiz, or it has to be from the command line?

You could use the session manager to launch compiz when gnome or kde starts, or using fusion-icon, which would place itself in the system tray as an icon.

---

### Post by alberto ferreira on 2008-03-14
I was looking for a GUI-based way to launch the program at any time without typing a thing - Just for curiosity :D

Thanks for your help luisromangz

---

### Post by luisromangz on 2008-03-14
Then fusion-icon should serve you well.

---

### Post by imronak on 2008-03-14
Its not a stupid question.

You can make a launcher. Thats what I have done. I use some 3rd part apps, which I install but those dont come up in the menu. So i make the launcher and then add it to the taskbar. :)

---

### Post by russo.mic on 2008-03-15
Just hit ALT + F2 to launch the RUN Program Dialog.  Then just type whatever into the box as if it was the terminal.

---

### Post by angry_johnnie on 2008-03-15
You're not far off.  Just type

```
compiz --replace & disown
```

Then you can close the terminal without killing compiz. :-)

---

### Post by mcduck on 2008-03-15
> **angry_johnnie said:**
> You're not far off.  Just type

```
compiz --replace & disown
```

Then you can close the terminal without killing compiz. :-)

or alternatively:

```
nohup compiz --replace &
```

---

### Post by alberto ferreira on 2008-03-15
I wasn't expecting so many replies :D


[COLOR="Blue"]_**Thank you very much to all of you!**_[/COLOR]

---

