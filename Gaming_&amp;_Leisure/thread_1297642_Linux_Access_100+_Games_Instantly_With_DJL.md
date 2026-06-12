---
title: "Linux: Access 100+ Games Instantly With DJL"
date: 2009-10-22
forum: Gaming &amp; Leisure
---

### Post by Sealbhach on 2009-10-22
I'm just checking this out, installing Urban Terror to see how it does. Looks pretty good and someone put a lot of work into this:

[http://maketecheasier.com/linux-access-100-games-instantly-with-djl/2009/10/17](http://maketecheasier.com/linux-access-100-games-instantly-with-djl/2009/10/17)

[IMG]http://images.maketecheasier.com/2009/10/djl-main.png[/IMG]

[IMG]http://images.maketecheasier.com/2009/10/djl-game-types.png[/IMG]

[IMG]http://images.maketecheasier.com/2009/10/djl-installation.png[/IMG]

.

---

### Post by AllRadioisDead on 2009-10-22
Woah, I've gotta check that out :P

---

### Post by Nevon on 2009-10-22
Hey, I worked on translating that! :D

And yeah, it is pretty neat if you're into games.

---

### Post by Inkpot on 2009-10-24
I tried and tried to get this to work, but I keep getting the same error:

 File "djl_main.py", line 1052, in <module>
    window  = Ui_Djl(app)
  File "djl_main.py", line 924, in __init__
    self.cree_reps()
  File "djl_main.py", line 290, in cree_reps
    os.mkdir(config(info=2)+'/jeux')
OSError: [Errno 13] Permission denied: '/usr/share/games/jeux'

It looks like there was a problem with where I made the default installation path for games, however I can't get the configuration screen to come back up so I can change anything. Can anyone help?


Inkpot

---

### Post by handy on 2009-10-26
Thanks for the head's up, I just installed it on Arch. :)

---

### Post by handy on 2009-10-27
I've been checking it out, & it installs all inside its own directory nest.  When you use DJL to uninstall it does it cleanly & quickly.  It has its own .djl/libs/ directory where downloaded files dependencies are stored & made available to other games which helps speed up future installations that require the same file(s).  Also when you delete a game, the dependencies that it bought with it stay in .djl/libs which is how it should be.

I like that .djl/ can be put where you desire, so for those that are into distro hopping, they can have .djl/ on a partition that won't be effected by the system changes that they go through.

I'm still testing it with smaller less demanding games at this stage, as I'm using the open-source drivers for my ATi GPU.

I'll convert back to the dreaded Catalyst before long & see how DJL handles the big guns.

---

### Post by carnagex420x on 2009-10-27
sounds like how Steam is setup.

lol i was late. even on the main page "It is inspired by Valve's Steam software for Windows." well there ya go - [http://en.djl-linux.org/](http://en.djl-linux.org/)

---

### Post by handy on 2009-10-27
Yes apparently it is inspired by the Steam way of doing things.

I've never used Steam, so it is all hear say for me. :)

---

### Post by handy on 2009-10-28
By the way, it's 122 games at the moment. ;)

---

### Post by handy on 2009-10-28
I installed the catalyst support for my AMD/ATi GPU today, & further tested DJL.

I have found that a few games don't just install as they are supposed to in the DJL way, but certainly most do.

A little feedback from users will quickly solve the few installation problems.

I have installed some large 3D games, with not a problem during installation or using DJL to access/start them.

I'm thinking that if DJL maintains support it will become a very popular & efficient way for Linux users to handle their games, & not just their FOSS games either.

---

### Post by johnboy1313 on 2009-10-28
the force is strong with this

---

### Post by handy on 2009-10-31
[I]**[Edit:]** I've edited this post as what I had said in it I have found to be completely inaccurate (thankfully). :)

The guys at DJL are still enthusiastic for the project, I made a stupid mistake when I was trying to contact them.

I'm sure the problem that I have had with registering on their forum will be sorted out before too long.

All good news in the end. :)[/I]

---

### Post by ant2ne on 2009-10-31
*Two Thumbs up*

Install was easy. And limited users (the kids) can get their own games. Hours and hours of entertainment.

Many of the games don't "just work" and require a little skilled (more skill than the kids have) to get them to work. 

I'm getting ALOT of > Error with bloodfrontier. 
Here is the error string: 

bin/bfclient: error while loading shared libraries: libSDL_image-1.2.so.0: cannot open shared object file: No such file or directory


Suggestion, install the library libSDL_image-1.2.so.0

For more information, you can go to the menu 'Information/Show games's output'Types of errors

> ant2ne@cygne-buntu:~$ ls -l /usr/lib/libSDL_image*
lrwxrwxrwx 1 root root    25 2009-05-10 10:32 /usr/lib/libSDL_image-1.2.so.0 -> libSDL_image-1.2.so.0.1.5
-rw-r--r-- 1 root root 48744 2008-02-11 21:20 /usr/lib/libSDL_image-1.2.so.0.1.5
ant2ne@cygne-buntu:~$ 
So, I'm not sure why I'm having this problem

---

### Post by handy on 2009-10-31
**@ant2ne:** So far I've had to install OpenAL & PyGame on my Arch system.

Beyond that (as stated earlier in this thread I think) I got 27 errors with one game which I had to manually close, one after the other, but DJL was downloading & installing the files into the ~/.djl/libs/ .  

I deleted another game that also added a few files to the above mentioned /libs/ , & observed that the DJL downloaded dependencies stayed in the ~/.djl/libs/ which is nice.

I don't know if you have noticed, but there is a menu option with a list of all(?) of the dependencies in the DJL repo', which I have thought that it may be a good idea to just go through & install all of those to begin with anyway.

I have also had a game or two not install due to an unobtainable dependency.  These are bugs.  Which when I finally get access to the DJL forum I will post.

I hope something in the above was of some assistance. :)

