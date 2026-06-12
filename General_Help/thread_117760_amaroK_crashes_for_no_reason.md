---
title: "amaroK crashes for no reason"
date: 2006-01-15
forum: General Help
---

### Post by DownloadTHIS on 2006-01-15
Whenever I start up amaroK, since yesterday (I didn't change anything), it starts up like normal, I see a little 0% progress meter at the botom next to the number of tracks that says to the left of it "Multiple background tasks running". Then it crashes. The terminal output says

```
benyamin@ubentu:~$ amarok
amaroK: [Loader] Starting amarokapp..
amaroK: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
kbuildsycoca running...
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
benyamin@ubentu:~$ kio (Scheduler): FATAL: BUG! _ScheduleJob(): No extraJobData for job!
kio (KIOConnection): ERROR: Header read failed, errno=104
kio (KIOConnection): ERROR: Header has invalid size (-1)
kio (KIOConnection): ERROR: Header read failed, errno=104
kio (KIOConnection): ERROR: Header has invalid size (-1)
kio (KIOConnection): ERROR: Header read failed, errno=104
kio (KIOConnection): ERROR: Header has invalid size (-1)


```

---

### Post by Mgcross on 2006-01-16
[QUOTE=DownloadTHIS]Whenever I start up amaroK, since yesterday (I didn't change anything), it starts up like normal, I see a little 0% progress meter at the botom next to the number of tracks that says to the left of it "Multiple background tasks running". Then it crashes. The terminal output says

```
benyamin@ubentu:~$ amarok
amaroK: [Loader] Starting amarokapp..
amaroK: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
kbuildsycoca running...
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
benyamin@ubentu:~$ kio (Scheduler): FATAL: BUG! _ScheduleJob(): No extraJobData for job!
kio (KIOConnection): ERROR: Header read failed, errno=104
kio (KIOConnection): ERROR: Header has invalid size (-1)
kio (KIOConnection): ERROR: Header read failed, errno=104
kio (KIOConnection): ERROR: Header has invalid size (-1)
kio (KIOConnection): ERROR: Header read failed, errno=104
kio (KIOConnection): ERROR: Header has invalid size (-1)


```[/QUOTE]
SAme problem here....any help?

---

### Post by Luke Redpath on 2006-01-18
I'm also having this problem, started yesterday!

---

### Post by eqisow on 2006-01-18
What version of amarok/KDE are you guys running?

---

### Post by DownloadTHIS on 2006-01-19
Amarok 1.3.1. I'm using XFCE 4.2, not KDE.

---

### Post by apswartz on 2006-01-21
I have upgrade to 1.3.8 and it still crashes...

alan@omicron:~$ amarok
amaroK: [Loader] Starting amarokapp..
amaroK: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
amaroK: [Loader] amarokapp probably crashed!
alan@omicron:~$ /usr/lib/amarok/amarokapp
Segmentation fault
alan@omicron:~$

---

### Post by DownloadTHIS on 2006-01-21
[QUOTE=apswartz]I have upgrade to 1.3.8 and it still crashes...

alan@omicron:~$ amarok
amaroK: [Loader] Starting amarokapp..
amaroK: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
amaroK: [Loader] amarokapp probably crashed!
alan@omicron:~$ /usr/lib/amarok/amarokapp
Segmentation fault
alan@omicron:~$[/QUOTE]

I also upgraded to 1.3.8, but for me this solved the problem. Odd...

---

### Post by quadomatic on 2006-03-05
i have the same problem...

---

### Post by Randomskk on 2006-03-05
I was getting random crashes with 1.3.8, but upgrading to 1.4beta fixed it for me.
That said, upgrading to 1.4beta was more crash happy than 1.3.8, but not that it's installed it's damned nice :D

---

### Post by ComplexNumber on 2006-03-05
this is the reason why i don't use amorak. i really don't know why people want to use amorak when its so buggy, temperemental, and unreliable. all that integration in kde isn't helping the reliability of many applications either, and is just helping to make the applications crash more frequently than they do already. i personally can't see the point of using mega-bloated applications like amorak that do everything but only half as well as many specialist applications do. i personally prefer to use lots of small and specialist applications. this has the advantage that the applications rarely crash (the more complex an application, the more likely it is to go wrong, in general), faster execution, better functionality because  the application is specialised.
amorak is overrated given its many problems.

---

### Post by Randomskk on 2006-03-05
[QUOTE=ComplexNumber]this is the reason why i don't use amorak. i really don't know why people want to use amorak when its so buggy, temperemental, and unreliable. all that integration in kde isn't helping the reliability of many applications either, and is just helping to make the applications crash more frequently than they do already. i personally can't see the point of using mega-bloated applications like amorak that do everything but only half as well as many specialist applications do. i personally prefer to use lots of small and specialist applications. this has the advantage that the applications rarely crash (the more complex an application, the more likely it is to go wrong, in general), faster execution, better functionality because  the application is specialised.
amorak is overrated given its many problems.[/QUOTE]

I'm not so sure; once I got amaroK 1.4 it's been stable as a rock, and it manages everything fast and without problems.
Things like getting album artwork, stats, the plugins (web control one is SO useful) and all that are really useful little things to have.

---

### Post by ComplexNumber on 2006-03-05
[quote=Randomskk]I'm not so sure; once I got amaroK 1.4 it's been stable as a rock, and it manages everything fast and without problems.
Things like getting album artwork, stats, the plugins (web control one is SO useful) and all that are really useful little things to have.[/quote] i had no end of problems with it freezing...especially when adding the playlists. it was on suse and mandriva.

---

### Post by poekie on 2006-03-11
The problem I've got with amaroK is that when I start it, it crashes and takes X with it, leaving me at the loginprompt.
Even when I'm not even trying to play a song: on startup, probably while reading the collection. I have tried gdb but because X restarts I'm not sure what it says before it crashes.
When a friend set up a clean X with ion as windowmanager, and I vnc'd my amarok there, it didn't crash. Our conclusion: kde got something nasty?
First: one evening normal use, I press 'stop' > amarok crashes, taking X with it
moments later, normal use, just crashes, taking X with it
and from then on on amaroK startup

oh, using kubuntu breezy and amarok 2:1.3.99+1.4beta1-0ubuntu3 (which is the latest I could get using repos with some tips&tricks pages)

---

### Post by WelterPelter on 2006-03-11
I like amarok, but it is kind of buggy. Where did you guys pick up a .deb of 1.4beta?

---

### Post by ComplexNumber on 2006-03-11
> it crashes and *takes X with it* thats the price to pay for KDE integration.


it may be an idea to use an older but more stable version of amarok.

---

### Post by poekie on 2006-03-11
> **ComplexNumber]thats the price to pay for KDE integration.
[/quote]
Yeah, but it's such a cool program  said:**
> 
it may be an idea to use an older but more stable version of amarok.
I began with 1.3.7 which started the crashing, and I tried updating because every single time I start it it crashes. 1.3.8 and the one I mentioned all have the problem. So it might not be amarok but KDE itself or something.

---

### Post by poekie on 2006-03-11
[QUOTE=WelterPelter]I like amarok, but it is kind of buggy. Where did you guys pick up a .deb of 1.4beta?[/QUOTE]

[www.czessi.net](www.czessi.net), found it somewhere on these forums

---

### Post by aysiu on 2006-03-11
AmaroK's working just fine for me.

People use it because it has a lot of features.
If you don't need a ton of features, JuK is a good replacement and has a lot more stability.

---

### Post by ComplexNumber on 2006-03-11
why not use kscd? it always worked fine for me.

---

### Post by z-vet on 2006-03-11
kscd plays audio-cd's, not mp3 or ogg stuff. 
And for amaroK...it does not crash here. I use self-compiled SVN and only problem i had was when i tried to use it with wrong TagLib (version other, than devs use). But i don't know any other app that provides even half of amaroK's functionality.

---

### Post by poekie on 2006-03-14
Finally, I found out that some weird file was crashing my amaroK and it's working fine now. Unless I try the stopbutton. In the normal view, it doesn't work *at all* (i.e. not even clickable) and in the menu it does the nice trick crashing with X alongside. Any ideas?

---

### Post by dfaure on 2006-10-11
I just fixed the KIO crash.
[http://www.ubuntuforums.org/showthread.php?p=1604859#post1604859](http://www.ubuntuforums.org/showthread.php?p=1604859#post1604859)

---

