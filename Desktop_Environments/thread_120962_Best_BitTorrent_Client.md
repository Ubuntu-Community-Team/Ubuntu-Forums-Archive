---
title: "Best BitTorrent Client?"
date: 2006-01-24
forum: Desktop Environments
---

### Post by Rev. Nathan on 2006-01-24
I'm gettin' kind of tired of Azureus. Linux was made to be light and fast, and with java using over 300MiB or memory... not a pretty picture. Not to mention if I couple that with another java application... my memory is raped!

So I've been looking around for a BT client that isn't made with Java. And it appears that there isn't too much, sadly. I found KTorrent, a KDE-based torrent client. I felt as though it would have kind of sloppy coding given its basic website and exterior, and this was no diffrent; it couldn't connect to torrents! It just read 'Stalled', whether the .torrent was from oink, torrentspy... whereever. Lame.

Then I tried my luck with wikipedia. Sure, I got plenty of results, but a lot of them where terminal-based (seriously, in a terminal?), not-yet-avaliable for Linux, or I couldn't compile them (Python is sooo lame; none of that stuff is in my repository). I ended up only being able to use one; Anatomic P2P.

Anatomic was amazing. I've never had a file download so fast (~200 KBps). However, I feel as though it was just luck. And the interface isn't quite what I was looking for. Yay, it had mutilple torrent support, but it wasn't resumable, or had an overview such as Azurues did.

The only thing I can hope for is that one of you knows a client not listed there, or can help me get ABC working. Anyone know of anything awesome?

Also, anyone know anything about anatomic? I'm getting insane speeds that Azureus wouldn't touch. I think it goes into a connection, and actually rapes the benefit of others. I'm getting 300KBp/s right now off of, like, 4 seeders. That's like... not possible! It must have some steriods thrown into it's code not yet publically known.

---

### Post by RAOF on 2006-01-24
Python is sooo awesome :P

If you want to get ABC working, I'll help :)  First, you probably want the python2.4 package.  And python-wxgtk2.6

---

### Post by rippon on 2006-01-24
I really wish my favorite bittorrent program in Windows could be released for linux. uTorrent is only a 105kb .exe in Windows. I think they are making a linux version in the near future.

As for now, ktorrent just because. I wouldnt call myself an advanced bittorrent user though.

---

### Post by Rev. Nathan on 2006-01-24
[QUOTE=RAOF]Python is sooo awesome :P

If you want to get ABC working, I'll help :)  First, you probably want the python2.4 package.  And python-wxgtk2.6[/QUOTE]
Dang, it appears I have both installed. Maybe I just don't get the concept of python... it doesn't have a central library? Seems I always need to download something off-site to get something running...

Anyways, it says I need wxPython and Python, which both are installed (assuming wxPython is python-wxgtk2.6). So I download, extract, and umm... none of the files run! Erm... can you check this out?

---

### Post by Rev. Nathan on 2006-01-24
[QUOTE=rippon]I really wish my favorite bittorrent program in Windows could be released for linux. uTorrent is only a 105kb .exe in Windows. I think they are making a linux version in the near future.

As for now, ktorrent just because. I wouldnt call myself an advanced bittorrent user though.[/QUOTE]
Oh yes, µTorrent was awesome. Used usually under 4MiB of memory... my instant messenger can't even say that! But alas, that isn't so, here. Isn't written in C, though? While I could run it through wine, it would use more memory than java would... deeming that idea useless.

---

### Post by RAOF on 2006-01-24
[QUOTE=Rev. Nathan]Dang, it appears I have both installed. Maybe I just don't get the concept of python... it doesn't have a central library? Seems I always need to download something off-site to get something running...

Anyways, it says I need wxPython and Python, which both are installed (assuming wxPython is python-wxgtk2.6). So I download, extract, and umm... none of the files run! Erm... can you check this out?[/QUOTE]
I'm not terribly familiar with ABC, but the files you're looking for are *.py files.  And to run them, go "python abc.py" from a terminal.  Or perhaps just double click on them.  But the terminal will give you better error messages, if it doesn't work ;)

---

### Post by Noah0504 on 2006-01-24
Well, I think the best BitTorrent client is uTorrent for Windows (I think they are working on a Linux port).  However, have you tried the official BitTorrent client?  It's great as well, and it's extremely light on resources.

