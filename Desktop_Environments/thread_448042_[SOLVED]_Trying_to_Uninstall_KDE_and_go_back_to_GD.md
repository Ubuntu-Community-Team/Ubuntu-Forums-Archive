---
title: "[SOLVED] Trying to Uninstall KDE and go back to GDE."
date: 2007-05-18
forum: Desktop Environments
---

### Post by RonB123123 on 2007-05-18
Trying to Uninstall KDE and go back to GDE. 

I searched through the forums and I ran this command.
```

sudo aptitude remove kubuntu-desktop

```

but then it gave me this:
[quote=Terminal]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
[/quote]

Is there any way to do this? Thanks. :)

~Ron

---

### Post by louieb on 2007-05-18
See the Pure Gnome page here [Psychocats Ubuntu Linux Resources]("http://www.psychocats.net/ubuntu/index.php")

---

### Post by merlinus on 2007-05-18
This may help --

[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

If you did not use aptitude to install kde, then you cannot use aptitude to remove it.

-merlin

---

### Post by raja on 2007-05-18
If I understand right, you installed Ubuntu and then installed KDE on top of it. Now you want to remove KDE - right ?

Your command will work if you installed KDE with aptitude. If you did it with apt-get, you have to list all the files to remove - see [this page]("http://www.psychocats.net/ubuntu/puregnome") for how to do it.

---

### Post by RonB123123 on 2007-05-18
Hey thank you very much, that very huge command worked! :D

Oh and I also found a bug in the terminal. If anyone is interested.

When I ran that command, everything worked fine. But then I ran a few more commands, and then tried to go back and find a command I typed in before that really big one, by pressing the Up Arrow. When I passed the big huge command, the terminal did something weird. It kept about half of the big command and showed the current command in the history that I was navigating through. When I pressed enter for that command in the history, it surprisingly worked fine.

---

