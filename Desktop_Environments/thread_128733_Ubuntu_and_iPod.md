---
title: "Ubuntu and iPod?"
date: 2006-02-12
forum: Desktop Environments
---

### Post by KevNice on 2006-02-12
I have an iPod nano that I want to run on Ubuntu. I'm assuming I can't install the iPod or iTunes software off the disc, so I tried just connecting the iPod. An iPod icon popped onto my desktop, and it was there under "Computer", and then afterwards it disappeared. How do I use my iPod with Ubuntu?

Thanks,
Kevin

---

### Post by handy on 2006-02-12
Hopefully the following link will solve your problem:

[http://ubuntuforums.org/showthread.php?t=103071](http://ubuntuforums.org/showthread.php?t=103071)

---

### Post by KevNice on 2006-02-15
Hey, thanks for the link! But...

It was going well until the part when it says to open fstab using:
sudo vim /etc/fstab

The instructions to say to add a device to this file, so that ipod can be mounted to it. But if I try to edit it off the desktop, its locked as a read only and won't let me change it to writable so that I can add that line. When I am in sudo, I am able to edit it, but after I paste in the line /dev/sda2.. (etc), I can't find any kind of save button, so I just close the window.. but that apparently doesn't work, because when I try to open it again there is some kind of conflict, and the change never gets saved.

How do I edit the fstab file?

Thanks

---

### Post by gosh on 2006-02-15
sudo gedit /etc/fstab

---

### Post by Suzan on 2006-02-15
My iPod nano works perfectly with gtkpod. I don't have to chance anything by hand at the fstab file.

YamiPod works also very well with the iPod nano.

---

### Post by Edward The Bonobo on 2006-02-15
The wiki pages on iPod support are maybe a little out of date?

I've been running my iPod with gtkpod (in fact, a major reason for my switch to Linux was that I couldn't run iTunes in Win98 and then heard about gtkpod) - but I've found some problems with it.  

However...I'm hearing very good things about amaroK - plus their site actually has a decent user handbook, partlu compensating for it being named after a Mike Oldfield album.  

Then...a couple of days ago, I heard about Banshee.  And today I heard that Rhythmbox now supports iPods.

Has anyone had experience of using any of these to manage their iPod?



(oh...and speaking of Wikis...I haven't got the instructions on how to convert video to iPod formats to work: [http://www.ubuntuforums.org/showthread.php?t=127542](http://www.ubuntuforums.org/showthread.php?t=127542)  Any ideas)

---

### Post by Suzan on 2006-02-15
I've tried out: gtkpod, YamiPod, Amarok, banshee, rythmbox

On my computer banshee and rythmbox are quite unstable, so I cannot use them. Maybe I have to try new versions of them.

With amarok it's no problem to put MP3s on the iPod. But I don't manage to make any playlist on the iPod. And amarok is very crude.... it deletes any playlists, which were prepared with any other program before. So if you want to use amarok with the iPod - ONLY use amarok for it.

YamiPod is very cool. No installation needed, only unrar it and go on... it's available for Windows, Mac and Linux. It handles MP3s and playlists very well.

gtkpod is still my favorite. I use the new version 0.99 of it. With that version you can handle album covers and podcasts. For me it works like a charm.

At the moment, you can't put photos on the iPod with that programs. But it's only a matter of time 'til it works, I think! ;-)

---

### Post by Edward The Bonobo on 2006-02-15
Can you save your iPod's database locally with gtkpod v0.99?  I can't see a way to do it in 0.94.  My problem is that whenever I click on anything - eg a playlist - and then click back to the main iPod list, it tries to re-load the whole damned thing...taking about 25 minutes.

Am I doing something wrong?

---

### Post by Suzan on 2006-02-15
Yes.

First I have to import my local files to gtkpod. Once. That may take a while.

The normal order to put MP3s on my iPod is:

- Plug in the iPod
- start gtkpod
- klick on "read" (the db from the ipod will read in)
- then drag & drop new files to the iPod, delete something, make playlists.... whatever.
- finally press "sync" (all the changes where made to the ipod)

Then I have to eject the iPod manually with

```
sudo eject /dev/sde2
```

Once I have read in the ipods DB, it don't reload anything until I sync. Works perfectly for me. But I think I does too with version 0.96, which is to find in the ubuntu respositories. Uhh... you have 0.94? I don't tried that version. Maybe you should test a newer version?

btw: my 70th entry.. hurray!

---

### Post by Ramses de Norre on 2006-02-15
Just for the record: when using vim to edit fstab you need to press esc after inserting is ready, then shift-q to get a command line and type wq! there (w: write, q:quit, !: do not ask confirmation).
But I guess you've done it with gedit allready:)

---

### Post by Edward The Bonobo on 2006-02-17
Yes...it could be a problem with v0.94.  I only installed about 4 weeks ago, but I'm glad they've got 0.96 already.  I'll update and try again.

Praise The Lord for Synaptic!  (or whoever it was that coded it).

---

### Post by Edward The Bonobo on 2006-02-17
Und...herzlichen Glückwunsch zu 70 Postings, Suzan.:)

