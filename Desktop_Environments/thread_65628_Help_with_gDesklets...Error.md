---
title: "Help with gDesklets...Error"
date: 2005-09-14
forum: Desktop Environments
---

### Post by dbrine on 2005-09-14
I installed Gdesklets without anyproblesm. Everything was working fine, no error until I rebooted. I now get an erro "No Such Property: desktop-borders "The element display does not have the desktop-borders property". And I have block boxes where my toolbar (replace with Gnome 2 bar) and my hdd desklets???? HELP. I removed them from them Synaptic, reloaded the gDesklets pakages, stopped and restart Daemon (no Errors...besides the above error).

---

### Post by adm on 2006-12-03
I have the same problem, but with hottieofthehour.
Help please :)

---

### Post by mark0071m on 2007-02-26
I seems that many of the desklets need editing of the .display file to work... I.E. hottieofthehour needed the word align removed.

---

### Post by orb9220 on 2007-02-27
Yes since the gdesklet developers remind me of programmers on valium. They totally disregard and have No Interest in keeping their project updated.

And since yahoo change the layout most if not all the weather widgets are busted.
I only use the clock now and there is a linux version of rainlendar for desktop calender.todo,appts. now.

Still have not found a clock,weather desktop widget that is Not KDE instead of gdesklets.

And Conky is great for system stats,connections,etc....

---

### Post by _graham_ on 2007-03-16
Just to clarify Mark's point:

Go to /usr/share/gdesklets/Displays/hottieofthehour
Edit the hottieofthehour.display and hottie.display files with a Text Editor
Delete the phrase 'align="center"' in each file and save them

Next time you run it, it should work!

---

