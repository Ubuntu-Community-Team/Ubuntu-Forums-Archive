---
title: "The Application &quot;nautilus&quot; has quit unexpectedly."
date: 2006-06-24
forum: Desktop Environments
---

### Post by NIlushan on 2006-06-24
Hi Guys,

I recently Installed Dapper Ubuntu on my PC, and from the first boot itself nautilus was giving a error and closing  :confused:  . I tried reinstalling it from many mirror sites, but it still gives the same crash error,

would someone please tell me what I should do to make nautilus work  :-k 

I have attached the bug report that was generated with this

Thanks a Lot,
Nilushan

---

### Post by NIlushan on 2006-06-24
Guess no one can help me :(

---

### Post by awbassett on 2006-06-26
I also have this error. On another machine that was upgraded from breezy to dapper, this doesn't happen. It only happens on my machine that was a clean install to Dapper. It also happens when I boot up the Live CD to install.

---

### Post by jonrkc on 2006-07-20
If this is the problem where the error message says glibc failed to allocate an enormous amount of memory (almost 2 Gigabytes), then it's the same thing that's happening to me, too.  It didn't happen till the last few days, and I'm unaware of making any drastic changes in that time.  I started with a clean install of Dapper in June, and Nautilus worked fine till three or four days ago.  Now it crashes like that every time.

A Google search shows the same problem happening to users for the last few YEARS.  I didn't find any post that had a solution to it.

---

### Post by jonrkc on 2006-07-25
I was on the IRC channel #ubuntu and learned that running Nautilus with the sudo command can mess things up; it seems I'm supposed to use gksudo for Gnome apps (incl. Nautilus), kdesu for KDE apps, and gksu for Xubuntu apps.  This was all news to me.  

So I ran Nautilus using gksudo and it loaded normally.  That made me think something in my usual-user ("jon")'s directory was at fault.  Sure enough, invoking Nautilus as jon, it crashed over and over.

So I tried creating a new user, "ted."  I gave him the same privileges as jon.  I copied all Jon's files to ted's home directory and chown'd and chmod'd them so they were his to work with.  

Ted was able to run Nautilus just fine.  With jon's files.  But jon couldn't run it with the same files!

At this point I didn't know what was up.  I got rid of the user ted and all his stuff.  I had to do this after ted logged out.  So no X session was running.  

After ted was killed off, jon tried to open an X session and the server authority file repeatedly timed out and prevented it.  I tried going to init 1 and back to level 5 where I normally work; no dice.

So I rebooted.  Still the same problem.  Over and over.

Then I opened Midnight Commander in the console to see if I could determine anything.  As jon, I was not allowed to delete the existing .serverauth file, which was no surprise; but what WAS a surprise was that the act of TRYING to somehow started an X session--and now I can run Nautilus as jon!

I have no idea what this means.  I do know that this "memory allocation" kind of problem is very common, to judge from a Google search, and I didn't see one single concrete solution to it in searching dozens of posts from 2001 on.  Apparently it can be solved by hit-or-miss techniques, but that's not very comforting, is it?

**UPDATE: **Next time I started Nautilus, it occupied almost 100% of my RAM and swap space both.  My swap space almost never gets used.  I was able to get to a console and kill Nautilus's processes--had to do it as root.  

Something's still badly wrong.  I guess I'll just give up on Nautilus.

---

