---
title: "Yast2 for Ubuntu?"
date: 2005-04-11
forum: Desktop Environments
---

### Post by Pixman on 2005-04-11
Hello community,

just a little question: Will this be implemented? Or actually supported?
(K)Ubuntu really needs this! And it isn't too hard to implement too :)
[http://yast4debian.alioth.debian.org/](http://yast4debian.alioth.debian.org/)

---

### Post by poofyhairguy on 2005-04-11
[QUOTE=Pixman]Hello community,

just a little question: Will this be implemented? Or actually supported?
(K)Ubuntu really needs this! And it isn't too hard to implement too :)
[http://yast4debian.alioth.debian.org/](http://yast4debian.alioth.debian.org/)[/QUOTE]


Looks cool. It would be a good idea to get jdong's attention on this. He is the backport maintainer, a kubuntu user, and a very nice guy.

---

### Post by arctic on 2005-04-11
the yast ubuntu/kubuntu stuff has already been discussed in detail. use the search tool next time ;)

---

### Post by tanari on 2005-04-11
GNOME system control tools work fine. I think only a few peoples need more :).

---

### Post by Pixman on 2005-04-11
Oh well, them YaST2 modules still simplify the process of working a LOT.. when I think about configuring uhm. .. like ... ANYTHING on a PC, including Apache, Samba & FTP Services... well, guess a lot of people would like that :)

---

### Post by !nkubus on 2005-04-11
I also support that :)

would be very nice :) and this will make kubuntu ahead of all the debian kde distribution around, even if it already is ahead ;)


just my 2 cents :)

---

### Post by abovett on 2005-04-11
Personally I've always found YaST to be a bit of a pain. It's OK if/while you use it (if a little OTT) but it expects you to do everything it's way. Try manually editing a config file, or using another tool to do it, and chances are either YaST will undo your changes, or get confused by them. I like the approach in Ubuntu - simple tools to do simple tasks without adding extra layers of complexity.

Maybe it's just me, but I've never been too keen on using a config tool when I'm not sure what it's actually doing. I think that too much integration and automation is a bad thing (just look at Windows!) because it hides too much of what's going on, and sooner or later that catches you out.

I know not everyone wants to get "under the hood" and that's half the point of Ubuntu but I think ease of use and ease of configuration can be achieved without putting a thick layer of abstraction between the user and what's going on if it's carefully designed.

Just my personal view!

Andy B

---

### Post by Pixman on 2005-04-11
maybe we should think different, or even bigger / smaller.

Let's not think of a port but of an adaption with fewer modules a more detailed output of the actions the config-tool does.

YaST could be a great base for that. And when I look at the current developments of yast4debian, the work might be done already in near future and ubuntu users can chose if they want to use it or not ;)

---

### Post by jdong on 2005-04-11
[QUOTE=poofyhairguy]Looks cool. It would be a good idea to get jdong's attention on this. He is the backport maintainer, a kubuntu user, and a very nice guy.[/QUOTE]

Yep I am (just kidding)

I've already seen it; I'll look into packaging it.

---

### Post by redlabour on 2005-07-20
[QUOTE=jdong]Yep I am (just kidding)

I've already seen it; I'll look into packaging it.[/QUOTE]
 jdong  - i have made a request in Backports Forum too.

---

### Post by abandoned_hussam on 2005-07-20
[QUOTE=jdong]Yep I am (just kidding)

I've already seen it; I'll look into packaging it.[/QUOTE]
 Yes, me would like this too, pretty please. :)

---

### Post by Terracotta on 2005-07-20
[QUOTE=tanari]GNOME system control tools work fine. I think only a few peoples need more :).[/QUOTE]

No offence, but wasn't this the KDE section of ubuntuforums? :-), So I think that a lot of people don't even have the GNOME system control tools here :-).

Well, since yast4debian is going to support apt  I think it would be a great replacement for Kynaptics :-), or Kpackage as well. Looking forward to this.

---

### Post by jdong on 2005-07-20
Right now, I'm using SuSE and dissecting YAST to get a better idea of how it works.

yast4debian is an on-going project; only a few yast modules are ported over, making the tool pretty useless right now. In fact, it's built in a non-Debian way, making it more difficult to package.

---

### Post by coolclassic on 2005-07-20
[QUOTE=Terracotta]No offence, but wasn't this the KDE section of ubuntuforums? :-), So I think that a lot of people don't even have the GNOME system control tools here :-).

Well, since yast4debian is going to support apt  I think it would be a great replacement for Kynaptics :-), or Kpackage as well. Looking forward to this.[/QUOTE]
 I have used yast with suse for 4years and the one thing I hated was the dependancy hell when installing software. If yast used the same interface as apt then it could be a great package.

---

