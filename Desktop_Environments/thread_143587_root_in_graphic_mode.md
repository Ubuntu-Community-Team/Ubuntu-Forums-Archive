---
title: "root in graphic mode"
date: 2006-03-12
forum: Desktop Environments
---

### Post by hikmat on 2006-03-12
I am unable to do anything in graphic mode in Kubuntu if I am root. If I want to edit a file that only root can, I have to use vi. If I try Kwrite of Kate, I get error message that I got refused by the server. Is this an immutable thing in Ubuntu/Kubuntu?

---

### Post by Xian on 2006-03-12
[QUOTE=hikmat]Is this an immutable thing in Ubuntu/Kubuntu?[/QUOTE]

In Ubuntu (Gnome) you can just:
$ sudo gnome-open /path/to/file

And the default text editor will open the file.

I knew kate would not operate under a admin command, but I thought kwrite would open as expected. Have you tried doing a Alt+F2 on the keyboard and entering 'kdesu kwrite'??

---

### Post by aysiu on 2006-03-12
Press Alt-F2 and type ```
kdesu konqueror
```

---

### Post by Jucato on 2006-03-12
if you need to do something in the terminal as root, you use sudo with the command.
if you need to do something in the GUI as root, you launch the app with kdesu. for example you can type this either in the command line or in the Run command dialog box (Alt+F2):
```
kdesu kate
```

@aysiu: While I find it convenient and sometimes necessary to open Konqueror as root, I think it's almost as dangerous as enabling a root GUI login. Unless you setup the roots themes/colors differently from the user theme, it's easy to forget that the Konqueror instance you opened has root privileges. Of course, when you need to graphically copy/move/link files, there's no other way to do it. 
But I think to do specific tasks like text editing, it would perhaps be better if they just kdesu kate/kwrite.

Oh, btw, there's an option in Konqueror to edit config/text files as root. Right-click on the file > Actions > Edit as root. :D

---

