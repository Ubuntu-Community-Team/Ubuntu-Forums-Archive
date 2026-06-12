---
title: "firefox go crazy on 9.04"
date: 2009-05-30
forum: General Help
---

### Post by mabulhija on 2009-05-30
i installed ubuntu 9.04 on my laptop lenovo SL400 and am trying to solve the problems about brightness and volume,...etc, but i dont know why firefox is not working correctly, i have updated the system, its update and the only thing i add to firefox is dTa manager, and flash player, and yet when ever i want to download any kinda file either using the dTa or the normal manager the firefox crush and when i re-open it, it starts like its the first time i open it, no bookmarks, no saved data from last use, nothing... i cant figure it out, what is the problem, can anyone help please.

thanks

---

### Post by asmoore82 on 2009-05-30
the crashed firefox is probably stuck in the background so the newly opened firefox spawns a clean profile.

kill _all_ firefox process - a restart may be the simplest way to accomplish this -
then to run the Firefox Profile Manager, open a terminal and:
```
firefox -P
```

---

### Post by lovinglinux on 2009-05-30
I would recommend disabling DownThemAll extension. I have been reading some reports about issues with this extension. So I guess it is the culprit.

---

### Post by mabulhija on 2009-05-30
the good thing in ubuntu/linux that you can format your pc in couple minutes as long as you dont have much applications already installed :D

the problem solved for now, i didnt install the dTa manager this time and its working normally.

but am facing the other problems, about brightness i found this web site and downloaded the files but i just dont know how to use them?!

[tetromino's](http://github.com/tetromino/lenovo-sl-laptop/tree/master) <--- check the page

the page says that is a fix, but how i should use it, i tried to compile the c file like this
cc -c lenovo-sl-laptop.c the only thing i got is a lot of errors!

any help.

thanks

---

