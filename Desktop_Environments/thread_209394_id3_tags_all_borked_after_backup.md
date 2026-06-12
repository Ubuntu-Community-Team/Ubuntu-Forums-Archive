---
title: "id3 tags all borked after backup"
date: 2006-07-05
forum: Desktop Environments
---

### Post by ddales on 2006-07-05
Hi all, I decided to try out Ubuntu 6.06 after being a long time Opensuse user.  I have a problem though that I need help with.  I haven't been able to find an answer.

With Opensuse 10.1 and Amarok 1.38 I downloaded a bunch of music that I bought from allofmp3.  When I opened up Amarok, or any other player, all of my music tags were nice and neat.  Artist, Album, Track, etc....

After installing Ubuntu, Rythmbox just didn't do it for me so I installed Amarok.  Then I did the upgrade to Amarok to 1.4.  It seems to work fine with one exception.

After I copied all of my mp3 files back to the hard drive from a standard K3b Data DVD they look fine.  I have all the songs seperated into their folders by album name.  Double click and I can play the songs with the default player, I think it's xine or something, dunno, hard to tell.

However, if I try to import my collection into Amarok, all the id3 tags are completely scrambled.  For instance, if I choose to play ACDC/Back in Black, I will suddenly hear a track from The Dark Side of the Moon.  

Also, when viewing the collection, all the folder names for the allofmp3 files that I downloaded are all screwed up.

All the mp3 files and folders that I ripped myself, using GRIP, appear fine in Amarok and in their correct order with their correct names, etc......

Any ideas?

I don't want to have to edit everything one by one.  I have hundreds of files from allofmp3 and that would be just plain annoying!

Thanks in advance!

---

### Post by Thund3rstruck on 2006-07-05
I have a massive collection myself (75GB) and I'm so paranoid that I keep them all on a W2K3 server (read-only) since I've had so many crappy applications (Windows Media Player, MCE, realplayer) destroy my tags. 

If it comes down to it and you must re-tag the collection use MP3Tag.de
[http://www.mp3tag.de/en/](http://www.mp3tag.de/en/)

in Wine or VMWare. It's the best program out there for tagging and it's fast. I was able to recover from a Win Media Center tagging rampage last year in a matter of hours by having the tool automatically re-tag all my music based on their filenames (%trackNumber% - %Artist% - %Album% - %Title%)

---

