---
title: "$PATH &amp; user, root, boot/login questions."
date: 2006-06-16
forum: Desktop Environments
---

### Post by DagMan on 2006-06-16
Hi,
I noticed that something wasn't loading on startup.
I opened a terminal and typed "echo $PATH" and got almost nothing.

I think I've fixed the problem as user but I'm not certain.
Right now I get as user: 
/usr/local/bin:/usr/bin:/bin:/usr/bin/X11:/usr/games

And as root:
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games


I found the info for user in another file.  Does it look right?  Does root look right?

Also, fixing it for the user account doesn't seem to have fixed it when I log in.  Notably, something in /usr/local/bin is not running from sessions-> Startup Programs but runs when I type it in as user.  I've screwed up more than I understand here.
Where else should I be looking for PATH, or whatever variables are needed, to be set and what should I be setting it to?

If it sounds like I've overwritten more than just that in a file, that would be helpfull to know as well so I can pull things out of a backup if I need to.  As it is, I don't know what I would even need.

Thanks.

---

### Post by lamego on 2006-06-16
You are not usually required to change the system PATH, next time make sure you install the applications to the proper path.. /usr/local is not a standard for ubuntu...

---

### Post by DagMan on 2006-06-16
[QUOTE=lamego]You are not usually required to change the system PATH, next time make sure you install the applications to the proper path.. /usr/local is not a standard for ubuntu...[/QUOTE]
/usr/local/bin is a standard place to put ones own scripts.  They were working fine on login and now they are not but work fine as root and as user.  My user path was also very badly screwed up with usr/bin being the only thing in it.  I wasn't asking how to modify it but what it's supposed to look like so I can make sure I fixed it correctly.



After looking a little more, it's perhaps now fine (If what I posted is okay) except things in /usr/local/bin that were working and have stopped working at login, possibly as a result of me tinkering around with GDM trying to get it to function with automatic login properly after the updates.  I can't for the life of me think of what exactly I could have done though since it had a serious impact on what I found myself able to access as a normal user as well.

Can someone, if nothing else, open a terminal and post the output to the following:

echo $PATH

and then again as su
... so I can feel satisfied with that for now.

If anyone can additionaly shed some light on the question of what happened to my login recognising /usr/local/bin that would be helpfull too.

Thanks in advance.

---

### Post by Nobber on 2006-06-16
As my normal user, $PATH is
```
/home/rjd/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games
```
As root, it's
```
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11
```

---

### Post by DagMan on 2006-06-16
Thanks Nobber.
I'll actually sleep better tonight after looking at someone else's.

---

### Post by ayoli on 2006-06-16
seems that PATH env var is stocked to /etc/environment
upgrades should overwrite this file i guess.

---

### Post by DagMan on 2006-06-17
It didn't overwrite that one.
It does appear that it was the update though... or my playing around with it, that caused the problem, so I think.  I changed my sources.list to this 
[http://www.ubuntuforums.org/showthread.php?t=185758](http://www.ubuntuforums.org/showthread.php?t=185758)
and got an update to a few things inluding GDM.  It fixed the problem I was having.  
This version of GDM also works with autologin.
The only other thing I did was this:
[http://www.ubuntuforums.org/showthread.php?t=74197&highlight=prelink](http://www.ubuntuforums.org/showthread.php?t=74197&highlight=prelink)
but I don't imagine that was what fixed it.

---

### Post by Qapris on 2006-09-07
[Qapris.Com]("http://www.qapris.com/forum") Opened.

---

