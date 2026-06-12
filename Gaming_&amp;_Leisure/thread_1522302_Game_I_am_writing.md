---
title: "Game I am writing"
date: 2010-07-02
forum: Gaming &amp; Leisure
---

### Post by JDShu on 2010-07-02
Because I am narcissistic, I wanted to draw attention to a clone I am making of a game I loved when I was a kid. I started writing this exactly a week ago in my spare time and I'm hoping that i can finish and release it quickly. I waste a lot of time on the internet though, so besides satisfying my need for attention, I thought I'd up the ante and try to get people interested in it so that I can be motivated not to disappoint.

For those of you that care about these things, I plan to open source this project eventually, but I am a huge noob, so the code is so messy at the moment its embarrassing :P. Thus I will follow a cathedral model since this is really about me trying to improve my programming skills rather than leveraging the power of open source.

You can visit my blog for details, but for the impatient, here is a short video of what I've done so far:
[URL="http://dl.dropbox.com/u/5597392/map_and_game.avi"]
Gameplay Video[/URL]

**New**: Alright, pretty much finished. I'm going to leave this project for a while, but I might come back later and add to it.

[IMG]http://dl.dropbox.com/u/5597392/wizardcity.png[/IMG]

[Released Game Here]("https://sourceforge.net/projects/wizardcity/")

---

### Post by vegetarianshrimp on 2010-07-02
Looks cool! Keep us updated.

---

### Post by djinnkeeper on 2010-07-03
It's admirable of you to buckle down and teach yourself the skills you know you're going to need, to do what you know you want to do.  Keep it up! :KS

---

### Post by Yneth on 2010-07-03
Very interesting, reminds me of this old Nintendo game called Tanks or something, remember it very vaguely .

---

### Post by belkinsa on 2010-07-03
Looks like a good game, keep it up!

---

### Post by JDShu on 2010-07-06
> **Yneth said:**
> Very interesting, reminds me of this old Nintendo game called Tanks or something, remember it very vaguely .

Battle City ;)

I'll probably add a lot more advanced features over time, but for now, its a clone.

---

### Post by efikkan on 2010-07-06
Keep up the good work!

What kind of rendering are you using? SDL?

---

### Post by kingrobdun on 2010-07-06
Cool game, it reminds me of my first game project.

---

### Post by Narcarsiss on 2010-07-06
With a lot more levels built-in "scenario like" this has a lot of potential.

Will be watching closely

P.s I have great Photoshop skills if i ca be of any help just pm me

---

### Post by JDShu on 2010-07-07
> **efikkan said:**
> Keep up the good work!

What kind of rendering are you using? SDL?

I use pygame, which uses SDL, yeah.

---

### Post by JDShu on 2010-07-18
Update, I've basically finished all the core elements of the game. Now I'm just giving it polish with additional, and hopefully original graphics. Oh, and try to get some sound in there. Next week will be a month since I started this project and I think I will stop spending all my free time on it. 

I'll make the source available (more to let people critique since I doubt it'll actually be useful to people :P) and try to create binaries. I will probably start on a different project, but I will add features and graphics as I long as I am interested. 

[Current Status]("http://dl.dropbox.com/u/5597392/July_18_2010.avi")

This was a great experience and I learned a lot from this project, including the basic game loop, setting milestones for myself, creating maintainable code, and of course lots of python. I encourage anybody who is interested in programming to make a simple game like this because there is no better teacher than experience :D

You can follow my progress on my blog, where I recorded a video every 2 or 3 days.

---

### Post by kiplingw on 2010-07-18
Very cool. Add a little OpenAL and you're solid.

---

### Post by JDShu on 2010-07-18
> **kiplingw said:**
> Very cool. Add a little OpenAL and you're solid.

Hmm I'm not too familiar, is it better than the sound methods in pygame?

---

### Post by kiplingw on 2010-07-18
Don't know too much about pygame, to be honest with you. However, I'm sure there are Python bindings for OpenAL by now.

---

### Post by JDShu on 2010-07-18
Ahh right, ok. Yeah I've been putting off sound. But I'll be having fun composing some tunes :D

---

### Post by kiplingw on 2010-07-18
Definitely. If you like tracker tunes, they might go well with your game. You can use MikMod for playback.

---

### Post by JDShu on 2010-07-24
Well, [URL="https://sourceforge.net/projects/wizardcity/"]here's the source.
[/URL]
Run the wizardcity.py file with python to play it.

```
python wizardcity.py
```

It uses pygame as a dependency.

I'm trying to make exes for Windows and debs for Ubuntu, but its really something I have no experience in, so it'll take a while :P

---

### Post by kiplingw on 2010-07-25
I don't have time right now to play it, but for packaging, I can give you some tips. For Windows, I recommend NSIS. For Debian packages, I recommend you take a look at the Ubuntu Packaging Guide.

---

### Post by JDShu on 2010-07-25
> **kiplingw said:**
> I don't have time right now to play it, but for packaging, I can give you some tips. For Windows, I recommend NSIS. For Debian packages, I recommend you take a look at the Ubuntu Packaging Guide.

Whoo deb packaging looks seriously complicated... I don't even know how to properly make a tarball with setup.py. I spent all my free time making an exe today, I guess I'll use my next day off with debs.

---

### Post by kiplingw on 2010-07-25
Don't worry, it's only complicated the first time you learn it. You don't have to really re-learn it again and you'll find that Debian packaging is very powerful and there is almost always a good reason why they make most of the decisions that they do. The Ubuntu Packaging Guide is pretty solid and is an excellent reference to have on hand.

---

### Post by JDShu on 2010-07-25
Yeah I took a look at the guide. It looks pretty good, I just need to sit still and go through it :D Its probably a useful skill to learn anyway.

---

### Post by kiplingw on 2010-07-25
Definitely. I recommend [**this**]("http://www.amazon.com/Autotools-Practioners-Autoconf-Automake-Libtool/dp/1593272065/") book as well.

---

### Post by ayyork on 2010-07-26
it has taken me 10 minutes to figure out what to say. How did you create that and how long did it take. i was wondering because i would like to learn how to make a living off of things like that.

---

### Post by JDShu on 2010-07-26
> **ayyork said:**
> it has taken me 10 minutes to figure out what to say. How did you create that and how long did it take. i was wondering because i would like to learn how to make a living off of things like that.

I used Python and Pygame to make it. I started the project on June 25th and completed it yesterday, July 25th. 

I too would like to make a living this way, but I'll need to up my skills some more first :D

It was a great experience.

---

### Post by JDShu on 2010-07-26
Well.. it already is complete haha. I still have to make a deb package, but if you have python and pygame, you can download the source and run it.

---

### Post by ayyork on 2010-07-27
thanks for the tips ,and i would like to play your game

---

### Post by JDShu on 2010-07-27
> **ayyork said:**
> thanks for the tips ,and i would like to play your game

its playable now :D

You can download it from the link in the OP.

---

### Post by ayyork on 2010-07-27
i am new here what does op mean?

---

### Post by JDShu on 2010-07-27
The first post of this thread :D

---

### Post by ayyork on 2010-07-29
it is not leting me play it

---

### Post by JDShu on 2010-07-29
whats the problem?

---

### Post by ayyork on 2010-07-31
wait got it to work asked a friend

---

