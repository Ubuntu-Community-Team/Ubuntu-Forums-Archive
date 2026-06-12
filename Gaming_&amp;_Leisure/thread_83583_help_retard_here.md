---
title: "help retard here"
date: 2005-10-29
forum: Gaming &amp; Leisure
---

### Post by mike547 on 2005-10-29
i just download americas army for linux 2.5 and get get it installed it drivin me retarded it says a shell script  how adn what do i use and i am very new to linux so detailed help a must

---

### Post by crane on 2005-10-29
Not quit sure what the question is here. You downloaded the game and can't install it?
Try opening a terminal window.
Then CD to where the file is. Say it's on your desktop
[color=blue]cd desktop[/color]
hit enter the type 
[color=blue] sudo sh (filename) 
without ()

---

### Post by stuporglue on 2005-10-29
Maybe you could explain what's wrong a little better. I got that you want to install America's Army 2.5, and that you're new to Linux. 

> it says a shell script how adn what do i use

What do you want to know about shell scripts? Do you have one you want to run? Do you need to write one? What says "a shell script"? -- the directions? What exactly does it say?

---

### Post by mike547 on 2005-10-29
ok been a long day sorry     i right click on the file and click propertys  say file type     shell script   it says mime type  application/x-shellscript  i wanna install it

---

### Post by stuporglue on 2005-10-29
Ok. One of the security features of Linux is that when you download something, it's not automatically executable. You can make it executable by right clicking it and selecting "Properties". In the "Permissions" tab, make it executable for Owner, Group, and Others. 

You'll probably need administrator power to install it, so we'll open up a terminal (in the System Tools menu, in Applications). 

You need to navigate to the file to run it in the terminal. Is it on your Desktop? 

Type: 
$ cd ~/Desktop
to get there (note that the $ just means it's a command to be typed. Don't type the $). 
To run it, type
$ sudo whatever_the_files_name_is

Hope that helps!

---

### Post by mike547 on 2005-10-29
like i said retard here looked at that fifty times or so and never sunk in  the securt exacute thing thank  you   very much :KS :KS :KS :KS  that was my biggest mistery so far with linux since sunday of this week!!! o and while i was right clickin i just changed the file that opend it to terminal and it work great  :KS :KS :KS  :KS not very often you get to help a retard tank you

---

