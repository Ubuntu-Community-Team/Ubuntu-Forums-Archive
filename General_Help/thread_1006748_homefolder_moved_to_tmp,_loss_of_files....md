---
title: "/home/folder moved to /tmp, loss of files..."
date: 2008-12-09
forum: General Help
---

### Post by jokoon on 2008-12-09
Hello :)

Trying to help me connect my ubuntu laptop to a suse10 network at my school, my teacher moved my home dir /home/moli to /tmp/moli and set it my home dir in /etc/passwd, changing my user id and stuff, thinking about the sticky bit of /tmp.

Later, I just couldn't find any of my files, I understood that Ubuntu just cleans /tmp before shutting down, I was quite horrified.

I tried to recover my files with [[COLOR="Blue"]ext3grep[/COLOR]]("http://www.xs4all.nl/~carlo17/howto/undelete_ext3.html"), a program that read the structure of an ext3 file system to analyse its journal etc., but it wasn't able to find a name of files I was looking for, and the tutorial is a little too complicated for me.

I'm just asking if there is someone who could tell me how cron.thinggie or rcS (or an ubuntu script that cleans /tmp) does its job, give me an advice or help me in my quest to recover these files I planned to backup but didn't in time... :-(

I'm begging !

I also posted [[COLOR="RoyalBlue"]there[/COLOR]]("http://groups.google.com/group/ext3grep/browse_thread/thread/e5a4914b15e36b49/895150165418adbc#895150165418adbc").

---

### Post by albinootje on 2008-12-09
Undeleting files in ext3 is much more difficult than in ext2.

Some months ago i spend some hours at the possibilities of undeleting 1 file in ext3 after a colleague deleted a file by mistake. Eventually i gave up.  You might want to take a look at this, but don't have high hopes.

[http://freshmeat.net/projects/ext3undel/](http://freshmeat.net/projects/ext3undel/)

P.S. Your teacher needs a basic Linux-course ;-)

---

