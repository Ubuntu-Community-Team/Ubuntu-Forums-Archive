---
title: "Learning Linux"
date: 2007-03-29
forum: Education &amp; Science
---

### Post by Pai on 2007-03-29
I've been a Window's user all my life, simply because that's what was directly available to myself.  Now for the first time I've started using Ubuntu (Dapper/Edgy), and am overwhelmed by the whole experience.  We all know that Ubuntu (or other distros) aren't completely usable in their initial state (based on legitimate open-source limitations), so I've had to paste a number commands into my terminal, without evening knowing their meaning.  I'll sadly admit that in a fit of frustration, I resorted to Automatix to retrieve and install codecs/fonts/apps for me.  I regret doing so, simply because I made the move to Linux to learn new things - not to have some script do everything for me.

I'm starting over.  How can I genuinely improve my understanding of not only this specific OS, but also the underlying components. I know relatively nothing about the Linux kernel, and would like to change that. I am uncomfortable with using the command line to achieve tasks, and would like to change that. I don't want some "easy" button, as many new users do.  I don't want to be copy/pasting commands to get things done. I want to, eventually, be at the point where I can do this on my own.

So I ask, can you please recommend some steps I should take in this learning process? This may include online tutorials, published reading, or any other miscellaneous advice you may have to offer. Anything helps really.  Generally, I'm looking to gain a better understanding of Linux as a whole. I don't see my future occupation relying on Linux/Unix administration, but I would like to be familiar with it at least.

Thanks for your time, and apologies for any misguided statements I may have made based on sheer ignorance.

---

### Post by DrMoxie on 2007-03-29
I started off in a similar way, MS products for my entire life, professional and personal, until I decided to cut all my home PCs and laptops over to Ubuntu (4.10).  Now as crazy as it sounds I found [Linux For Dummies]("http://www.amazon.com/Linux-Dummies-7th-Dee-Ann-LeBlanc/dp/0471752827/ref=pd_bbs_sr_1/102-7053428-8413753?ie=UTF8&s=books&qid=1175191613&sr=8-1") and the [Linux Pocket Guide]("http://www.amazon.com/Linux-Pocket-Guide-Daniel-Barrett/dp/0596006284/ref=pd_sim_b_4/102-7053428-8413753?ie=UTF8&qid=1175191613&sr=8-1") to be two very helpful books, not in terms of studying but for provide some basic and easy to digest information.  Beyond that I spent many hours on here reading and occasionally posting as well as using Google to track down information not covered well enough in the Man pages.

---

### Post by gus sett on 2007-03-29
you may find a trip to your local Border's or Barnes & Noble bookstore
helpful.  Many folks use an O/S for years before pondering the family
tree, and you'll find that many easy-to-fathom guides are available for
*unix* as well as the Linux namesake/variants.  You can also piece
together alot by consulting *man*, the native manual (pages)
right from your command line, in the meantime. :arrow:

P.S. if you go for a guide from the shelves, look up kernel in the 
index so that you can gauge if the book contains enough details
to last you a while.  You can easily identify a half dozen publications
with white covers and simply light blue cover print, which are circa 
the founding/foundation days of unix.

> **Pai said:**
> I've been a Window's user all my life, simply because that's what was directly available to myself.  Now for the first time I've started using Ubuntu (Dapper/Edgy), and am overwhelmed by the whole experience.  We all know that Ubuntu (or other distros) aren't completely usable in their initial state (based on legitimate open-source limitations), so I've had to paste a number commands into my terminal, without evening knowing their meaning.  I'll sadly admit that in a fit of frustration, I resorted to Automatix to retrieve and install codecs/fonts/apps for me.  I regret doing so, simply because I made the move to Linux to learn new things - not to have some script do everything for me.

I'm starting over.  How can I genuinely improve my understanding of not only this specific OS, but also the underlying components. I know relatively nothing about the Linux kernel, and would like to change that. I am uncomfortable with using the command line to achieve tasks, and would like to change that. I don't want some "easy" button, as many new users do.  I don't want to be copy/pasting commands to get things done. I want to, eventually, be at the point where I can do this on my own.

So I ask, can you please recommend some steps I should take in this learning process? This may include online tutorials, published reading, or any other miscellaneous advice you may have to offer. Anything helps really.  Generally, I'm looking to gain a better understanding of Linux as a whole. I don't see my future occupation relying on Linux/Unix administration, but I would like to be familiar with it at least.

Thanks for your time, and apologies for any misguided statements I may have made based on sheer ignorance.

