---
title: "Can´t start graphical session"
date: 2006-03-15
forum: Desktop Environments
---

### Post by arthur on 2006-03-15
Today, 20 minutes after installing a large number of plugins and apps using **automatix**, my Ubuntu installation refused to open a Gnome session. An error message is displayed, and a non-graphic command-line login is shown.

As far as I know, the automatix script works fine. Does anybody recognize the most likely cause for this? 

Thanks in advance, I am really annoyed :mad:

---

### Post by lamego on 2006-03-15
Posting the error message could help...

---

### Post by stabface on 2006-03-15
i had problem yesterday after using the automatix script, and couldn't login it. what had happened was while using the script it filled my / partition and that made x not boot.

---

### Post by arthur on 2006-03-15
Thanks for the quick help :) 
Googled a bit, and found the solution:
[B]
sudo apt-get clean[/B]
(in text-mode login)

That was all!

---

