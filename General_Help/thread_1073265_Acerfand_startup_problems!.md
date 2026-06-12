---
title: "Acerfand startup problems!"
date: 2009-02-18
forum: General Help
---

### Post by Joezorry on 2009-02-18
So I have installed Ubuntu on the netbook, manage to get acerfand working, and everrything.
But when I restart my computer i have to write the script sudo acerfand #.
Is there anyway I can make this start up as soon as the computer is on?

---

### Post by Joezorry on 2009-02-18
Everytime I start up the computer, acerfand won't start, how do I make it start everytime I start the computer...

---

### Post by growlf on 2009-05-20
Try placing a line like this in your rc.local: 

>  start-stop-daemon –-start –-name acerfand –-startas /usr/local/bin/acerfand –-background This works for me, and I found it at:  [http://mike987.wordpress.com/2009/04/28/acerfand-in-ubuntu-904-jaunty/](http://mike987.wordpress.com/2009/04/28/acerfand-in-ubuntu-904-jaunty/)

---

