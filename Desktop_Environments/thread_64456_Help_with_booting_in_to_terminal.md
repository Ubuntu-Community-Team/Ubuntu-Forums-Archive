---
title: "Help with booting in to terminal"
date: 2005-09-11
forum: Desktop Environments
---

### Post by kennny2004 on 2005-09-11
hi there I have ubuntu full installed,,,,,, and i want it to run servers,,, but i want to keep the graphical, so is there anyways i can only run terminal, and open from there what ever i need to run,,,, and how do u do it i think ctrl alt f1 is useless because it still runs the gnome and all that stuff that i do not want.
thanks  ](*,)

---

### Post by heimo on 2005-09-11
Is this what you're looking for?
[http://ubuntuforums.org/showthread.php?t=64116](http://ubuntuforums.org/showthread.php?t=64116)

---

### Post by Wide on 2005-09-11
You can also add

apt-get install rcconf

That will allow you to edit your run levels & start up programs.

Have it start with out GDM then start x when you feel like GUI's

I do the same thing on my test server, it's Debian but same stuff :)

---

### Post by jworr on 2005-09-11
You can also boot without X and gnome being started

 to do this hit 'e' when at the grub boot loader
next select the second line and put and space and '3' at the end of the line
hit enter and 'b' and now ubuntu will boot without x server and gnome being started

---

### Post by kennny2004 on 2005-09-11
thanks for all ur help :)

---

