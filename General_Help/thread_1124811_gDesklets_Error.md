---
title: "gDesklets Error"
date: 2009-04-13
forum: General Help
---

### Post by uNiQue1337 on 2009-04-13
Hello, i just installed gDesklets and when i go to accessories and click gDesklets it gives me the following error

[B]Could not launch 'gDesklets'
Failed to execute child process "gdesklets" (No such file or directory)[/B]

Any idea? Thanks.

---

### Post by lovinglinux on 2009-04-13
I'm not sure about the error, but gDesklets is kind of old. You should consider trying screenlets, which is very nice.

---

### Post by uNiQue1337 on 2009-04-13
> **lovinglinux said:**
> I'm not sure about the error, but gDesklets is kind of old. You should consider trying screenlets, which is very nice.
Thank you very mutch.

---

### Post by lovinglinux on 2009-04-13
I went searching for more information on both and I found this:

> **bryonak said:**
> gDesklets is a very old project and all of its developers have moved on to something different. I don't know the exact reasons, but it has been considered dead for quite some time now.

Screenlets was intended to replace gDesklets and has come a long way (stable and efficient in Intrepid).
But in 2008 infighting among the developers broke out about some commit, behaviour and copyright issues.
The project got forked into Universal Applets, which lets other GNOME applications like the panel include widgets (mainly Screenlets, but others are planned).
Additionally the main developer for Screenlets left, so it is more or less stopped at the moment. There are still some bug fixes being made and it works very well for many users, but it's expected to die out in the future.

Universal Applets is still quite young and unstable, but will probably become the standard "widget" framework after Screenlets.



*EDIT: looks like some german developers have picked up on gDesklets again. [gdesklets.de]("http://www.gdesklets.de")*

Please notice that to run screenlets you need compiz.

---

### Post by stelekpl on 2009-04-25
Today I upgraded to 9.04 and have the same problem. It worked fine in 8.10. Any ideas?

---

### Post by stelekpl on 2009-04-25
OK, so this problem is easily solvable by editing the first line of:

/usr/bin/gdesklets

to point to an existing python version. But then - it still does not work :(

---

### Post by itsjustarumour on 2009-04-25
> **stelekpl said:**
> OK, so this problem is easily solvable by editing the first line of:

/usr/bin/gdesklets

to point to an existing python version. But then - it still does not work :(

Yeah, I think this is an issue the gDesklets devs are aware of, I seem to remember some talk about this on the gDesklets mailing list within the last few weeks or so.



EDIT:

Found it!  From the gDesklets mailing list:

> Date: Sun, 29 Mar 2009 19:58:01 +0200

"This current ubuntu bugs seem to depend on Python 2.6/3.0..."

So there you have it.

---

### Post by Urbanmoth on 2009-04-25
Easy to solve:

```
sudo apt-get install python-all
```

---

### Post by liame on 2009-05-04
> **urbanmoth said:**
> easy to solve:

```
sudo apt-get install python-all
```

thank u!!!

---

### Post by lotvx on 2009-07-27
solo este es necesario

sudo apt-get install python2.5

---

