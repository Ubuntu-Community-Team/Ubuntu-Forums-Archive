---
title: "HowTo Install Grid War 2"
date: 2007-05-23
forum: Gaming &amp; Leisure
---

### Post by nami on 2007-05-23
Hello

I downloaded gridwars_lin.zip but don't know how to install it,

Help...

---

### Post by MonkeyBoy on 2007-05-24
[http://www.getdeb.net/release.php?id=883](http://www.getdeb.net/release.php?id=883)

Try this link.  All you need to do is open the deb with the gdebi package installer and it does the rest.

---

### Post by nami on 2007-05-29
tried that, downloaded it, double clicked it, it installed with no errors, but does not load the game.

---

### Post by barmazal on 2007-05-29
pro game im with 650.000 on hard

---

### Post by nami on 2007-05-31
i can't even get it to work...

---

### Post by jingo811 on 2008-02-21
Me too is having trouble making this game work.
[http://www.getdeb.net/app/GridWars+2](http://www.getdeb.net/app/GridWars+2)
I already setup my ATI with Envy and whenever I launch the game I get kicked out to the GDM.  Now what :confused:

---

### Post by jingo811 on 2008-02-23
Sooo disappointing I tried the debs in Gutsy and Feisty only a black screen followed   X crash.  Unpacked the source file then ran this in terminal "./gridwars"
gridwars_0.0.0+20060309.orig.tar.gz
Still only a black screen followed by X crash. :(

---

### Post by eilu on 2008-02-23
I got mine from happypenguin and it runs with no problems (just unzip to your chosen location)... try that one?

---

### Post by jingo811 on 2008-02-23
I go here and follow the download link which directs me to the same developer webpage that I visited in the past.
[http://www.happypenguin.org/show?Grid%20Wars%202](http://www.happypenguin.org/show?Grid%20Wars%202)
[http://gridwars.marune.de/](http://gridwars.marune.de/)

Unzipped this file then ran "./gridwars" still a black screen and X crash.
gridwars_lin.zip

On the other site it says this:
[http://www.incitti.com/Blitz/](http://www.incitti.com/Blitz/)
August 8, 2006
> 
	Sorry folks... I've had to remove the link to the download.
Email from BizarreCreations:
"We're beginning to feel the effects of
the Geometry Wars clones on our sales via
Microsoft now and are beginning a process to
begin to more robustly protect our copyright
and intellectual property.

Therefore, I'd like to ask you in an amicable
fashion to stop infringing our IP and pull
the game 'Grid Wars' from the internet for download.

I hope you understand and are able to do this
without us having to take further steps."

---

### Post by piterhansel on 2008-05-01
I hope I'm not committing a crime :oops:

I love this game, and I play it since Feisty I think... It works well on Hardy!
Downloaded it from getdeb last year. 

Cheers :popcorn:

---

### Post by mister_k81 on 2008-05-01
No installation should be necessary for the "gridwars_lin.zip" file, I just tried it out, and it seems to be working fine in Hardy. Just unzip it, and put all the files into one folder, then you probably have to download: "libstdc++5", which you can get by opening up the terminal and typing: 

```
sudo apt-get install libstdc++5
```

Or by doing a search in the synaptic. Then, open up the folder with the unzipped contents in it and click on the "gridwars" executable file to start. :)

Edit: Whoops, I didn't realize this thread was almost a year old. 8-[

---

### Post by jingo811 on 2008-05-02
That old file worked as bad as the new ones from the authors homepage it crashed X again.  Guess it's time to upgrade to Hardy soon or it must be something about my hardware that this game doesn't like :(

---

### Post by mister_k81 on 2008-05-04
This game worked for me on Gutsy as well. Maybe it is a hardware problem, or even a dependency one? Is there anyway to check for errors by running the game in the terminal before it crashes X?

---

### Post by piterhansel on 2008-05-05
> **piterhansel said:**
> I hope I'm not committing a crime :oops:

I love this game, and I play it since Feisty I think... It works well on Hardy!
Downloaded it from getdeb last year. 

Cheers :popcorn:


-> Sorry bout that... If I have it I thought other may have it... :confused:

---

### Post by jingo811 on 2008-05-05
> **mister_k81 said:**
> This game worked for me on Gutsy as well. Maybe it is a hardware problem, or even a dependency one? Is there anyway to check for errors by running the game in the terminal before it crashes X?

This is the best I can do error wise.  I looked into /var/log/dmesg also but didn't know what to look for.  Since the programmer was prohibited from further coding on this game making bug reports probably will fall to death ears anyways.   So I guess this game is dead from improvements and fixes. :(
```

bill@gates$ **gridwars &> errall**

XIO:  fatal IO error 104 (Connection reset by peer) on X server ":0.0"
      after 419 requests (48 known processed) with 0 events remaining.
```

---

### Post by piterhansel on 2008-05-08
GridWars 2 is back to GetDeb. Just download and install it. It works for me since feisty till hardy!!

[http://www.getdeb.net/app/GridWars+2]("http://www.getdeb.net/app/GridWars+2")

:biggrin:

---

### Post by illu45 on 2008-05-08
If you are having random crashing, try disabling the game's sound and music (through the config menus). That fixed most of the random crashing for me. As far as installing goes, I would just download the .zip from the [official site]("http://gridwars.marune.de/") unzip it to a directory, open a terminal and navigate to the gridwars directory, then use ./gridwars to launch the game. That way, if it crashes, you should be able to see the error messages and possibly figure the problem out.

---

### Post by GavinZac on 2008-05-08
[http://www.getdeb.net/download/2610/0](http://www.getdeb.net/download/2610/0)

---

### Post by JSuresh on 2008-08-27
i played a ton of gridwars on xp and i'm happy to see it ubuntu.

however, when i tried to run it on ubuntu 7.10, it runs horribly horribly slow (can't be hardware because this laptop could handle the game fine under xp)

---

### Post by cristo-father on 2008-08-28
> **JSuresh said:**
> i played a ton of gridwars on xp and i'm happy to see it ubuntu.

however, when i tried to run it on ubuntu 7.10, it runs horribly horribly slow (can't be hardware because this laptop could handle the game fine under xp)

It ran very well with an nvidia, but after i got my ati i got the same problem.

---

### Post by Shannon_VanWagner on 2009-06-14
Here's the link that did it for me on Ubuntu 9.04 Jaunty Jackalope:

[http://howto.landure.fr/gnu-linux/ubuntu-8-04-hardy-heron/install-grid-wars-on-ubuntu-8-04-hardy-heron](http://howto.landure.fr/gnu-linux/ubuntu-8-04-hardy-heron/install-grid-wars-on-ubuntu-8-04-hardy-heron)

Yes I know the link says "hardy-heron" but it worked for me on Jaunty too!
Cheers!:popcorn:

---

