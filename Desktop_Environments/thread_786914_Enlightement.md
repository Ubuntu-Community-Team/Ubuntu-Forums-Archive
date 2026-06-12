---
title: "Enlightement"
date: 2008-05-08
forum: Desktop Environments
---

### Post by Zophixan on 2008-05-08
Hey guys, hope this is in the right section - I just tried installing E17 and I think everything went well, however when i log out, and try logging into enlightement, it says "you tried to start from bin this is bad, you should use englightement start. I this maybe because of me previously using an old guide which didn't work, where I edited the enviroment file. Does anyone have a good enviroment file for enlightement?

---

### Post by Rui Pais on 2008-05-08
> **Zophixan said:**
> Hey guys, hope this is in the right section - I just tried installing E17 and I think everything went well, however when i log out, and try logging into enlightement, it says "you tried to start from bin this is bad, you should use englightement start. I this maybe because of me previously using an old guide which didn't work, where I edited the enviroment file. Does anyone have a good enviroment file for enlightement?

Hi Zophixan.

How do you install it?

And do you start it? directly? login manager?
Can you post the output of:
```
ls /usr/share/xsessions/
```
?

---

### Post by Zophixan on 2008-05-08
Hi, i used this guide : [http://ubuntuforums.org/showthread.php?t=97199&highlight=E17+cvs&page=54](http://ubuntuforums.org/showthread.php?t=97199&highlight=E17+cvs&page=54)
I start it via login manager.
I have tried in kde starting it, but obviously that wouldn't work! I have yet to try starting it from command line. Since preferbly would like it to work through login manager.

---

### Post by angry_johnnie on 2008-05-09
That howto is quite old, actually... Why don't you try removing e17 and installing it again, using [this]("http://ubuntuforums.org/showthread.php?t=546746") howto, which is more recent, and works fine.  I used it to install e17 when hardy was still beta and it's worked without any problems.

---

### Post by Rui Pais on 2008-05-09
> **Zophixan said:**
> Hi, i used this guide : [http://ubuntuforums.org/showthread.php?t=97199&highlight=E17+cvs&page=54](http://ubuntuforums.org/showthread.php?t=97199&highlight=E17+cvs&page=54)
I start it via login manager.
I have tried in kde starting it, but obviously that wouldn't work! I have yet to try starting it from command line. Since preferbly would like it to work through login manager.

Ah that explain it the problems. 
Like angry_johnnie said it's old and obsolete. 
You should check the last posts of threads when they are closed, usually they link to updated ones when closing. 

About your problem, assuming that script run it successfully till the end, to correct it do:
```
sudo rm /usr/share/xsessions/e17.desktop
sudo ln -s /opt/e17/share/xsessions/enlightenment.desktop /usr/share/xsessions/enlightenment.desktop
```

That done it's the same as run my deb package on updated thread, without some minor tweaks... 

hth

---

