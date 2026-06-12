---
title: "gedit wont work when used with sudo"
date: 2006-06-02
forum: Desktop Environments
---

### Post by mental_drummer on 2006-06-02
Really weird - just installed Dapper n getting it all set up. gedit has been working fine for days and all of a sudden if i use
```
sudo gedit
```
nothing happens at all - it just sits there. However if i use gedit as a normal used it starts up ok. Ive reinstalled it but to no avail

thanks in advance

---

### Post by edwina on 2006-06-02
I'm only a newbie, but I've had this problem myself for a couple of reasons ...

You might want to verify that you have the right access privileges. If you don't have write access, nothing comes up on the terminal when you try to edit a file. Upgrading might have messed with your Users setttings I suppose.

Try ```
gksu gedit
``` instead. I had a similar issue in KDE Dapper, where only ```
kdesu kwrite
``` will launch the editor.

Hope that helps.

---

### Post by mental_drummer on 2006-06-02
I gave that a go but got this message
```
(gedit:14806): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

```
Nice try tho! Its really annoying having to use nano all the time...](*,) 
Any more ideas???

---

### Post by MattCarp on 2006-06-02
[QUOTE=mental_drummer]Really weird - just installed Dapper n getting it all set up. gedit has been working fine for days and all of a sudden if i use
```
sudo gedit
```
nothing happens at all - it just sits there. However if i use gedit as a normal used it starts up ok. Ive reinstalled it but to no avail

thanks in advance[/QUOTE]

This works for me, without a problem.  Can you sudo other commands without a problem?

I'd check to make sure /usr/bin/sudo wasn't corrupted, and also check your path, but I'm just grabbing at straws.

---

### Post by mental_drummer on 2006-06-03
ok thanks guys - it seems to have stopped doing it now and starts fine...
well all's well that end's well
thanks

---