---

### Post by ant2ne on 2009-11-01
thanks for that advice. It helped a lot. Click repository from the drop down menu and then libraries. It'd be nice if one could mass select them and hit download.

More of the games are working now. Lots of fun! Sauerbraten is pretty cool.

Now my problem seems to be "can not display video mode" and black screen on several of the games. I can still hear the games splash through the speakers, but I have to CNTL+ALT+Backspace to get back my visuals. Games that do this to me are teeworlds and Urban Terror and Smoking Guns. I've got a 256Mb Nvidia running on an AMD dual core system, so I don't think it is resources I'm lacking. I'm thinkin I should launch with a command line. Any advice?

---

### Post by handy on 2009-11-01
I can't help you with that beyond advising you to install any games that give you trouble or aren't in the DJL repo' via other means (apt or whatever) & if it is convenient move it into the ~/.djl/jeux/<game name>/ & then make a shortcut to it in the DJL games panel, so your children or anybody can still easily access all games from the one location.

If any games you install are difficult to move for whatever reason, it doesn't matter, as you can still make a shortcut to them, even if they are Wine games, which is nice. :)

I have moved one or two, just because I'm like that... ;)

---

### Post by handy on 2009-11-01
> **ant2ne said:**
> 
Now my problem seems to be "can not display video mode" and black screen on several of the games. I can still hear the games splash through the speakers, but I have to CNTL+ALT+Backspace to get back my visuals. Games that do this to me are teeworlds and Urban Terror and Smoking Guns. I've got a 256Mb Nvidia running on an AMD dual core system, so I don't think it is resources I'm lacking. I'm thinkin I should launch with a command line. Any advice?

I've had a thought (they come slowly these days :)) on the video mode problem; I'd have a poke around in the ~/djl/jeux/<your game>/ & see if you can find any config files there, nested in another directory or whatever.  Sometimes it can be quite obvious to the uninitiated what to change to make something like video mode more suitable to the system.  A little trial & error can be required.

If you do find any solutions like that, post them in this thread, & perhaps the DJL forum, (if you can manage to successfully make an account, you will be doing better than I! ;)

---

### Post by lovinglinux on 2009-11-01
Looks really nice. I'm currently testing it.

---

### Post by ant2ne on 2009-11-07
> **handy said:**
> I've had a thought (they come slowly these days :)) on the video mode problem; I'd have a poke around in the ~/djl/jeux/<your game>/ & see if you can find any config files there, nested in another directory or whatever.  Sometimes it can be quite obvious to the uninitiated what to change to make something like video mode more suitable to the system.  A little trial & error can be required.

If you do find any solutions like that, post them in this thread, & perhaps the DJL forum, (if you can manage to successfully make an account, you will be doing better than I! ;)I changed the desklop resolution to 800x600 and the "can not display video mode" and black screen does not occur on several of the games. Now I need to figure out if there are launch options or config files to modify these games on launch.

Anyone know if this will work on a Mac PPC ubuntu system?

---

### Post by Ericj1186 on 2009-11-08
Is it possible to change the installation directory of the games?  I like to keep my games installed on a second hard drive, for the sake of space.  Can I do this and how?

---

### Post by 569874123 on 2009-11-08
Menu->Settings->Game install directory(or something like that).

---

### Post by neojames on 2009-11-08
Does anyone know whether this is 64bit combatable cause my laptop cant handle this, so I was thinking about putting it on my desktop.

---

