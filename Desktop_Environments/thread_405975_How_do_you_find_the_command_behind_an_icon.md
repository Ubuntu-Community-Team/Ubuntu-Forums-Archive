---
title: "How do you find the command behind an icon?"
date: 2007-04-10
forum: Desktop Environments
---

### Post by holz on 2007-04-10
Hi all

just installed Xubuntu and i have few questions. How do you find out the command behind an icon? For example, i would like customize the panel to have a specific launcher, Office writer for example, or the calendar. How do I know which command line triggers each? In windows you right here and select properties, but i no longer run windows...
](*,) 

TIA

---

### Post by tictacman on 2007-04-10
Usually the commands are the same as the name. For example the calendar in xubuntu (Orage), is just orage.  I didn't know what the command was for the menu entry for openoffice writer. So I clicked on it - then I had a look at the processes I was running by using this command:

```
ps U myname
```

alot of stuff came up and I couldn't be bothered to sift through so I filtered it with what I thought would be in the command

```
ps U myname | grep office
```

line came back to tell me soffice was running, and that was the command I was looking for.

Its a bit drawn out way of finding out, but I guess it might help you.

---

### Post by miggols99 on 2007-04-10
Well in KDE, you can right click on an icon and choose "put item into run dialogue". One of the many great features of KDE :)

For you, you could look in the menu editor.

---

### Post by fwojciec on 2007-04-10
Run Accessories/Appfinder (from XFCE menu) - find the application -  right click on it and choose "More Information" - check what is says in "Command" 

I hope that helps ;)

---

### Post by mojoman on 2007-04-18
> **holz said:**
> Hi all

just installed Xubuntu and i have few questions. How do you find out the command behind an icon? For example, i would like customize the panel to have a specific launcher, Office writer for example, or the calendar. How do I know which command line triggers each? In windows you right here and select properties, but i no longer run windows...
](*,) 

TIA

A bit late perhaps but in Linux a program -or it's launcher at any rate- resides in a specific folder. If you know the name of the launcher -and it's almost always the name of the application- the wonderful little command "whereis" is what will save your day. For example, I've installed filezilla and want a launcher in my panel bar. In a terminal I write: 

```
mojoman@jukejoint:~$ whereis filezilla
filezilla: /usr/bin/filezilla /usr/X11R6/bin/filezilla /usr/bin/X11/filezilla /usr/share/filezilla /usr/share/man/man1/filezilla.1.gz
```

Filezilla, just like a ton of applications, is in /usr/bin/ so the correct path is  "/usr/bin/filezilla".

Now, of course I don't want the few measly icons available, I want the real McCoy so for icons I go to /usr/share/pixmaps and, lo and behold, there is filezilla.xpm so I add "/usr/share/pixmaps/filezilla.xpm" as the search path for the icon. Just add name and description, click close and I got a beuitiful filezilla icon right in my panel which will launch my favorite gui ftp client. A lot of icons are available on usr/share/pixmaps but there are icons in other folders as well. Fooling around with the command locate, combined with grep, is a good way to get a feel for where the bulk of them are. Remember that icons usually have the extension .xpm, .png or .svg (I'm not 100% on the last one) and combining locate with grep is a good way to find them.

Hope this helps.
/mojoman

---

