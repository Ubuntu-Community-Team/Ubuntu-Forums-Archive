---
title: "Hard Drive Space Dissappearing"
date: 2009-02-28
forum: General Help
---

### Post by slimjim4959 on 2009-02-28
So this is a pretty odd problem that I am currently experiencing. It seems as though my hard drive space is just disappearing. I have gone through a few forum searches and cleaned out my junk with auto clean and other techniques people have recommended but it still fills randomly. I currently have my root and home on the same 92gb partition. 

I have run disk usage analyzer/filelight and my root directory and home take up about 20gigs. The whole situation is very weird because I had about 10gigs free 5 days and ago and now I have basically nothing left. I haven't been installing any programs or any personal files (except one document).

I guess what I am trying to ask is if there is a way to detect what is taking up my space? Can I post any kind of logfile or perhaps find a program that is doing it? 10gigs is a LOT of space to just lose in 5 days.

Thanks for all your help!

---

### Post by Rinzwind on 2009-02-28
Did you empty trash? :)

---

### Post by entr3p on 2009-02-28
> **Rinzwind said:**
> Did you empty trash? :)

Haha yeah I was about to say that.:lolflag:

---

### Post by talkingwires on 2009-02-28
I just freed up several hundred megabytes by clearing out /var/logs. Apparently, the log files keep piling up, and if you've been running Ubuntu for a while, their file size can really add up.

Another quick way to free up space is "sudo apt-get clean", which will get rid of cached packages from updates and upgrades.

---

### Post by slimjim4959 on 2009-02-28
Thanks for all of the replies:

Yes my trash is empty

I did run clean and autoclean

I will check out my logs file but that doesn't really explain how I lost 10gigs... I checked it and it was only 20megs.

I am wondering if I could upload a log file or something else for people to look at? Could it be a stray program? I can't tell what I am missing.

Why am I taking up a full 92gigs of my hard drive when my root and my home only take up 20 gigs total?

---

### Post by mulligan.can on 2009-02-28
cd to / and then run:

sudo du -xhc --max-depth=1

and post the results for us.

du will print the disk usage of every folder in / letting you narrow down where the stolen space is going to.

---

### Post by slimjim4959 on 2009-02-28
0	./sys
0	./proc
4.0K	./mnt
8.0K	./Recycled
6.1M	./bin
16K	./home_backup
0	./tmp
du: cannot access `./home/leo/.gvfs': Permission denied
16G	./home
16M	./etc
412M	./lib
466M	./opt
7.2M	./sbin
20K	./.Trash-0
60G	./var
47M	./boot
16K	./lost+found
4.0K	./initrd
0	./dev
3.4G	./usr
19M	./root
12G	./media
4.0K	./srv
92G	.
92G	total
leo@Leo-X:/$

---

### Post by linuxisevolution on 2009-02-28
> **slimjim4959 said:**
> 0	./sys
0	./proc
4.0K	./mnt
8.0K	./Recycled
6.1M	./bin
16K	./home_backup
0	./tmp
du: cannot access `./home/leo/.gvfs': Permission denied
16G	./home
16M	./etc
412M	./lib
466M	./opt
7.2M	./sbin
20K	./.Trash-0
60G	./var
47M	./boot
16K	./lost+found
4.0K	./initrd
0	./dev
3.4G	./usr
19M	./root
12G	./media
4.0K	./srv
92G	.
92G	total
leo@Leo-X:/$

Look at what is stored in /var . 60gb is in there. Your home directory is 16gb, which isn't that much..

---

### Post by thtrgremlin on 2009-02-28
var is a place a lot of programs store / dump data, such as logs, but it is also where ftp servers and Apache can hold files. Any chance you have a file server that someone may be dumping files on? my /var/ is 858M and I am running several web sites.

And a question to anyone else out there, and this reminds me, is there a way to use 'ls' to list every file and sort by modified date, and then, say shorten the list with something like | head -n 50.

Just a thought. I have wanted to do that before and been a little lost about how to go about it.

Best luck.

---

### Post by BGFG on 2009-02-28
Can stuff be deleted manually from /var or should they be purged through the terminal? i no longer have e17 installed but there is a 600mb e17_src folder in /var/cache.

---

### Post by thtrgremlin on 2009-03-01
/var/cache holds all cache files for every program. As far as I know, if you delete the cache files for any program that isn't running, it will just get / make them again as necessary making anything there pretty safe to delete. But proceed with caution, never actually done it and that is an educated guess. If it totally hoses your system, be curious to know, but don't blame me.  :)

---

### Post by BGFG on 2009-03-01
Got rid of it, no fireworks yet :) Guess I'm the guinea pig this morning.....

thanks :P

---

### Post by thtrgremlin on 2009-03-01
Glad that helped you. Wonder if slimjim4959 ever had his issue resolved. hmm...

---

### Post by slimjim4959 on 2009-03-01
Hey All. du is really helpful, I never knew about it.

so I realized that sbackup was doing incremental backups and I deleted them and started sending them to an external hard drive. But for some strange reason it hasn't cleared all of the space. I ran du and now it looks like this:

leo@Leo-X:/$ sudo du -xhc --max-depth=1
0	./sys
0	./proc
4.0K	./mnt
8.0K	./Recycled
6.1M	./bin
16K	./home_backup
0	./tmp
du: cannot access `./home/leo/.gvfs': Permission denied
16G	./home
16M	./etc
412M	./lib
466M	./opt
7.2M	./sbin
20K	./.Trash-0
382M	./var
47M	./boot
16K	./lost+found
4.0K	./initrd
0	./dev
3.4G	./usr
59G	./root
12G	./media
4.0K	./srv
92G	.
92G	total


Why does my root suddenly have 59g? When I run du on it I get this:

leo@Leo-X:/root$ sudo du -xhc --max-depth=1
9.8M	./.lotus
12K	./.dbus
8.0K	./.gconfd
20K	./.config
4.0K	./.pulse
59G	./.local
376K	./.gconf
4.0K	./.debtags
420K	./.gstreamer-0.10
4.0K	./.wapi
4.0K	./.aptitude
28K	./.xine
4.0K	./.gnome2_private
7.0M	./.cache
4.0K	./.gvfs
8.0K	./.hplip
4.0K	./Desktop
204K	./.gnome2
480K	./.synaptic
12K	./.kde
8.0K	./.nautilus
59G	.
59G	total


It's odd because none of that adds up to 59gigs. But it's also like 60gigs just suddenly transferred somewhere else. I've looked around in Nautilus and I just can't find the culprit. This is getting very frustrating because my program is getting to the point where programs are starting to crash. My pidgin won't load, my thunderbird won't get email, my firefox doesn't have bookmarks, a history, or an address bar. The system is getting very very bad. Any insights on this? And yes my trash is empty.

Thanks again for all of your help!

---

### Post by slimjim4959 on 2009-03-01
OK... wow I am an idiot. So I found that I guess I didn't empty my trash? I found the files in .root/.local/share/trash

The deleted backup files are split into two folders "files" and "info."

I gksudoed into nautilus and I shift deleted the files. I think this covers my problem. Boy that was a rookie mistake...

---

### Post by thtrgremlin on 2009-03-02
Yeah, your post before had 59G in /root/.local and I was trying to think why you would have ANYTHING in that directory. Guess you figured it out  :)

Was it growing as you deleted stuff, or what? Was the original issue resolved?

---

