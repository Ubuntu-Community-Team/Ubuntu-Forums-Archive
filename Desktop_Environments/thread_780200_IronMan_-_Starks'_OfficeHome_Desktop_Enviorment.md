---
title: "IronMan - Starks' Office/Home Desktop Enviorment"
date: 2008-05-03
forum: Desktop Environments
---

### Post by Prom1 on 2008-05-03
Hello Everyone,

My first post here, and I'm a curious Ubuntu onlooker. I'm pretty proficient in WinXP/Win2K/WinME, but Linux & I have had major issues in the past (Fedora Core2/4). But now Linux is primed for the average home user (about time) and I mean the common average user (not coder/hacker/whatever).

That said, I already have Gibsy on Live CD and it works beautfully on my old Dell Optiplex GX260 PC. Don't worry I'll be upgrading soon enough.

Now for the reason of my post. In this movie, IronMan (yes I did a search; nothing found here), there are a few quick scenes of Tony Stark using his PC @ home, and one scene in particular where Ms Potts (his assistant) uses his desktop PC. You can IMMEDIATELY tell its Linux (although the home monitors are Apple). It looks AWESOME! And considering DELL servers were used (I couldn't remember seeing them though), I was hoping that someone here could kindly point me in the right direction to getting Ubuntu to look similar to that desktop.

Thanks.

---

### Post by LeoSolaris on 2008-05-03
I haven't seen the movie yet, so if ya catch a pic to post, I could probibly give you some pointers on how to do it.

Leo

---

### Post by Prom1 on 2008-05-03
Unfortunately there isn't one that I can find via Google searching.

---

### Post by LeoSolaris on 2008-05-03
Give it some time. I am sure it will come out. If not, eventually the DVD will come out and you can do a screenshot of the movie.

---

### Post by Prom1 on 2008-05-04
This is the best shot I can find of IronMan's/Starks home PC ... [IMG]http://farm3.static.flickr.com/2143/2409575007_a4ebb99442.jpg[/IMG]

Cannot find one of the office though, folder structure layout was sweet.

---

### Post by kerry_s on 2008-05-04
i heard it looks like a tweaked out kde desktop.

---

### Post by the yawner on 2008-05-04
I suspect the office PC is KDE. It has a Mac-looking interface but the hardware is branded Dell. The other bits are obvious pre-rendered animations.

---

### Post by DJ_Peng on 2008-05-04
Perhaps someone used [Mac4Lin]("http://ubuntuforums.org/showthread.php?t=555373")? ;)

---

### Post by psionfenix on 2008-05-05
Here you go. sorry about the crappy quality, but...you know how it is.
[IMG]http://img518.imageshack.us/img518/8062/sios1sd8.png[/IMG]
[IMG]http://img231.imageshack.us/img231/673/sios2tc5.png[/IMG]


I'm hesitant to say it's KDE, as KDE has that huge bar at the bottom. (might be modifiable, I've never really truly played with KDE). It reminds me a bit of elive (at least the video they have, i refuse to pay 5 euros to 'test' something).

---

### Post by the yawner on 2008-05-05
I attached a KDE screenie of their version of the Mac-menu (which is now missing in KDE4). I believe the bottom panel can be replaced/modified to look/behave as a dock. But I wouldn't know as I've only dabbled a bit in KDE.

The icons animation does remind me of Elive as you have suggested.

---

### Post by psionfenix on 2008-05-05
What is so different about elive as opposed to running enlightenment on ubuntu (i'm running e-gnome right now anyway). I just dont see why it looks so different.

---

### Post by aikiwolfie on 2008-05-05
It could just as easily be Gnome with a Compiz theme and a load of custom widgets. Maybe somebody should just write to the producers and ask?

---

### Post by the yawner on 2008-05-05
Mmm... The only thing I remember with Elive was the animation when opening it's control panel thingie.

I still say it's KDE with pre-rendered animations added as a final effect.

---

### Post by justin whitaker on 2008-05-05
The desktop in Stark's office is KDE....the one in his house, I don't remember...my question is: where is my JARVIS?

---

### Post by dicecca112 on 2008-05-05
I hate to be a kill joy, but it would make better fiscal sense for a movie to just green screen it then to actually take the time and effort to make a desktop theme.

---

### Post by Kraxsis on 2008-05-05
I can't specifically speak for this movie. But I can speak for films that I have worked on and what generally is the case. Is there a chance that it is a tweaked desktop sure. It does happen now and then. However given the advancement of current technology in the effects area there is a greater chance it was a composited screen or a complex "Motion Menu" no real desktop just a movie clip if you will being played back full screen to emulate a desktop. Specifically created to the right aspect ratio and so forth. Lastly like someone suggested, it may be composited in later on as a post production effect. All of the above mentioned are industry standards but it all down to the effects supervisor and director as to what they wanted.

---

### Post by psionfenix on 2008-05-06
It may have very well been done in post. But, isn't that part of the allure of linux? Being able to create awesome stuff? So, while it may not be something pre-existing, it can be created. I think that's more of the direction this is taking anyway (from other posts).

---

### Post by Gunfreak on 2008-05-14
> **Kraxsis said:**
> I can't specifically speak for this movie. But I can speak for films that I have worked on and what generally is the case. Is there a chance that it is a tweaked desktop sure. It does happen now and then. However given the advancement of current technology in the effects area there is a greater chance it was a composited screen or a complex "Motion Menu" no real desktop just a movie clip if you will being played back full screen to emulate a desktop. Specifically created to the right aspect ratio and so forth. Lastly like someone suggested, it may be composited in later on as a post production effect. All of the above mentioned are industry standards but it all down to the effects supervisor and director as to what they wanted.

If we can dream it we can build it.

---

### Post by psionfenix on 2008-05-14
after having watched it again in the theatre, the basic implementation is rather, well, easy. (i'll try to make a mockup if i get time). The issue would be the scrolling folders part, which reminds me alot of like kibadock and AWN. as for the automatic opening...maybe a script? though  i personally wouldnt want the auto open, because it'd make-a-me-crazy

---

### Post by loell on 2008-05-14
sorry, but i think its windows using stardock products ei (WindowBlinds) :biggrin:

---

### Post by psionfenix on 2008-05-14
Could be. Though I've never seen windows look that pretty or move that quick.

Either way, doesnt mean we can't develop it.

---

### Post by loell on 2008-05-14
> **psionfenix said:**
> 
Either way, doesnt mean we can't develop it.

sure,  so here are some proposed specs, then you may start coding.

[B]
stark's home desktop[/B]

one can use enlightenment foundation libraries, as those fancy widgets are not possible using gtk or qt.


**stark's office desktop**

the window decoration can possibly be replicated using compiz theming , though the dark floating cubes is possible through cairo with compositing enabled.

---

