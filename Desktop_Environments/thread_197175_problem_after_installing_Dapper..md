---
title: "problem after installing Dapper."
date: 2006-06-15
forum: Desktop Environments
---

### Post by bettermanlamia on 2006-06-15
K i installed it...restarted the comp...and then it comes up with just a command line...nothin else. asks me to login in command line then just a propt is givin to me...no gnome desktop or anything...what did i do wrong? i installed it like any other linux.

---

### Post by taurus on 2006-06-15
Did you install the server version or the desktop version?  What happens if you type "startx" at the prompt?  If you get an error about command not found, then you need to install Gnome as
```

sudo apt-get update
sudo apt-get install ubuntu-desktop

```

---

### Post by bettermanlamia on 2006-06-15
[QUOTE=taurus]Did you install the server version or the desktop version?  What happens if you type "startx" at the prompt?  If you get an error about command not found, then you need to install Gnome as
```

sudo apt-get update
sudo apt-get install ubuntu-desktop

```[/QUOTE]
its the server version. Looked better then the live version. wasnt sure really which one to get. :(
i tried entering startx into the command prompt. and it said command not found.

Now u said i have to install gnome.
i'll enter the code u sent into the prompt and hopefully it will work. :)
although i thought Ubuntu automaticly installed gnome...


EDIT 1: no online connection for me. i dont have a modem or ethernet card that works with linux :( or just cant get it to work.

EDIT 2: i put in sudo apt-get install ubuntu-desktop and it came up with "E: Couldn't find package ubuntu-desktop"

---

### Post by angkor on 2006-06-15
[QUOTE=bettermanlamia]its the server version.[/QUOTE]

The server edition does not come with unwant stuff like a graphical desktop. ;)

Just download the Desktop CD and start over, maybe it'll pick up your ethernet, at least you'll get a desktop.

---

### Post by bettermanlamia on 2006-06-15
[QUOTE=angkor]The server edition does not come with unwant stuff like a graphical desktop. ;)

Just download the Desktop CD and start over, maybe it'll pick up your ethernet, at least you'll get a desktop.[/QUOTE]
ooooo ok. Thanks. I've got it downloading now. ^_^;

O yea by the way my computer doesnt have a enternet card. it has a modem but i think its a winmodem or something like that. :( and i heard those things dont work on linux. so:(
thanks.

EDIT: oo i just thought of a question, What is a good cheap ethernet card or a way to get a wireless internet by way of USB on linux. I have a USB wireless set up for my brother im sure he wont mind me using it to get updates now and then. so the computer doesnt die. :razz: 
is it possiable to get a USB wireless internet on linux?

---

