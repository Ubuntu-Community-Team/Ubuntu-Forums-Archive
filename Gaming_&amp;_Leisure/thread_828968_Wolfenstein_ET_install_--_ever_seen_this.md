---
title: "Wolfenstein ET install -- ever seen this?"
date: 2008-06-14
forum: Gaming &amp; Leisure
---

### Post by glenmo on 2008-06-14
when installing Wolfenstein ET 2.60, the installer doesn't ask me where to install -- just goes directly to the symbolic link...

if i just go ahead and install it, it puts everything to the root of my filesystem.

here's a video: [http://www.youtube.com/v/l3gS7qCb-B8](http://www.youtube.com/v/l3gS7qCb-B8)

anybody seen this before?  know how to fix it?

---

### Post by glenmo on 2008-06-15
please! any suggestions?

---

### Post by Hobgoblin on 2008-06-16
So if you just select OK where you type wtf? then what happens, because everything in your video looks OK to me.

[http://ubuntuforums.org/showthread.php?t=5246](http://ubuntuforums.org/showthread.php?t=5246) suggests using root terminal, you can do **sudo su** if you don't have root terminal.

---

### Post by glenmo on 2008-06-16
the installer should ask me where to install to, with the default location being /usr/local/games/

if i just ok that, it installs to the root of my drive.  

i'll try doing a "sudo su -" beforehand and get back to you, but i'm pretty sure i tried that to no avail.

---

### Post by Hobgoblin on 2008-06-17
> **glenmo said:**
> the installer should ask me where to install to, with the default location being /usr/local/games/

Mine asks me for installation directory before the symlink location.  Whichever way I do it.

> 
if i just ok that, it installs to the root of my drive.  


Can you show us?

I can't remember where I got my installer from but you could try getting it from another site.

---

### Post by Hobgoblin on 2008-06-17
[This may help](https://help.ubuntu.com/community/EnemyTerritory)

I've just tried the version from..

wget -c [http://ftp.games.skynet.be/pub/wolfenstein/et-linux-2.60.x86.run](http://ftp.games.skynet.be/pub/wolfenstein/et-linux-2.60.x86.run)

which works for me.

---

### Post by glenmo on 2008-06-20
ok, i'm back, and still no luck...

[http://www.youtube.com/watch?v=ASG9obybWLk](http://www.youtube.com/watch?v=ASG9obybWLk)


did sudo su -

did wget as in the forum post for installing wolfenstein...

i'm at a loss.  it installed fine on this computer when i had gutsy...

---

### Post by gfk on 2008-06-20
I have just installed et myself and I just use "sudo" instead of "sudo su" which worked just fine and installed in the right place, try that.

---

### Post by glenmo on 2008-06-20
that was the first movie...

---

### Post by gfk on 2008-06-21
Sorry I should have also checked that one.  I just seen the first one and everything seems fine.  I get the same installation path and just installed it there.  It seem like the right logical place to put it.  Why wouldn't you not want to install it there?

---

### Post by Hobgoblin on 2008-06-23
> **gfk said:**
> Sorry I should have also checked that one.  I just seen the first one and everything seems fine.  I get the same installation path and just installed it there.  It seem like the right logical place to put it.  Why wouldn't you not want to install it there?

The path in his youtube vid is for the symlinks.  I get asked for the install path before that.

I'm at a loss, I did it on Hardy, from the file I posted earlier.

Are you sure you don't have it installed already?

Can you post the content of /usr/local/games?

---

### Post by glenmo on 2008-06-24
/usr/local/games is blank... nothing in there.  

i would imagine that root is able to write into that directory.

this is freakin crazy.

---

### Post by Hobgoblin on 2008-06-24
And you definitely used the installer I linked to?

---

### Post by glenmo on 2008-06-24
i used the ubuntu guide you linked to when i started -- you saw when i tried to wget the file, it said i had already done it...

---

### Post by gfk on 2008-06-24
I see, it ask where to install symbolic links instead.

I guess try downloading another installer from somewhere else, search google.


Really odd problem.

---

### Post by Hobgoblin on 2008-06-26
Sorry, didn't see your other vid.

Delete the one you have and wget it again.  That way we are **sure** you are using the **same** copy.

---

### Post by DoktorSeven on 2008-06-26
There should be a GUI installer that's a lot easier to use, try **gksudo ./et-linux-2.60.x86.run** (or **kdesu ./et-linux-2.60.x86.run** for kubuntu).

If you need commandline, try sudo bash et-linux-2.60.x86.run (maybe there's a problem using dash).

---

### Post by glenmo on 2008-11-07
can you believe this?  still not working.

---

### Post by glenmo on 2009-01-13
bump, still nothing...

---

### Post by glenmo on 2009-01-15
i think i may have found a way around this issue...

[http://ubuntuland.nireblog.com/post/2008/12/14/playbuntu-is-now-playdeb](http://ubuntuland.nireblog.com/post/2008/12/14/playbuntu-is-now-playdeb)

using the playdeb repository, i was able to install wolfenstein.  i'm doing it over ssh, so i can't verify that it's playable yet, but at least it's installed...

---

