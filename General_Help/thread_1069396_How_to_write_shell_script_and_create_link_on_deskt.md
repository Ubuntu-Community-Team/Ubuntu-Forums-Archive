---
title: "How to write shell script and create link on desktop?"
date: 2009-02-13
forum: General Help
---

### Post by UranUtan on 2009-02-13
Hi,

I would like to create a script that execute this line:
```
VBoxManage startvm MyVM1
```
Then have a shortcut on the desktop so that I can execute the command above in one single click.

Can you please show me how to to that?

Thanks in advance.

---

### Post by tjwoosta on 2009-02-13
why have a script?

just right click the desktop and choose create launcher

put your command in the box that says command


forgive me if im missing something, i have not used gnome for some time now

---

### Post by UranUtan on 2009-02-14
Super cool, thanks. Didn't know it's that simple.

---

### Post by dcstar on 2009-02-14
> **UranUtan said:**
> Hi,

I would like to create a script that execute this line:
```
VBoxManage startvm MyVM1
```
Then have a shortcut on the desktop so that I can execute the command above in one single click.

Can you please show me how to to that?

Thanks in advance.

The best way to learn how to do a shell script is to look at what already exists in your system and make a copy which you modify to your own needs.

Copy something like the /etc/rmt script to your Desktop and then modify it to your needs (open a terminal and do these commands):

```
mkdir Scripts
cp /etc/rmt ~/Scripts/my-script
chmod 777 ~/Scripts/my-script
gedit ~/Scripts/my-script
```

Then you modify the script (you can change/delete all the comments below the first line) with the commands you need, and make a launcher as per the instructions in the other post.

---

### Post by UranUtan on 2009-02-14
Wow Ok it's even better (chain several cmd in a single script).  chmod 777 was the part I was missing. Thanks for the quick lesson.

---