---

### Post by kingsidy on 2006-01-24
here is  a list of all the torrents.
[http://en.wikipedia.org/wiki/Comparison_of_BitTorrent_clients]("http://en.wikipedia.org/wiki/Comparison_of_BitTorrent_clients")

you can check the ones that run in linux. I have always used azureus, but i am going to try that anatomic torrent and see whether it is better as far as speed.

---

### Post by Rev. Nathan on 2006-01-24
[QUOTE=kingsidy]here is  a list of all the torrents.
[http://en.wikipedia.org/wiki/Comparison_of_BitTorrent_clients]("http://en.wikipedia.org/wiki/Comparison_of_BitTorrent_clients")

you can check the ones that run in linux. I have always used azureus, but i am going to try that anatomic torrent and see whether it is better as far as speed.[/QUOTE]
Yes, this is the guide I used. Unfortunately, I didn't get many results as you can see. I don't have too big of a problem going back to Az, but I just feel there should be better out there.

---

### Post by vruum on 2006-01-24
As for ABC I got version 3.0.1 running with very little trouble. just put #!/usr/bin/python as the very first line of abc.py, only problem is that the buttons sometimes disappear. comes back when you press something though.

---

### Post by shanghaipi on 2006-01-24
In the dapper flights, there is a bittorrent client called Freeloader that functions much like Azureus, but without all the bells and whistles that Azureus has.  I too would prefer Azureus, but I agree that it is extremely heavy on resources.  Perhaps there is a .deb out there that you can download on the Freeloader website that can work with Breezy.

---

### Post by kingsidy on 2006-01-24
the anatomic torrent seem pretty good. I was getting some pretty good speeds with enough seeds.

---

### Post by Khanater on 2006-01-30
Anyone knows where is saved the Anatomic P2P configuration file? Because i cant save the configuration and need configure ports range.

I cant install Ktorrent with apt-get because dont found the package, someone knows a repository adress that have that package?

Thanks!

---

### Post by kingsidy on 2006-01-30
you have to enable the extra repositories if you want to install ktorrent.

---

### Post by Rev. Nathan on 2006-01-30
[QUOTE=kingsidy]you have to enable the extra repositories if you want to install ktorrent.[/QUOTE]
I think I actually nabbed a .deb from KTorrent's official website ( [http://ktorrent.pwsp.net/](http://ktorrent.pwsp.net/) ). It says it's designed for Kubuntu, so I'm sure it will work all as well in Ubuntu.

---

### Post by saubz on 2006-02-01
I actually use the default bittorrent client.  It is light on resources and I get just as good download speeds with it.

---

### Post by nedkelly on 2006-02-17
I think the one thing that linux is missing the most is a feature rich torrent client with low memory use.

Because of this I have used alot of different clients, Azureus, rufus, freeloader and gnome-bitttorrent. I can not say which one is best since I think that one is just as good (bad) as the next one;) 

But there might be a little light at the end of the tunnel, there is macOS X client/*nix client called [Transmission,]("http://transmission.m0k.org/") it is not so developed yet, but there seems to be a seriuse development going on, so I can only urge people to go to there forum and request the features the need in a torrent client.:D

---

### Post by twigboy on 2006-02-17
Ive had pretty good success with bittornado on windows.  I was planning on trying it out on linux and you can get it through apt-get.

---

### Post by gibson on 2006-02-17
I usr the btcursesclient that runs in a terminal window but i launch them in screen

> sudo apt-get install screen

which is awsome.

you can detatch the terminal session and leave the processes running in the background then reattach at any time. Major advantage is i can check on the progress and even start torrents from anywhere i can use ssh.

even if you do not want to do this for your torrents, i would recommend looking into screen... so simple, but soooo usefull. I will try and write a how-to for it when i get the time.... doesnt look like any time soon though.

welll i guess that is my 2 pence for the day

rock on

---

### Post by horsefactory on 2006-02-17
btlaunchmanycurses.bittornado is my client of choice. I have it running inside screen set to watch /mnt/video/torrents, when a torrent is dropped in that folder it grabs it and starts downloading, when it's deleted the client hops off the torrent. I use the bittornado version over the official as --max_upload_rate is counted for the entire list of torrents running, and not per torrent.

---