---

### Post by 1/0 on 2007-03-29
A good thing is to choose another distro. I used (until last week) Gentoo. You'll learn much more with that distro but you will have much more trouble installing updating. I learned so much and the forum is great. 

I learn by searching for specific problems and solutions. Google is a friend. There are tonnes of books online (s.a. [http://ploug.eu.org/doc/linux-cookbook.pdf](http://ploug.eu.org/doc/linux-cookbook.pdf). (You don't have to buy books unless you want a paper copy, which could be good when the net/computer is down.)

There are wiki:s (s.a. [http://wiki.ubuntu.com](http://wiki.ubuntu.com) and [http://gentoo-wiki.com](http://gentoo-wiki.com)).

If you are like me, books are not fun. Search for specific problems instead.

---

### Post by arbulus on 2007-03-29
Ubuntu is definitely a great distro for the beginner.  You get to wade in without too much shock and can feel reasonably comfortable, but after you start to feel your way around a bit, you may want to try on another distro that might be a bit more complicated.  1/0 mentioned Gentoo, and that would definitely be a fun adventure.  As would Slackware or Sabayon or any other source based distro, where you have to complie programs from source, and in some cases build the OS from scratch.  

I've often found that learning is better if I have an objective.  That is to say, I went about trying to set up a server running Linux for file and print serving, and also trying my hand at web serving as well (you just have to be careful with web or mail serving as some elements may violate your ISP's terms of service).  But that really helped me because I knew what I was trying to do and could look for specific info to help me.  And in doing so, i've learned a great deal about the whole OS in general.    

My example is that I plugged a 500GB external hard drive and 2 printers into the server machine and wanted to share those with 2 Macs, one of which dual booted with Ubuntu.  So that was a great lesson in understanding file sharing across platforms, as well as a basic understanding of mounting drives configuring file systems.  The forums here, as well as linuxquestions.org, ubuntuguide.org, and google were invaluable tools.  I screwed things up a number of times, but I think you learn more from the mistakes you make in that respect.  But finding a problem or an impasse and googling myself crazy really paid off.  One thing that helps also is that if you have a problem and find a solution to it that uses the graphical interface, see if you can also find a solution that you can do through the command line, so that you can see both sides of it.  

Welcome to the community.  Just remember: don't give up.  There's always a solution, and if it's not working, just try another distro, one is bound to work with your system.

---

### Post by kennyhow on 2007-03-30
I've wanted to buy this book ever since I saw it in the book store...but now that 7.04 is due out in July, I might hold back.

[[IMG]http://ec1.images-amazon.com/images/P/0132435942.01._AA240_SCLZZZZZZZ_.jpg[/IMG]]("http://www.amazon.com/Official-Ubuntu-Book-Benjamin-Mako/dp/0132435942/ref=pd_bbs_sr_2/104-4372230-3238360?ie=UTF8&s=books&qid=1175290519&sr=1-2")

Check it out.  It might do you some good.

---

### Post by micha105 on 2007-04-03
If you are already a bit familiar with the dos shell, this could be useful:
[http://tldp.org/HOWTO/DOS-Win-to-Linux-HOWTO.html]("http://tldp.org/HOWTO/DOS-Win-to-Linux-HOWTO.html")

This helped me a lot, when I switched from Windows to Linux my processor's cache was damaged -> Got always errors over errors, no matter what I was doing.
This way I learned a lot, since almost nothing worked like it should have, and I always was trying to get something running.. (was Suse 6.0 by then)

---

### Post by andylow on 2007-04-10
Thanks for that. It really do a great help for me.

---

### Post by bigboy_pdb on 2007-06-12
My response in this thread might be helpful:
[http://ubuntuforums.org/showthread.php?t=467543](http://ubuntuforums.org/showthread.php?t=467543)

---

### Post by mwacky on 2007-06-13
I definitely learned by trial and error.  I installed Ubuntu and broke it beyond my repair capabilities a few times as well as trying a few different distros (Fedora, OpenSUSE, Gentoo).  No doubt that Ubuntu is easy out of the box, and the large user community helps you with your specific customizations whether it is through the forums, docs, or ubuntuguide.org, which is great by the way and would be my top recommendation to new users,

---

### Post by in_flu_ence on 2007-06-14
This forum is the best place to learn about ubuntu and Linux. I generally get answers within 24hours. You really have to break it to learn it. I learn my windows OS that way as well.

In the process, you will also be able to identify unfound bugs which will be helpful to the community.

---

