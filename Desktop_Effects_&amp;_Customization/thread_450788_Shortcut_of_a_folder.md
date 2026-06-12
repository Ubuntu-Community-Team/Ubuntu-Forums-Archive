---
title: "Shortcut of a folder"
date: 2007-05-21
forum: Desktop Effects &amp; Customization
---

### Post by tkoutso on 2007-05-21
I want to make a shortcut  of a folder on the desktop. I right-click the folder, I chose "make link", but I receive an error message. What should I do?

---

### Post by murat13 on 2007-05-21
You can use **ln ** command for that.Just open a terminal window then type something like this
**ln -s /boot /home/yourname/Desktop/**

---

### Post by tkoutso on 2007-05-21
Can I use a launcher instead? Or is there any way of my first attempt working (make link)?

---

### Post by Znupi on 2007-05-21
Using a Launcher:
Name: the name of the folder
Command: nautilus /path/to/folder
Comment: whatever you wish.
You can choose an icon, too.
Click OK :P.

If you're using Kubuntu or something that is not on GNOME, you'll probably have to change nautilus to whatever your file browser is.

---

### Post by tkoutso on 2007-05-21
I am sorry, let's say the folder is: media/disc/abc

The command should be:

nautilus /path/to/media/disc/abc

???

---

### Post by Znupi on 2007-05-21
no, it should be
```

nautilus /media/disc/abc

```
:)

---

