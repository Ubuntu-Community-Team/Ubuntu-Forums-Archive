---
title: "Ran the ipod updater in windows, now ipod won't work w/ gpodder"
date: 2006-09-05
forum: Desktop Environments
---

### Post by allenshull on 2006-09-05
Yes, I know I am an idiot for updating my iPod.  Here's my situation:

My iPod is a 30g 5G Video.  It doesn't matter, but it is black.
Computer one is a Windows box at home w/ iTunes.  It holds all my music because it's big and roomy.  It's not Ubuntu because it's in NTFS and has a ton of files, not to mention a ton of windows-only programs I still use (i.e. games). It has no access to the internet.
Computer two is an Ubuntu laptop at my folks' house whose only purpose is to get on the internet to check comics and news and download podcasts.  Because I don't actually listen to anything on this computer, I pretty much only use gPodder to quickly and easily update my podcasts.

So of course my problem is that I like to listen to my 10 gigs of music on my ipod while foolishly also liking to listen to podcasts when they come out.  If I wanted either I wouldn't have a problem.

Now whenever I try to run gPodder it just crashes when I sync or cleanup.  Is there any way to avoid completely reformatting my iPod on my Windows box with iPod software 1.0 and then getting all my podcasts?

---

### Post by dentaku65 on 2006-09-07
I dunno if can helps, but I think the best alternative to itunes is amipod; if you don't know maybe it's worth a try. Is not in the repo, but is easy to install/use even on xp.... and yes you can copy files from pc-to-pc with ipod :cool: 

[http://yep.it/?f0lbhz](http://yep.it/?f0lbhz)

---

### Post by Toxicity999 on 2006-09-07
I hate to dig up the old gem but isn't the ipod easily mountable as a VFS? I understand the convenience of auto checking and downloading Podcasts and such but in the interim doesn't that do? And if you have all of this music backed up already what's the issue with formatting the eye-Beast? Other than minor inconvenience that is. =P

---

### Post by allenshull on 2006-09-10
Sorry.

1:  Amipod, tried it, not to my liking.
2:  There's no "oh no I'm destroyed" problem with my music, yes it is all backed up, but there is an annoyance with constantly having to have either music or podcasts, but not both.

---

### Post by lukew on 2006-09-10
Hi,

Check the disc for errors.

Have you managed to sync from linux yet? You might need to delete the itunes db and recreate it through a linux application; through from my undertsanding this might not let you synch in windows.

Why cant you you just download podcasts onto your hd and then sync from linux? 

Oh, btw, rythumbox can sync podcasts onto your ipod!

Luke

---

### Post by oswaldkelso on 2006-09-10
Have you tried [http://www.yamipod.com/main/modules/downloads/]("yamipod") you can run it from your ipod on osx, windows, and linux or all of them!. I use Juice (ex ipodder lemon) to down load my podcasts and just point yamipod at the downloaded files to build the data base. It is alittle buggy but getting better all the time, you can use itunes with out effecting it.

---

### Post by allenshull on 2006-09-10
Okay, I've officially figured it out.  I started up GTKpod, "Read" the iPod, then "Synced" the iPod, and everything was fine.  I accept the fact that I'm probably going to just do this again when I want to add some new music to my collection on my home-base computer.

1: I could download podcasts on my laptop, transfer them to my home PC, and then add them using Windows iTunes, but, then, they wouldn't be registered as official podcasts on the iPod's own OS, which makes them much easier to find and listen to (especially when I can't remember which I've listened to and which I haven't).

2: Things that haven't worked for me and I won't try them again:  Rhythymbox, Amarok, Banshee, XMMS, iPodder, Amipod, Yamipod.  It's not crazy loyalty to gPodder, it's just that I've tried over the past two months every other option I can find and nothing works perfectly, but gPodder works (by far) least badly.

---

