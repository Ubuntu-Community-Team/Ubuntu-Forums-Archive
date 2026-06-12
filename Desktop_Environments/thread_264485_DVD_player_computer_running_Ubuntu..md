---
title: "DVD player computer running Ubuntu."
date: 2006-09-24
forum: Desktop Environments
---

### Post by btboudreaux on 2006-09-24
I have this project in mind that I'm thinking of doing one day. 

I want to build a computer, put all my dvds on one harddrive, and then when I want to watch a movie I can just load it from the harddrive without having to find any DVDs.

I want to use Ubuntu (unless there is something better), but I'm having trouble with some things.

Ok first, I like the xine-ui movie player. Is there anyway I can get it to play a movie directly off the harddrive from a DVD folder or an ISO file? Are there any other movie players that would be better to use in this project that could do this?

My other problems are with ripping dvds in linux but I think the forums have enough info on that. Ok anyhow, anyone??

---

### Post by Groovie on 2006-09-25
> **btboudreaux said:**
> 
Ok first, I like the xine-ui movie player. Is there anyway I can get it to play a movie directly off the harddrive from a DVD folder or an ISO file?


I guess you can use [this]("http://linux.softpedia.com/get/Desktop-Environment/Tools/Mount-ISO-image-2216.shtml") program to mount your iso files to an imaginary drive and then load them in xine, havent tested it yet, but it should work.. :)

---

### Post by ropers on 2006-09-25
try videolan.org/vlc 
it can play the video_ts folders that are on DVDs -- so you could just copy all of them to your HDD and take things from there. 
However, some would consider copying entire the contents of entire DVDs to your HDD a serious waste of disk space. Unless you're a purist and you want bit-for-bit pixel-for-pixel what's on your DVDs, you may want to look into transcoding -- depending on how much lossy compression you're willing to accept, that could yield you up to a tenfold reduction in size. VLC, Mplayer and ffmpeg (ffmpeg.mplayerhq.hu, mplayerhq.hu) all can transcode.

---

### Post by btboudreaux on 2006-09-25
Groovie: I couldn't get that to install. I tried the install script. Oh well.. thanks. Maybe I'm doing something wrong, I don't know.

ropers: Thanks VLC plays ISOs directly and the folders. Although it's not as pretty or as friendly as xine-ui from what I can tell. Doesn't matter, seems to do what I need. The players will probably be updated and Ubuntu Dapper +3 will be out anyhow before I get to do this. 
I know it seems to be a waste of disk space, but disk space is getting cheaper and cheaper. Around January this year I bought a 300 gig drive for 250, now I saw they are selling 500 gig drives for 214. I shrink them down to 4.7, which allows for about 105 movies on a 500 gig drive. And besides, no telling the actual lifetime of a burned DVD. I don't actually have the money to do this now, when I do hopefully terabyte drives will be cheap and I can set this up with two drive. (one for backup)

---

### Post by lonce on 2006-09-25
It would be better to rip the dvd's to drive and convert them to Divx or another format with high quality.  Why use 4 gigs for a movie when you can use 700 megs and fit 4 times as many.

---

### Post by Groovie on 2006-09-26
> **lonce said:**
> It would be better to rip the dvd's to drive and convert them to Divx or another format with high quality.  Why use 4 gigs for a movie when you can use 700 megs and fit 4 times as many.

This is goinh a bit of topic, but for my own sake i do not like the poor crappy quality the divx format gives me, if you se a divx movie against a dvd youl see and hear the difference. I always go for the dvd, then i wont have to irritate myself about bad blackrendering and crappy sound etc.

I can only hope that more and more are seeing the benefits of an high def and high quality experiense. For instanse one buddy of mine downloaded LOTR 1 in High deff, okay it was a huge download, but when Frodo and his chubby friend  is walking over the meddow you can notice details as flies and "dust" on the screen. This is ultimate for me. =)

Anyways, this was a bit off topic and i appologise. I just had to.. :p
To the real matter. About the programme. I couldnt get it to work either. Guess we have to settle for the old "mount -t iso9660 .. etc" ](*,)

---

