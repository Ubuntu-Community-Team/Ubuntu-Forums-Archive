---
title: "browse files with sudo powers"
date: 2008-12-14
forum: General Help
---

### Post by vampist on 2008-12-14
I know there is a command. I just don't know it.

You know where you drag my computer link to the panel then change the command to <the sudo command>. It asks for the sudo password then you have sudo powers while browsing.

I had the command but I recently had to reinstall ubuntu.

Oh yes that may help.. I have ubuntu 8.04 LTS.

---

### Post by SuperSonic4 on 2008-12-14
```
gksu nautilus
```

---

### Post by northern lights on 2008-12-14
```
gksu nautilus
```opens a filemanager with root rights.

Let it be known that it is not advisable to use it for daily work.

---

### Post by chriskin on 2008-12-14
you can also enable the script for nautilus from ubuntu tweak that lets you browse as root

---

### Post by jakupl on 2008-12-14
# taken from [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

This is a trick from the [this thread]("http://www.ubuntuforums.org/showthread.php?t=24008") on the [Ubuntu Forums]("https://help.ubuntu.com/community/UbuntuForums").

Create a [launcher]("https://help.ubuntu.com/community/HowToAddaLauncher") with the following command:

```
gksudo "gnome-open %u"
```

When you drag and drop any file on this launcher (it's useful to put it on the desktop or on a panel), it will be opened as root with its own associated application. This is helpful especially when you're editing config files owned by root, since they will be opened as read only by default with gedit, etc.

---

### Post by vampist on 2008-12-14
Thanks guys! You Rock :guitar:

---

