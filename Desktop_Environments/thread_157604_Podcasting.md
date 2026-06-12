---
title: "Podcasting"
date: 2006-04-09
forum: Desktop Environments
---

### Post by spartan777 on 2006-04-09
Is there a good podcast program out there for linux (or one that works well with wine) that can fetch podcasts using bittorrent and/or rss feeds? I listen to twit, security now, and lugradio often, and going to check them manually gets tiresome. thanks in advance!

---

### Post by John.Michael.Kane on 2006-04-09
this may help you

[http://www.castpodder.net/](http://www.castpodder.net/)
[http://perli.net/projekte/gpodder/](http://perli.net/projekte/gpodder/)
[http://www.peapodpy.org/](http://www.peapodpy.org/)
[http://www.podgrid.org/](http://www.podgrid.org/)
[http://podracer.sourceforge.net/](http://podracer.sourceforge.net/)
[http://www.yamipod.com/main/modules/home/](http://www.yamipod.com/main/modules/home/)

---

### Post by gpeck157 on 2006-04-18
[QUOTE=SD-Plissken]this may help you

[http://www.castpodder.net/](http://www.castpodder.net/)
[http://perli.net/projekte/gpodder/](http://perli.net/projekte/gpodder/)
[http://www.peapodpy.org/](http://www.peapodpy.org/)
[http://www.podgrid.org/](http://www.podgrid.org/)
[http://podracer.sourceforge.net/](http://podracer.sourceforge.net/)
[http://www.yamipod.com/main/modules/home/](http://www.yamipod.com/main/modules/home/)[/QUOTE]

Thanks for this list! I setup gpodder and it works just fine.

G

---

### Post by joflow on 2006-05-23
anyone have any experience with peapod?

I need to use peapod because its cli and I'm using it on a server.

I've set it up, installed urlgrabber, installed bittorrent 4.9, and edited the xml configuration file but when I run the script it doesn't download anything.  Is it that the files haven't finished yet?  How do I know if its actually downloading anything or not?  It created the folder structure (in my case /podcasts/twit and /podcasts/systm) but the folders are empty...any ideas?

---

### Post by adamkane on 2006-05-23
amaroK handles podcasts well (better than any other software in my opinion).

---

### Post by joflow on 2006-05-23
I'm also trying to setup podracer since I found out that its cli as well.

The sample subscription files works well and downloads the podcasts.  When I edit it with my own rss feeds...I end up with no mp3s and a bunch of errors.

This is the terminal output: 

/usr/bin/podracer: line 167: btshowmetainfo.py: command not found
root        : STDERR   Traceback (most recent call last):
root        : STDERR     File "<stdin>", line 6, in ?
root        : STDERR   ImportError: No module named download

It repeats this message a few times then I get:

curl: no URL specified!
curl: try 'curl --help' or 'curl --manual' for more information

---

### Post by keheikev on 2006-05-25
[QUOTE=spartan777]Is there a good podcast program out there for linux (or one that works well with wine) that can fetch podcasts using bittorrent and/or rss feeds? I listen to twit, security now, and lugradio often, and going to check them manually gets tiresome. thanks in advance![/QUOTE]
Just as an aside I happen to listen to twit, leo laportes the tech guy, and often security now. Thats what caught my attention in your thread. 
Keheikev
:KS I wont give up if you dont!

---

### Post by keheikev on 2006-05-25
How do I go about setting up gpodder.? The website doesnt clearly tell me. 
Keheikev

---

### Post by hanzj on 2006-08-04
> **gpeck157 said:**
> I setup gpodder and it works just fine.


I installed [gpodder]("http://perli.net/projekte/gpodder/"), too. But how do i sync the podcasts with my iPod. How do you do it?

---

### Post by omarabdelhaleem on 2008-03-21
Yeah, gPodder definitely works, even in Ubuntu 7.10!

---

### Post by happyisland on 2008-03-29
Weird - gpodder has been really buggy for me. It syncs correctly about 10% of the time, it doesn't delete files that I tell it to delete, it downloads only partial podcast mp3s, etc, etc. I like the layout and the idea, but in its current version I can't recommend it.

---

### Post by mister_p_1998 on 2008-03-29
You want Icepodder, easy small and runs on a cron task

---