---

### Post by KevNice on 2006-02-17
Yeah thanks.. I was able to fix it up with gedit. I downloaded and installed gktpod, but I'm having problems transferring songs to the iPod. i think the reason is that there was a conflict with the install, I am currently having problems with the lilypod-data file. So I'm going to try and get that fixed and then reinstall gktpod, and see if it works better

---

### Post by KevNice on 2006-02-17
new problem...

when I open gtkpod, the first thing im supposed to do is click "read iTunesDB". When I click on it, I get this message:

"/media/ipod/iPod_Control/iTunes/iTunesDB' does not exist. Import aborted."

I figured that means the file doesn't exist in the folder /media/ipod on my computer. But it wouldn't let me create the necessary folders, its write protected or something. If this is the problem, how do I make folders in terminal?

---

### Post by binarymelon on 2006-02-17
i had the same problem initially, their may be a linux fix for this but all i did was connect it to a windows pc and launch iTunes it generated the empty file and all was fine from there.  Or I think banshee can generate it for you as well.

---

### Post by Edward The Bonobo on 2006-02-17
Yes, that's precisely it.  The iTunes database has to be set up on a Windows machine in iTunes first.  I believe there are also problems if you go back from gtkpod to iTunes...like you lose your whole database.

---

### Post by KevNice on 2006-02-23
Ok, I connected the iPod to a friend's windows machine and ran iTunes, and uploaded a single song just to be sure. No Problem.

On my Ubuntu machine, I still get the same message when I read iTunes DB. When I try to upload a song, it's telling me that the database structure must be created first. I can't sync anything. Also, I installed Banshee, but when I try to run it, nothing happens.

What's going on here? All I need is for my iPod to work and then I can say that I enjoy Linux. But up til now it's been a headache

---

### Post by larsemil on 2006-02-23
ju can run itunes through cross over office. 

its easy to use, just like windows... 

cross over office costs money. here is some info about it:
[http://thepiratebay.org/details.php?id=3404011](http://thepiratebay.org/details.php?id=3404011)

---

### Post by Manny C on 2006-02-23
As a paying customer of CrossOver, I object to larsemil's link to a pirate site.

Mods: are you reading this?

---

### Post by Suzan on 2006-02-23
[QUOTE=KevNice]When I try to upload a song, it's telling me that the database structure must be created first. [/QUOTE]

So then - create a database structure! After import your DB, go to "File > create DB structure"
(or similar, I have an german gtkpod version)

---

### Post by KevNice on 2006-02-24
Well, that's the problem Suzan, is that I can't Import. and "Create Directories" doesnt do anything.

OK, I have CrossOver office installed now, and iTunes. However, it's not recognizing my iPod on this iTunes. How do I get it to recognize it? (It is mounted properly and gtkpod recognizes it)

---

### Post by KevNice on 2006-02-24
Nevermind.. I installed YamiPod and it works fine! Thanks for the help anyway

---

### Post by sinaen on 2006-03-10
yamipod for windows or linux?

I think that every program for ipod is a bit tricky

and several support them and they all are very messy, isnt itunes supposed to be easy to port to linux?

amongst the programs i found that support ipods are these
amaroK
GTKpod
Banshee
rhythmbox
yamipod
mypod  is java and not tested on windows. i didnt get it to work thou :(
gnupod 
whale

some of these programs i havent really tested but i have tried the tops and try with yamipod now and thats one of the most advanced i think and hope on but it needs to have one song on the player to "reach" it maybe thatll be updated in the future

banshee i dont understand. but as i have seen it seems that that program is the only one in what you can change your ipods name
rhytmbox well not much of an tester there am i started it concluded it was messy and shut it down again :)

whale i found a couple of minutes ago so i havent tested that  yet

---

