---
title: "CS:S on wine crashes..."
date: 2006-06-07
forum: Gaming &amp; Leisure
---

### Post by echo $USER on 2006-06-07
I have steam installed and working beautifully,  but when i try to load CS:S, the screen shows up then crashes.  Here is the output. 

> > WINEDEBUG="-all" wine Steam
wine: Call from 0x2a00c490 to unimplemented function d3d9.dll.D3DPERF_SetOptions , aborting
wine: Call from 0x7fc0eb30 to unimplemented function dbghelp.dll.SymGetSymFromAd dr64, aborting
Unable to remove c:\program files\steam\shortcuts.dat!
Shutting down. . .

I followed these instructions exactly to install it:
[url]http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO
+Steam&back=HOWTO+INDEX+Wine+Games[/url]

---

### Post by ubu-for on 2006-06-07
Same problem over here! :wink:

[http://ubuntuforums.org/showthread.php?t=182880](http://ubuntuforums.org/showthread.php?t=182880)

---

### Post by echo $USER on 2006-06-07
Woops sorry,

Is the answer here:

[http://www.linux-gamers.net/modules/newbb/viewtopic.php?topic_id=2391&forum=10&post_id=11468](http://www.linux-gamers.net/modules/newbb/viewtopic.php?topic_id=2391&forum=10&post_id=11468)

I am at work, and the firewall here wont let me access it.  And my proxy is down since i formatted/installed dapper.

I'm sure i have the right mozcontrol loaded.

---

### Post by ubu-for on 2006-06-07
[QUOTE=echo $USER]Woops sorry,

Is the answer here:

[http://www.linux-gamers.net/modules/newbb/viewtopic.php?topic_id=2391&forum=10&post_id=11468](http://www.linux-gamers.net/modules/newbb/viewtopic.php?topic_id=2391&forum=10&post_id=11468)

I am at work, and the firewall here wont let me access it.  And my proxy is down since i formatted/installed dapper.

I'm sure i have the right mozcontrol loaded.[/QUOTE]

Your link is broken! Can't login to your forum account.

---

### Post by echo $USER on 2006-06-07
Today is not my day.

Google this

wine: Call from 0x2a00c490 to unimplemented function d3d9.dll.D3DPERF_SetOptions , aborting

It will be the first link.  Thanks.  I just cant wait to get home to find a solution.  I want to get there, fix it, and play.  never to see windows again, well except at work..

---

### Post by Stone123 on 2006-06-07
[http://appdb.winehq.org/appview.php?versionId=1554](http://appdb.winehq.org/appview.php?versionId=1554)

I found this and it worked fine except shuting down at 27 % . 

and all i had to do was type :

$WINEDEBUG="-all" wine Steam.exe -applaunch 10 -heapsize 300000 & 
$wineboot 

and repeat it a comple of times till it passes 27 %.

---

### Post by echo $USER on 2006-06-07
[QUOTE=Stone123][http://appdb.winehq.org/appview.php?versionId=1554](http://appdb.winehq.org/appview.php?versionId=1554)

I found this and it worked fine except shuting down at 27 % . 

and all i had to do was type :

$WINEDEBUG="-all" wine Steam.exe -applaunch 10 -heapsize 300000 & 
$wineboot 

and repeat it a comple of times till it passes 27 %.[/QUOTE]

Yeah, i fixed the steam update problem of failing at 27% last night.  But does CS:S work for you without crashing?

---

### Post by ubu-for on 2006-06-07
[QUOTE=Stone123][http://appdb.winehq.org/appview.php?versionId=1554](http://appdb.winehq.org/appview.php?versionId=1554)

I found this and it worked fine except shuting down at 27 % . 

and all i had to do was type :

$WINEDEBUG="-all" wine Steam.exe -applaunch 10 -heapsize 300000 & 
$wineboot 

and repeat it a comple of times till it passes 27 %.[/QUOTE]

Steam and CSS are already installed, but CSS doesn't start since some updates.

---

### Post by ubu-for on 2006-06-07
[QUOTE=echo $USER]
> 
[http://appdb.winehq.org/appview.php?versionId=1554](http://appdb.winehq.org/appview.php?versionId=1554)

I found this and it worked fine except shuting down at 27 % .

and all i had to do was type :

$WINEDEBUG="-all" wine Steam.exe -applaunch 10 -heapsize 300000 &
$wineboot

and repeat it a comple of times till it passes 27 %.

Yeah, i fixed the steam update problem of failing at 27% last night. But does CS:S work for you without crashing?[/QUOTE]

5 minutes faster! Damn! ;)

---

### Post by echo $USER on 2006-06-07
[QUOTE=ubu-for]5 minutes faster! ;)[/QUOTE]

lol, if it weren't for this forum, I wouldn't have anything to do at work

---

### Post by ubu-for on 2006-06-07
Maybe you have more success with WineCVS/CVScedega?!

[http://winecvs.linux-gamers.net/index.php/Main_Page](http://winecvs.linux-gamers.net/index.php/Main_Page)
[http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Cedega+CVS&amp;amp;amp;amp;back=HOWTO+INDEX+Wine](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Cedega+CVS&amp;amp;amp;amp;back=HOWTO+INDEX+Wine)

[http://ubuntuforums.org/showthread.php?t=118801&highlight=cvs+cedega](http://ubuntuforums.org/showthread.php?t=118801&highlight=cvs+cedega)
[http://ubuntuforums.org/showthread.php?p=1090956#post1090956](http://ubuntuforums.org/showthread.php?p=1090956#post1090956)

---

### Post by echo $USER on 2006-06-07
> **ubu-for]Maybe you have more success with WineCVS/CVScedega?!

[http://winecvs.linux-gamers.net/index.php/Main_Page](http://winecvs.linux-gamers.net/index.php/Main_Page)
[url]http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Cedega+CVS&amp said:**
> 

[http://ubuntuforums.org/showthread.php?t=118801&highlight=cvs+cedega](http://ubuntuforums.org/showthread.php?t=118801&highlight=cvs+cedega)
[http://ubuntuforums.org/showthread.php?p=1090956#post1090956](http://ubuntuforums.org/showthread.php?p=1090956#post1090956)

Would it screw up my wine installation?  I already have call of duty, dvd shrink, dvd decrpter working under it.  I wouldnt want to screw that up.  Please advise.

---

### Post by ubu-for on 2006-06-07
[QUOTE=echo $USER]Would it screw up my wine installation?  I already have call of duty, dvd shrink, dvd decrpter working under it.  I wouldnt want to screw that up.  Please advise.[/QUOTE]

Don't think so. But NO guarantee!

Maybe you should backup/move/rename your ".wine" folder first.

CU (11:30 pm CET)

---

### Post by echo $USER on 2006-06-08
Well i got half-life 2 working, not very well but it works.  CS and DOD work wonderfully.  If only CS:S and DOD:S...

---

### Post by ubu-for on 2006-06-13
[QUOTE=echo $USER]Well i got half-life 2 working, not very well but it works.  CS and DOD work wonderfully.  If only CS:S and DOD:S...[/QUOTE]

CSS works with Wine 0.9.15 again! 47 FPS without sound (winecfg)! :mrgreen:

P.S. Sound doesn't work.

---

### Post by echo $USER on 2006-06-13
[QUOTE=ubu-for]CSS works with Wine 0.9.15 again! 47 FPS without sound (winecfg)! :mrgreen:

P.S. Sound doesn't work.[/QUOTE]

Nice, i'll try it when i get home.  How do i find out what version of wine i have?  Is it> $wine --version?

---

### Post by echo $USER on 2006-06-13
Just updated to wine 9.15;  CS:S and DOD:S now work, and they have sound.

---

### Post by crankcaller on 2006-06-14
what sort of frame rate are you getting there?
I may give it a go as css was crashing on cedega timedemo and so i'm not gonna pay for it!

---

### Post by echo $USER on 2006-06-14
[QUOTE=crankcaller]what sort of frame rate are you getting there?
I may give it a go as css was crashing on cedega timedemo and so i'm not gonna pay for it![/QUOTE]

On the CS:S stress test i got 88fps with 1024x768, AAx4, all low settings, also if i try to change the video setting it crashes.  In windows i get 120 fps with 1024x768 all high settings.

---

