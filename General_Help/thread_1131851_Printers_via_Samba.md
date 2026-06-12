---
title: "Printers via Samba"
date: 2009-04-21
forum: General Help
---

### Post by Aus_Tux on 2009-04-21
Hello fellow Linux users, please excuse the stupidity of this thread.

Q1. How do you get a Windows (XP Home in this case) computer to see an Ubuntu (8.10 Gnome/KDE Blend) computer?

Q2. How do you set up a print server?

Q3. Is there a program, script or other autonomous object that can automatically do the above?

My setup:-
-Dual Boot Windows XP Pro/Ubuntu 8.10 desktop connected to a wireless router and a HP MP500 printer via USB (Samba and Cups are both installed, although reset to default after failed attempts to solve the problem).
-Windows XP Home laptop connected to the same wireless router.
-Both computers are part of a windows network (unfortunately the desktop only got in with its windows alter-ego)

Please, if its not too much trouble, provide the simplest, preferably GUI-centric, solution to this problem (I do not mind downloading resources).

P.S. I know this has been done before tons of times, but none of the guides I found (courtesy of Google) were explicit enough or were riddled with ambiguities. If you can find me a page that explains step by step exactly what to do, in layman terms, that would be extremely helpful.

---

### Post by hyperdude111 on 2009-04-21
I assume you have installed samba.

Right click on the directory you want to share from ubuntu to windows go to sharing and allow all shares. 

Go to the windows machine and type in explorer " //yourname-desktop/ " The folder should come up.

---

