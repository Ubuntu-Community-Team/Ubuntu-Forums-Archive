---
title: "Secret Maryo Chronicles music"
date: 2009-03-24
forum: Gaming &amp; Leisure
---

### Post by ubuntu27 on 2009-03-24
Hello everyone. 
I have installed SMC 1.7 from GetDeb.net 
And the game works fine.

The problem that I have is that I can not figure it out where to put the music files in. The Music files are not packaged in deb format.

I know that SMC looks for music files at **usr/share/games/smc/music**
But, I cannot create a directory called "smc" since there is a binary executable called smc at usr/share/games

I have been playing around directories tryong to figure it out how to solve this.

The following is what I tried so far:

1)I tried moving the smc binary inside the smc directory. And when I tried to execute the game, it tells me that it is not installed.

2) Tried to put the smc binary inside /usr/local/bin and smc directory where the music resides inside usr/share/games/smc/music

Result: Application not installed

3) Put smc inside /usr/local/games

Result: Application not installed.


I am at lost now.

---

### Post by hikaricore on 2009-03-24
[http://sourceforge.net/project/downloading.php?groupname=smclone&filename=smc-music-4.0_i386.deb&use_mirror=superb-west](http://sourceforge.net/project/downloading.php?groupname=smclone&filename=smc-music-4.0_i386.deb&use_mirror=superb-west)

You should have looked the the SMC site.  :p  They are indeed packaged in deb format.

---

### Post by ubuntu27 on 2009-03-24
> **hikaricore said:**
> [http://sourceforge.net/project/downloading.php?groupname=smclone&filename=smc-music-4.0_i386.deb&use_mirror=superb-west](http://sourceforge.net/project/downloading.php?groupname=smclone&filename=smc-music-4.0_i386.deb&use_mirror=superb-west)

You should have looked the the SMC site.  :p  They are indeed packaged in deb format.

Thank you for the link!!

Now I have to wait 1 1/2 to 2 hours to download. (It is downloading at 2-3kb/s)


EDIT: Wow, it started downloading at 50 kb/s now. ^^ Yey!

HMmm// The deb package comes  with the old version of the music. 
I suppose I can replace individual ogg files with the new one.

---

### Post by BigSilly on 2009-03-24
I love this game.

---

### Post by ubuntu27 on 2009-03-24
Alright, I replaced the old music with the new one that I downloaded fro the Secret Maryo Chronicles official website. 
And it works wonderfully :)

The music directory to replace with the new one is

**usr/share/games/smc/music**

---

### Post by hikaricore on 2009-03-24
Package is still the easiest way to go for most people to be honest.
You should have looked at the top of the sourceforge page and chosen a different mirror if you had trouble downloading.  :p

---

