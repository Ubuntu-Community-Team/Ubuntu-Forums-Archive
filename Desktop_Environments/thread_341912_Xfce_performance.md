---
title: "Xfce performance"
date: 2007-01-19
forum: Desktop Environments
---

### Post by dewm_solo on 2007-01-19
Good morning to all of you,

Being a developer and slowly making my switch to linux, I decided to try a lightweight environment. So I installed xfce yesterday.

Now, I have to say that I love the way it feels and once very well setup and customized I believe it can turn out into one hell of a great desktop environment.

But.....

The project claims to be lightweight and that xfce should be extremely fast ....bla bla bla.

Can someone help me figure why my install of xfce seems to be slower than my Gnome install? Frames(Windows) move sluggishly in xfce...they seem to drag ...when in gnome they respond and follow my cursor perfectly. Opening a new window or application seems to be heavier on the system than it is in gnome.

Does it have to do with the build of xfce? or the current state of the project.....or am I just becoming paranoid and imagining things? :confused:   :-k 

Thanks for taking the time to read through this. Let me know what you think.

---

### Post by ahaslam on 2007-01-19
> **dewm_solo said:**
> Does it have to do with the build of xfce? or the current state of the project.....or am I just becoming paranoid and imagining things? :confused:   :-k 


It's certainty not the current state of the project, it's working nicely here. Though I must add that the 3 major DE's *feel *the same with no apps running on my laptop. It's only when you're multitasking that you'll notice a small difference. If you really want something that's indisputably quick, try openbox. Don't be put off by the default look, it's just as customizable as the others.

> Can someone help me figure why my install of xfce seems to be slower than my Gnome install? Frames(Windows) move sluggishly in xfce...they seem to drag ...when in gnome they respond and follow my cursor perfectly. Opening a new window or application seems to be heavier on the system than it is in gnome.

Strangly I experience the same thing with Fluxbox, that's supposed to be lighter than xfce. I wonder if it's a hardware thing?

Tony.

---

### Post by dewm_solo on 2007-01-19
> **Anthony Haslam said:**
> It's certainty not the current state of the project, it's working nicely here. Though I must add that the 3 major DE's *feel *the same with no apps running on my laptop. It's only when you're multitasking that you'll notice a small difference. If you really want something that's indisputably quick, try openbox. Don't be put off by the default look, it's just as customizable as the others.

Thanks for answering by the way. Alright....I thought that maybe the project was in too early a stage to hit the performance that is advertised on every hardware configurations. It works on my install too and I did find it to be very customizable indeed. I have to say that I like it very very much. It actually sits at the top of my list right now hehe.



> **Anthony Haslam said:**
> Strangly I experience the same thing with Fluxbox, that's supposed to be lighter than xfce. I wonder if it's a hardware thing?

Could be I guess.....driver maybe too....It's just weird that being so much smaller than gnome...and needing much less resources. Yet it appears to make your computer drag more. Although it is well within an acceptable difference, but it should be the same difference the other way around ...with xfce being that much faster. I wonder if a fresh build directly in my environment wouldn't help it.....

---

### Post by ahaslam on 2007-01-19
> **dewm_solo said:**
> Could be I guess.....driver maybe too....It's just weird that being so much smaller than gnome...and needing much less resources. Yet it appears to make your computer drag more. Although it is well within an acceptable difference, but it should be the same difference the other way around ...with xfce being that much faster. I wonder if a fresh build directly in my environment wouldn't help it.....

Also worth consideration is the built in compositor - do you have any transparency's or shadows? When I enable these it makes it noticeably slower than either gnome or kde.

> There a 10 kinds of people. Those who understand binary...and those who don't. :-k  

Nice sig ;)

---

### Post by igknighted on 2007-01-19
Xfce will struggle at times, depending on what programs you are using.  If you are using your KDE or even some Gnome apps in Xfce, more libraries are loaded and the performance gain is lost.  Avoid OpenOffice and Firefox especially if you want to cut down on programs that will drag your system down as these are two of the worst (try epiphany and abiword/gnumeric as alternatives).  I personally am a KDE fan, so I'll put in a shameless plug here about common libraries... If you are like me and tend to use lots of windows at once (or at least without restarting) then KDE may be for you.  It preloads many libraries so the base system is more sluggish than other DEs, but it handles a load much better than Gnome (or even Xfce sometimes) because of more efficient library usage (assuming you use native KDE apps (Kopete, not Gaim, Konqueror for web browsing etc.)

---

### Post by dewm_solo on 2007-01-19
> **igknighted said:**
> Xfce will struggle at times, depending on what programs you are using.  If you are using your KDE or even some Gnome apps in Xfce, more libraries are loaded and the performance gain is lost.

Thanks ...great explanation. Makes a lot of sense.

> **igknighted said:**
> Avoid OpenOffice and Firefox especially if you want to cut down on programs that will drag your system down as these are two of the worst (try epiphany and abiword/gnumeric as alternatives).  
Well...having just installed xfce, I haven't had time to try OpenOffice, but starting Firefox was the reason for this post.  So heuh....well looks like you are right hehe. Thanks for the alternatives, I'll give them a shot. I'm a little disappointed though I must say. I will miss my firefox. I just verified something though....the name epiphany rang a bell and I looked it up. It is the gnome web browser. Anyhow I'll give it a try.

> **igknighted said:**
> I personally am a KDE fan, so I'll put in a shameless plug here about common libraries... If you are like me and tend to use lots of windows at once (or at least without restarting) then KDE may be for you.  It preloads many libraries so the base system is more sluggish than other DEs, but it handles a load much better than Gnome (or even Xfce sometimes) because of more efficient library usage (assuming you use native KDE apps (Kopete, not Gaim, Konqueror for web browsing etc.)

Great explanation again...thanks. Something else to look at. I never was the KDE fan, but then again I don' t really have anything against it. I just seem to always make my way back to Gnome for some reason.

I used to love Enlightenment....and even with all its bells and whistles it still manages to run better than xfce on my pc, so I might go back to it.

I want to give xfce a good chance first though. So I'll stick to it for the next week or so and see what comes out of this experience.

Thanks again

---

### Post by alalor1 on 2007-03-21
I think Compositor might have something to do.  My computer ran great and very fast with XFCE 4.4, as soon as I figured out how to turn on compositor, it slowed down to snail pace.  I had to turn it off and now everything is back to normal.  Just not as pretty.

---

### Post by Kobalt on 2007-03-21
I will support igknighted's point : my girlfriend is using an old laptop of mine and I've been quite impressed to see how KDE was performing instead of Gnome, then Xfce...

---

