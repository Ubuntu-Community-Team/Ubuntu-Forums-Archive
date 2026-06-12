---
title: "Problem with Desktop file"
date: 2018-12-09
forum: Desktop Environments
---

### Post by mitmag on 2018-12-09
Hi folks:
  I have a very weird problem with Desktop files.
I have no problem creating the file. When I copy
the file to the Desktop, double click the icon, the
screen just blinks. That is all I get. No matter how
I create the file that's all I get. If I create a launcher
it does the same thing. I am missing something but
can't figure it out. It seems so easy but I have trouble.
Thanks for any help you can offer. I am using 14.04.

---

### Post by ajgreeny on 2018-12-09
Show us an example of text content of a .desktop file that does not work from your Desktop and also show us the permissions of that file with ```
ls -l *name*.desktop
```changing the word *name* to whatever you called the file, of course.

Please use **Code-Tags** for terminal output to show that text in a more readable format, the same as it is in the terminal, not as plain text. See my signature below for a **How-to**

---

### Post by mitmag on 2018-12-09
```

Here is the info you requested:

family_cube.desktop

#!/usr/bin/env xdg-open

[Desktop Entry]
Encoding=UTF-8
Version=1.0
Type=Application
Terminal=false
Exec=/home/scott/allegro5/opengl/family_cube
Name=family_cube

Permissions:
-rw-rw-r--1 scott scott 187 dec  9 16:31 family_cube.desktop


```

---

### Post by ajgreeny on 2018-12-09
Not sure about this but in Xubuntu .desktop files need to be executable for them to work, but that may not be the same for all DE versions.

Also make sure that script itself is executable with  ```
ls -l /home/scott/allegro5/opengl/family_cube
```

---

### Post by mitmag on 2018-12-10
I just discovered the problem. If I use a standalone program it works fine.
This particular program has to load 6 JPG files for textures on the cube. Does
anyone know how to handle that with a desktop file or a link?
Thanks for your time!

---

### Post by ajgreeny on 2018-12-10
No idea, I'm afraid, but if you let us see the script file content, I am assuming it is a script, and it may give us more chance of seeing what is not working.

I do not know allegro5, exactly what it does or is expected to do, but others may so keep looking here for other answers.

---

### Post by CatKiller on 2018-12-10
.desktop files are just ways to pretty up the running of commands for the desktop. They don't *do* anything themselves. They simply collect together a name, an icon, and a command to be run.

Once you've got your full command (and we have no idea what that is) working at the command line, you could put it in a .desktop file if you wanted a pretty way to launch it.

So if your full command is something like ```
/home/scott/allegro5/opengl/family_cube --load-images jpg1.jpg jpg2.jpg jpg3.jpg jpg4.jpg jpg5.jpg jpg6.jpg
``` you could put *that* in a .desktop file. As it stands, you're launching your thing with no arguments, which apparently doesn't work for whatever that thing is.

---

