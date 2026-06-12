---
title: "Ho Do I Know What  Display To Use"
date: 2009-04-14
forum: Desktop Environments
---

### Post by smith3 on 2009-04-14
The comp I am using needs to be locked down so  end users can't get to it.

If i can get rid of all panels this will be handy. I still need to access a gui sometimes though.

I am trying to launch apps on a a gnome desktop from a terminal window over SSH, that want to know what display to use. The SSH session is on my laptop and the Program should run on the machine I am connected to. I want to be able to launch stuff like a terminal and file browser and gconf-editor.

IDK  command for terminal or file browser, but do know some commands that i need to run:


[FONT="System"]system:~$ gconf-editor
cannot open display:
Run 'gconf-editor --help' to see a full list of available command line options.
system:~$[/FONT]

 I opened help for that command  but am not sure how to determine the name of the display that gnome is running on.

Also if u guys know the command line to invoke a gnome file browser and a terminal session that would be great.

---

### Post by scragar on 2009-04-14
Try running```
export DISPLAY=':0.0'
```
And run the command again.

---

### Post by smith3 on 2009-04-14
Worked Great !

Thanks a lot scragar

now all i need is commands to run terminal and a file browser ;)

---

### Post by scragar on 2009-04-14
You can get away with using:

```
gnome-open ./
``` to open a file browser on the current directory(but for Xubuntu the file browser is **thunar** and for Ubuntu it's **nautilus**, not sure about other variants).

The terminal is called **gnome-terminal** if you don't know the distro's terminal though you can ALWAYS use **xterm**

---

### Post by scragar on 2009-04-14
After checking the distro independant method for opening a terminal is ```
x-terminal-emulator
```

I'm not sure about a file manager though. I will keep looking.


PS: add a single & at the end of a command to make it run in the background, so you can continue using that shell.

---

### Post by smith3 on 2009-04-14
scragar u are da bomb.

The commands for the the apps  work perfect and thanks for tossing the & trick in there , I would have been scratching my head.

On another note, where are u finding the listing of gnome commands so i don't have to ask u  how do you get sessions to run or this or that . 


Thanks again for quick response!

---

### Post by scragar on 2009-04-14
> **smith3 said:**
> On another note, where are u finding the listing of gnome commands so i don't have to ask u  how do you get sessions to run or this or that.

It's just creative googling. I found the x-terminal-emulator thing after googling "linux default terminal", the first result had a command to change it, I recognised the x-... part as being the same as x-window-manager to launch the default window manager(startx being the best way, but it's nice to know alternatives :p), so I tried it, and it worked.

Most of the stuff I've learnt from my own searching/needs or by reading threads on forums or on IRC.

---

