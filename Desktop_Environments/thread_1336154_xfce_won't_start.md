---
title: "xfce won't start"
date: 2009-11-24
forum: Desktop Environments
---

### Post by scummy on 2009-11-24
first off, i've looked at other threads about this, but the problems described are different or the solutions (e.g., deleting various .conf files) haven't worked.

for some reason i was messing around with my resolution in xubuntu karmic, and i put it to a low one. the screen went light blue and the computer was totally unresponsive, so i had to restart it. from the login screen, when i select xfce, it seems like it starts trying to load, and then doesn't. i have logged in as root and xfce will start, but it won't when i log in normally. i logged into an xterm session, and installed lxde, and it will start normally. i've even tried purging and then reinstalling xfce, and it still doesn't work.

this all started when i changed the resolution, so i figured it had something to do with that, but i changed my xfce display settings xml file to the correct resolution, and it still doesn't work.

any more ideas? i don't really want to reinstall yet (i have to move a bunch of files off of the hard drive before i can do that, anyway).

---

### Post by XubuRoxMySox on 2009-11-24
I haven't been able to get LXDE to cooperate, and when I installed it for one more valiant effort, it borked by Xubuntu login screen. Uninstalling LXDE and Openbox restored my Xubuntu to (mostly) normal.

I've learned that LXDE takes the majority of its code from Xfce anyway, and I doubt very much that when LXDE finally "matures" that it will be much different from its parent. But right now the two don't seem to play nice together. At least not on my 'puter. I did keep PCManFM around, though. I find it much easier and more intuitive than Thunar.

-Robin

---

### Post by scummy on 2009-11-24
I only added Lxde after Xfce stopped working, just so that I would have a working DE until I got Xfce working again.

---

### Post by scummy on 2009-11-25
ended up installing gnome, as i need more from my desktop than lxde can give me. gnome is working well, though for some reason, it is still using thunar as my file manager.

---

### Post by t.rei on 2009-11-25
run "nautilus" using the run dialog, select any folder with a rightclick, there, under properties you can edit the 'open with' option, should you want to use another filemanager. I think the gnome default is listed as "File Manager".

---

### Post by Pogeymanz on 2009-11-25
If you are still trying to get XFCE to work, try deleting .cache from your home directory. It might have been messed up when you encountered the first problem.

---

### Post by scummy on 2009-11-27
things seem to have sorted themselves out. no idea why/how, though.

---

### Post by NuxIT on 2012-05-04
Hi, I'm having this same issue now! I was able to get into xfce fine after I just upgraded from 11.10 to 12.04. 

However, while at work I connected remotely and now my desktop won't load at home. It just comes right back to the login window every time I login. :(

I deleted the .cache directories but it's won't let me! Any ideas?

Any help greatly appreciated. This all happened when I was trying to get my xrdp over ssh session to work again. Agghhh.

---

### Post by overdrank on 2012-05-04
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

