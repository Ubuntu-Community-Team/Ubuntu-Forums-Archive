---
title: "Repos"
date: 2008-06-29
forum: Debian
---

### Post by Fred_E _krugar on 2008-06-29
I know there is already a thread on this but it got a little off topic pretty quick.


So could you guys list what repos are the most used. Like the backports and media and the extra stuff, yall know what I mean.

Maybe we could get it stickied so everybody knows where to find all the extra repos.



BTW I bet kerry_s knows all of them off the top of his head lol

---

### Post by Fred_E _krugar on 2008-06-29
Would these be all that I realy need to get everything I pretty much need???




deb [http://www.debian-multimedia.org](http://www.debian-multimedia.org) lenny main
deb [http://security.debian.org/](http://security.debian.org/) testing/updates main contrib non-free
deb [http://ftp.debian.org/debian/](http://ftp.debian.org/debian/) testing main contrib non-free

---

### Post by cdiem on 2008-06-29
Hi, I also use Lenny. Here are some more repositories, that you may want to have for a desktop computer with Debian Lenny:

```
#Security updates
deb http://security.debian.org/ lenny/updates main contrib non-free
#Skype
deb http://download.skype.com/linux/repos/debian/ stable non-free
#Opera
deb http://deb.opera.com/opera/ lenny non-free
```

---

### Post by kerry_s on 2008-06-29
> **Fred_E _krugar said:**
> Would these be all that I realy need to get everything I pretty much need???




deb [http://www.debian-multimedia.org](http://www.debian-multimedia.org) lenny main
deb [http://ftp.debian.org/debian/](http://ftp.debian.org/debian/) lenny non-free
deb [http://ftp.debian.org/debian/](http://ftp.debian.org/debian/) testing main contrib non-free

you don't need->
deb [http://ftp.debian.org/debian/](http://ftp.debian.org/debian/) lenny non-free

it's the same as testing.
where's the security repo?
```
deb http://security.debian.org/ testing/updates main contrib non-free
```

---

### Post by kerry_s on 2008-06-29
> BTW I bet kerry_s knows all of them off the top of his head lol

:lolflag:
i'm taking a linux break right now, i'm using win2k pro sp4. i put it on my ibm t20, then mom stole it for her, it's now a kitchen cookbook, music player, etc...
anyways i needed to get familiar with it again so i wiped my vaio pcg-430 and put the exact same setup so i can test things before i do it on the ibm, so as not to screw things up. i forgot a lot of things so it takes me a while to remember how to set things just right, i'm running bare bones so the only protection is a firewall, all other protection is through locking things down internally.

some security samples:

---

### Post by Fred_E _krugar on 2008-06-29
OK kerry does that look better??

---

### Post by Fred_E _krugar on 2008-06-29
> **kerry_s said:**
> :lolflag:
i'm taking a linux break right now, i'm using win2k pro sp4. i put it on my ibm t20, then mom stole it for her, it's now a kitchen cookbook, music player, etc...
anyways i needed to get familiar with it again so i wiped my vaio pcg-430 and put the exact same setup so i can test things before i do it on the ibm, so as not to screw things up. i forgot a lot of things so it takes me a while to remember how to set things just right, i'm running bare bones so the only protection is a firewall, all other protection is through locking things down internally.

some security samples:



Tisk Tisk you traitor. ;)

---

### Post by kerry_s on 2008-06-29
change:
deb [http://www.debian-multimedia.org](http://www.debian-multimedia.org) lenny main
to
deb [http://www.debian-multimedia.org](http://www.debian-multimedia.org) testing main

that should future proof you for when lenny moves to stable. that's normally what i use, so you should be good.
sometimes i'll test opera to see how it's coming along:
```

deb http://deb.opera.com/opera/ lenny non-free

as root:
wget -O - http://deb.opera.com/archive.key | apt-key add -

```

> Tisk Tisk you traitor. 

sometimes it feels so good to be so bad. :twisted:
the irony is this computer just loves "MS", it runs perfectly and using less resource than i can get with a custom linux install. :(
normally in linux i'm around 35->45 process's running, in win2k i have 17, but if i didn't have my drive set to read only and had to run "AV" and "anti-whatever", i think they would be about the same.

---

### Post by basenvironment on 2008-06-30
I only use main myself. I might occasionally get something from the multimedia repo though.

---

