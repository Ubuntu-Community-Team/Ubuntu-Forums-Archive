---
title: "TCE install problems"
date: 2007-01-15
forum: Gaming &amp; Leisure
---

### Post by umattu on 2007-01-15
I downloaded the loki installer for TCE and I am unable to install it.

I have "chmod +x true.combat.elite_0.49b-english.run" 

now when I run it The archive intergrity checks out but I get this when it starts unpacking

matt@matt-edgy:~/Downloads$ sudo ./true.combat.elite_0.49b-english.run
Verifying archive integrity... All good.
Uncompressing True Combat: Elite 0.49b-english...........................
./search.sh: 36: Syntax error: Bad substitution

I have even tried running it in a root terminal and got the same thing

Please help

---

### Post by umattu on 2007-01-16
anyone?

---

### Post by haxer on 2007-01-16
[http://ubuntuforums.org/showthread.php?t=306884&highlight=tce](http://ubuntuforums.org/showthread.php?t=306884&highlight=tce)

:D

---

### Post by haxer on 2007-01-16
Place it on the Desktop then drag and drop into terminal then use sudo sh in the begining:)

---

### Post by umattu on 2007-01-16
Thanls for posting
I tried all of what you suggested but I still get the same error

matt@matt-edgy:~$ sudo sh /home/matt/Desktop/true.combat.elite_0.49b-english.run 
Password:
Verifying archive integrity... All good.
Uncompressing True Combat: Elite 0.49b-english...........................
./search.sh: 36: Syntax error: Bad substitution
matt@matt-edgy:~$ 

I have even D.L.ed the file a second time and I still get this

any ideas

---

### Post by haxer on 2007-01-17
you need to install enemy terrotory first it says so to in the link i gave you :) try it out and download the new version of 0.49b [http://liflg.org/?catid=6](http://liflg.org/?catid=6) 

and heres an how to install enemy terrotory [http://www.katanoon.nl/ubu-e/install.php](http://www.katanoon.nl/ubu-e/install.php) take it to the 5th  step then install 0.49b instead

---

### Post by imspecial on 2007-01-21
it is ```
sudo sh ./home/matt/Desktop/true.combat.elite_0.49b-english.run
``` not ```
sudo sh /home/matt/Desktop/true.combat.elite_0.49b-english.run
```  You forgot the period before the path of the run file.

---

