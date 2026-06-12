---
title: "how to: open vmd file using nautilus - ubuntu 14.04"
date: 2014-09-21
forum: Education &amp; Science
---

### Post by Claus7 on 2014-09-21
Hello,

I wanted to open a vmd file by right clicking and opening it. Back in the days of maverick I used this [solution]("http://ubuntuforums.org/showthread.php?t=1690838").

In order to do the same thing in ubuntu trusty 14.04, I had to create a script with the following line:
> xterm -e /usr/local/bin/vmd **$1**

(as you can see adding the $1 to the previously issued command).

I added the script under: .local/share/nautilus/scripts
and with a right click on the file and clicking this script, vmd opens the file I have selected.

Regards!

---

