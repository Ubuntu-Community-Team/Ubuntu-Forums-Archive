---
title: "Kiba dock - Jaunty"
date: 2009-05-21
forum: General Help
---

### Post by steigerjb on 2009-05-21
Hey all,

I need some help installing the Kiba Dock in Jaunty Jackalope. I had tried before with Intrepid but I couldn't figure it out. ](*,)

I know docks are really needed in Ubuntu but the Kiba Dock looks like it could be kinda fun to play around with. :D:guitar:

I also know there are other docks but I want the Kiba dock in particular.

---

### Post by gettinoriginal on 2009-05-22
This sites tutorials are usually right on, and try to be simple:
[http://www.ubuntugeek.com/search?cx=017338271194360913207%3Avuzb4jxd_2m&cof=FORID%3A11&q=kiba-dock&sa=Search#1026]("http://www.ubuntugeek.com/search?cx=017338271194360913207%3Avuzb4jxd_2m&cof=FORID%3A11&q=kiba-dock&sa=Search#1026")

---

### Post by keypox on 2009-05-22
only docks i found stable is awn and docky. 

I like docky, it maybe basic but works great

have you tried ubuntu tweak?   I think it adds this stuff for you.[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

---

### Post by steigerjb on 2009-05-24
> **gettinoriginal said:**
> This sites tutorials are usually right on, and try to be simple:
[http://www.ubuntugeek.com/search?cx=017338271194360913207%3Avuzb4jxd_2m&cof=FORID%3A11&q=kiba-dock&sa=Search#1026]("http://www.ubuntugeek.com/search?cx=017338271194360913207%3Avuzb4jxd_2m&cof=FORID%3A11&q=kiba-dock&sa=Search#1026")

Yeah, it installed an everything, somewhat. I don't seem to have any of the cool stuff in this video (which is why i wanted kiba dock in the first place):

[http://www.youtube.com/watch?v=rSZtTo1lXP8](http://www.youtube.com/watch?v=rSZtTo1lXP8)

I have some of it, spinning icons and small "in place" bounces. It doesn't bounce all over the place like in the video. I also don't have the rope or spring for all.  Are they things that need to be added separately?

---

### Post by steigerjb on 2009-05-26
bump

anyone???????????//

---

### Post by chriskin on 2009-05-26
it's a pity that kiba-dock developers won't just make a deb 

hope someone else does in their place, or their trunk works better in the future than it does now, since most parts just won't install correctly in some computers

---

### Post by MasterPoulos89 on 2009-05-26
Hello Again.

I figured out how to compile and install the akamaru folder but I don't know if that will fix the problem.

To compile and install just go into the kiba-dock/akamaru folder downloaded with the script and find the file "configure.in". Edit line 51.

Change
AC_SUBST("$AKAMARU_REQUIRES")

to

AC_SUBST(AKAMARU_REQUIRES)

So just take out the quotes and $ from that line then cd to the akamaru folder from terminal and type 

"./autogen.sh &#8211;prefix=/usr &#8211;exec-prefix=/usr"   or 

"./autogen.sh --prefix=/usr --exec-prefix=/usr --libdir=/usr/lib64"  if you used the 64bit script.

then type "make" then "sudo make install".

After doing this I can't find any effects that your talking bout so I don't know if this will help.

---

### Post by chriskin on 2009-05-26
masterpoulos, are you from Greece?

---

### Post by MasterPoulos89 on 2009-05-26
Yes I am indeed Greek. Did my last name give it away? Why you Greek too?

But I'm not from Greece. I'm born in the US of A

---

### Post by chriskin on 2009-05-26
> **MasterPoulos89 said:**
> Yes I am indeed Greek. Did my last name give it away? Why you Greek too?

But I'm not from Greece. I'm born in the US of A

yeah, it was a bit of a give-away , but people these days think Greek is cool and use it even if they are not Greek , so i had to ask to be sure.  


anyway, back to topic, i'll go try what you said in your first post , since i can't say i have anything else to do right now :)

---

### Post by MasterPoulos89 on 2009-05-26
I updated the script to install the "akamaru" folder on the other post 

[http://ubuntuforums.org/showthread.php?t=972117](http://ubuntuforums.org/showthread.php?t=972117)

But as the post says, there is one error "autoconfig not using gettext" but it installs anyway.

I have no clue about the extra features that are missing or if it has to do with the gettext thing. IDK.

---

### Post by steigerjb on 2009-05-26
> **MasterPoulos89 said:**
> Hello Again.

I figured out how to compile and install the akamaru folder but I don't know if that will fix the problem.

To compile and install just go into the kiba-dock/akamaru folder downloaded with the script and find the file "configure.in". Edit line 51.

Change
AC_SUBST("$AKAMARU_REQUIRES")

to

AC_SUBST(AKAMARU_REQUIRES)

So just take out the quotes and $ from that line then cd to the akamaru folder from terminal and type 

"./autogen.sh –prefix=/usr –exec-prefix=/usr"   or 

"./autogen.sh --prefix=/usr --exec-prefix=/usr --libdir=/usr/lib64"  if you used the 64bit script.

then type "make" then "sudo make install".

After doing this I can't find any effects that your talking bout so I don't know if this will help.

Sorry I don't know what you mean. Here's what I have done:

1. Uninstalled Kiba dock like you said.
2. Went to your post and downloaded Kiba-Dock.tar
   - extracted and placed Kiba-Dock folder in a downloads folder I created in my home folder.
3. Now what? All I see in Kiba-Dock folder is Kiba-Dock_x86 and Kiba-Dock_x64

---

### Post by MasterPoulos89 on 2009-05-26
Yea.....Sorry......I made it confusing. Disregard what I said before. All you have to do now is install the kiba-dock as you did before from my script. I updated the script to install kiba-dock and the "akamaru" folder.

But as I said.....I don't think this gives the extra effects you are looking for.

---

### Post by steigerjb on 2009-05-27
I am waiting to install it til someone who know tells us how to get the COOL stuff \\:D/

---

### Post by MasterPoulos89 on 2009-05-28
Cool.....I guess I'll keep an eye out too. I'm curious to see what more kiba-Dock has to offer. Why not use it anyway though. It still has everything you need from a Dock. I think its pretty convenient to have all the programs you use together waiting for you to click them instead of hiding in the menu bar.

---

### Post by steigerjb on 2009-05-31
Anybody???????????????????????????????????

---

### Post by steigerjb on 2009-06-12
bump

---

### Post by fabounet on 2009-06-13
if you're looking for "cool" effects you might give a look to GLX-Dock.
it also has some nice physics effects like icons exploding or disappearing into a black hole, or bouncing, etc

---

### Post by steigerjb on 2009-06-20
> **fabounet said:**
> if you're looking for "cool" effects you might give a look to GLX-Dock.
it also has some nice physics effects like icons exploding or disappearing into a black hole, or bouncing, etc

Never heard of that dock. Where do i find out about what effects it has?

---

### Post by chriskin on 2009-06-20
> **steigerjb said:**
> Never heard of that dock. Where do i find out about what effects it has?


glx-dock is cairo dock 2 in a new name

---

### Post by steigerjb on 2009-06-21
> **chriskin said:**
> glx-dock is cairo dock 2 in a new name

oh ok. I've heard of Cairo dock

---

### Post by raafaell on 2009-06-29
Kiba Dock will always be the best dock.. i sense.. you guys should watch [this video]("http://www.youtube.com/watch?v=E81Yf1Nyeys") of a WORKING PHYSICS Kiba Dock on The Jaunty!

:guitar:

---

### Post by steigerjb on 2009-06-30
> **raafaell said:**
> Kiba Dock will always be the best dock.. i sense.. you guys should watch [this video]("http://www.youtube.com/watch?v=E81Yf1Nyeys") of a WORKING PHYSICS Kiba Dock on The Jaunty!

:guitar:

Hey Raafaell. I emailed you. Hope you can instruct me on how to get it.

---

### Post by chriskin on 2009-06-30
instructions should be given in the forums so that others can use them as well

---

### Post by steigerjb on 2009-06-30
> **chriskin said:**
> instructions should be given in the forums so that others can use them as well

He is going to do a how to. If he doesn't post it in forums, I'll post it here.

---

### Post by raafaell on 2009-06-30
you guys may wanna take a look at the [HOWTO]("http://ubuntuforums.org/showthread.php?p=7551073") !!! ;)

---

### Post by MasterPoulos89 on 2009-07-01
That "How To" link doesn't bring me to the proper page......it says I don't have proper permissions.....Is it just me or is that the wrong link?

---

### Post by raafaell on 2009-07-01
You guys can try the link once again. :-D

---

### Post by steigerjb on 2009-07-01
> **MasterPoulos89 said:**
> That "How To" link doesn't bring me to the proper page......it says I don't have proper permissions.....Is it just me or is that the wrong link?

I need the link too. I had the same problem as MasterPoulos89. (Don't have permission)

---

### Post by steigerjb on 2009-07-01
i guess he will be back tomorrow w/ the link:-\":frown:#-o

---

### Post by raafaell on 2009-07-02
Howto install kiba-dock with physics on Jaunty: [LINK]("http://ubuntuforums.org/showthread.php?p=7551073") :popcorn:

---

### Post by steigerjb on 2009-07-02
> **raafaell said:**
> Howto install kiba-dock with physics on Jaunty: [LINK]("http://ubuntuforums.org/showthread.php?p=7551073") :popcorn:

Thanks man, I am off to bed now so I'll try it out tomorrow

One question:

for the codes like: gedit kiba-dock/configure.ac 

it's supposed to be "sudo gedit kiba-dock/configure.ac" correct?

I COULD HAVE WORKING KIBA DOCK TOMORROW! YAY! FINALLY! BEEN TRYIN SINCE 8.10 FIRST CAME OUT. I'M EXCITED!

---

### Post by steigerjb on 2009-07-03
> **raafaell said:**
> Howto install kiba-dock with physics on Jaunty: [LINK]("http://ubuntuforums.org/showthread.php?p=7551073") :popcorn:

See my post (#5) in your HOW TO

---

