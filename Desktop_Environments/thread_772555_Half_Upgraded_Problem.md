---
title: "Half Upgraded Problem"
date: 2008-04-28
forum: Desktop Environments
---

### Post by Spoken on 2008-04-28
alright, due to my busy schedule with school and work etc, ive only been able to upgrade from 7.10 to 8.04 piece by piece. 

Last night i left my laptop on so it can upgrade while i caught some sleep. this morning it finished fetching the new packages and was installing them. i had to stop the process because i had to go to school. so im at school now in the library, i turned my laptop on and when i logged in, a lot of my theme stuff / screenlets is gone, and i got this error message that says "failed to initialize HAL!", it says its a internal error.

i dont know what to do. my guess is that it messed up because the upgrade to 8.04 removed certain packages and hadnt had the chance to install the new ones.

is there anything i can do? my upcoming classes that i have in a few hours would be a lot easier if i could continue taking notes on my laptop lol.

====================================
MY SITUATION
====================================
Compiz fusion and emerald theme manager are still working

MY WIFI CONNECTION IS BROKEN!!! I CANT USE SUDO APT GET COMMANDS!

BUT! my panel color and location is back to default, my folder theme is different, and my screenlets are broken.

---

### Post by Xiong Chiamiov on 2008-04-29
What happens when you run
```

sudo apt-get update; sudo apt-get dist-upgrade; sudo apt-get upgrade

```
or
```

sudo apt-get upgrade -f

```
?

---

### Post by Spoken on 2008-04-29
alright, well, i would love to do that, but i have a new problem.  the hardy upgrade has disabled my wifi card.  so now i have no internet.

---

### Post by toupeiro on 2008-05-01
[http://www.dellcommunity.com/supportforums/board/message?board.id=sw_linux&thread.id=9476](http://www.dellcommunity.com/supportforums/board/message?board.id=sw_linux&thread.id=9476)

It appears there is a way to envoke a dell system utility to repartition your entire disk if you are unable to recover from CD

---

### Post by agim on 2008-05-01
Next time I would try to fresh install. I hear of so many more problems with upgrade. I usually devote a small partition (about 6-10GB) to the new install, and give it a month, to make sure it works.
As far as the rest goes, I would try to get your wireless card working first. How did you do it initially? Is it something that worked out of the box? Or did you use ndiswrapper?

---

### Post by toupeiro on 2008-05-01
You can also download [Dell ISO's of ubuntu]("http://linux.dell.com/wiki/index.php/Ubuntu_7.04#Download_Dell_Ubuntu_Image"), I just discovered.  They may have some drivers slipstreamed into the install if you are having problems with the vanilla ISO's.

---

