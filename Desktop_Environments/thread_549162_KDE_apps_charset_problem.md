---
title: "KDE apps charset problem"
date: 2007-09-12
forum: Desktop Environments
---

### Post by cromozon on 2007-09-12
Hi, I am fairly new to ubuntu, but not to linux in general, I used gentoo for quite some time, so one could expect to be able to solve stupid problems like this...

non the less, I have installed kde from synaptic, because I like it better than gnome.

But when I open a file edited in dos in a KDE apps, ( kate / kwrite ) it borgs the special characters in it (I'm from Denmark), the strange thing is I can write the letters in the app.

the following picture show the problem better i think.
[IMG]http://swn.nu/cg/images/font_problem.png[/IMG]

---

### Post by miggols99 on 2007-09-12
What font are you using? The Gnome app may be using a font supporting the characters. Try different fonts in the KDE control centre to see if it works.

---

### Post by cromozon on 2007-09-13
Hi migols99.

I am using monospace font, in both gedtir and kwrite, so I don't think it is the fon't which is the problem, if that is the case I't doesn't make sense that I can write the special characters, but not load.

Further more, and what I didn't mention before, is that if I SAVE the file with kwrite, it will also borg the charachters when I open it in another program, 

I suspect it is something happening when it loads the file.

hmm before posting this i played arround with some opening option,
in gedit, 
[LIST]
[*]it default to automatic (works)
[*]refuses to open in utf-8 format (system default)
[*]opens correct in iso-8859-15
[/LIST]

in kwrite, it simply defaults to utf-8, if I forces it to use-8859-15 it works perfectly.

I guess that answers my question kinda :)

in kwrite, settings->setup editor->load/save, I can see kwrite defaults to kde-defaults.
(the menu names might not be entirely correct, since my kwrite has danish menus :) ) 

So I am thinking this must be possible to do automatic ( since gedit can, so must kde be able to :) )

simple changing the system default is a bad solution, since I use many different computers, also where I am not the administrator, so I can never be sure what format I will recieve a file in. 

if there is anyone who might know how to get kde to handle this automatically, it would make me ( and perhaps others :) ) very happy.

---

