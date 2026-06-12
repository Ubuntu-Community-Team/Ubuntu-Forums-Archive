---
title: "Wolfenstein: Enemy Territory problem. Can't join servers"
date: 2007-12-15
forum: Gaming &amp; Leisure
---

### Post by ares623 on 2007-12-15
when I try to join a server, the loading screen tells me it's downloading something.. but it never starts downloading. it just stays at 0%.

---

### Post by Dogfighter on 2007-12-15
2.55? 2.56? 2.60? 2.60b?
all mods?
all download options enabled?
other downloads closed down before?

---

### Post by ares623 on 2007-12-15
version 2.60
actually i'm just interested in the mod True Combat: Elite,
but neither of them works. 
i don't know any download options..

EDIT: just tried again today twice.. it crashes when it starts loading.

---

### Post by Dogfighter on 2007-12-16
did u install as root?
if yes, uninstall and reinstall without root.
often solves most problems.

---

### Post by weblordpepe on 2007-12-16
You'll also run into serious troubles with Punkbuster using the linux one.

To cut a long story short: The built-in punkbuster client which comes with the the linux WolfET doesn't update itself automatically.
What you'll *need* to do is download the punkbuster tool from the punkbuster website, and tell it where your WolfET installation is.

You can then click its upgrade button, and it will update your WolfET for you. You'll have to do this, or else you'll be bumped off every server which uses punkbuster.

---

### Post by Dogfighter on 2007-12-16
u dont need to download anything.
simply use the pbweb.x86 for updating, when done copy it into /home/.etwolf/pb and update there again.
works fine ;)

---

### Post by weblordpepe on 2007-12-17
???? yeah? Ooo

---

### Post by ares623 on 2007-12-17
> **Dogfighter said:**
> u dont need to download anything.
simply use the pbweb.x86 for updating, when done copy it into /home/.etwolf/pb and update there again.
works fine ;)
i'll first try this.. how do I run pbweb.x86? i tried double-clicking but doesn't work.

---

### Post by weblordpepe on 2007-12-18
> **ares623 said:**
> i'll first try this.. how do I run pbweb.x86? i tried double-clicking but doesn't work.
It'll be a terminal program. You'll go into the terminal, **cd** your way into the directory, and then type **./pbweb.x86**

Eww my cat drooled on my laptop.

---

### Post by ares623 on 2007-12-18
> **weblordpepe said:**
> It'll be a terminal program. You'll go into the terminal, **cd** your way into the directory, and then type **./pbweb.x86**

Eww my cat drooled on my laptop.
lol. eww.. anyway, i tried that, but it says "command not found"
i'll try the other one next..

---

### Post by ares623 on 2007-12-18
> **weblordpepe said:**
> You'll also run into serious troubles with Punkbuster using the linux one.

To cut a long story short: The built-in punkbuster client which comes with the the linux WolfET doesn't update itself automatically.
What you'll *need* to do is download the punkbuster tool from the punkbuster website, and tell it where your WolfET installation is.

You can then click its upgrade button, and it will update your WolfET for you. You'll have to do this, or else you'll be bumped off every server which uses punkbuster.
but i'm not getting any Punkbuster error messages.. do you really think that's the problem?

---

### Post by weblordpepe on 2007-12-19
You'll probably run into some troubles with Punkbuster. I always did.

---

### Post by weblordpepe on 2007-12-19
> **ares623 said:**
> lol. eww.. anyway, i tried that, but it says "command not found"
i'll try the other one next..That will probably be because the file doesn't exist. Putting **./foobar** is how you run programs on the command line if they are flagged as executable.

All kinds of files can be flagged as executable. If you run them by going **./foobar** then it'll run foobar with the correct interpreter, that being perl, sh, binary or whatever.

---

### Post by ares623 on 2007-12-19
here is the terminal when I try running pbweb.x86.. it does exist. but if I can't run is as not su, but when I sudo it, it says command not found.
```

administrator@Linux-Home-Desktop:~$ cd /usr/local/games/enemy-territory/
administrator@Linux-Home-Desktop:/usr/local/games/enemy-territory$ cd ./pb/
administrator@Linux-Home-Desktop:/usr/local/games/enemy-territory/pb$ ls
htm      pbags.so  pbcl.so   PB_EULA.txt  pbsv.so
pbag.so  pbcl.db   pbcls.so  pbsv.db      pbweb.x86
administrator@Linux-Home-Desktop:/usr/local/games/enemy-territory/pb$ ./pbweb.x86
bash: ./pbweb.x86: Permission denied
administrator@Linux-Home-Desktop:/usr/local/games/enemy-territory/pb$ sudo ./pbweb.x86
[sudo] password for administrator:
sudo: ./pbweb.x86: command not found
administrator@Linux-Home-Desktop:/usr/local/games/enemy-territory/pb$ 


```

---

### Post by DoktorSeven on 2007-12-19
Make it executable:

```
sudo chmod 755 pbweb.x86
```

then run

```
sudo ./pbweb.x86
```

---

### Post by ares623 on 2007-12-20
updated punkbuster now.. still not able to connect to anything. any suggestions?

---

### Post by ares623 on 2007-12-23
screw this.. was able to play a few maps. then I just got pissed. lol
how do I completely remove this game? 
will deleting the install directory do the trick?

---

### Post by ares623 on 2007-12-24
bump

---

