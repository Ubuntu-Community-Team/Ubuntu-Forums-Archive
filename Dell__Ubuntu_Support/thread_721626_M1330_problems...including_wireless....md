---
title: "M1330 problems...including wireless..."
date: 2008-03-11
forum: Dell  Ubuntu Support
---

### Post by thelonesquirrely on 2008-03-11
heya, 

So i am trying to make the switch over to being primarily linux, but i am having some trouble with some of the different things failing on my laptop.  Some of them are more general (i could do another post too...) but the most severe are directly pertaining to the hw i am on.  here is the list!  thanks!  

1) the total failure of my wireless card.  it was working well for about a month, slowly it went downhill, now it is dead-ish.  it won't connect to a network, but it will show them (and some time some networks that aren't really there).  
what i've done:
  -I tried to disable/re-enable the broadcom drivers in the restricted driver manager (didn't think this would do anything...and it didn't)
  -I blacklisted the ipw3945 module and added in the iwl one (followed the instructions posted here)....this was the nail in the coffin i think.  after this i couldn't get on to the networks at all. so...
  -I tried an 'undo' - meaning i rm the blacklist file from /etc and then the iwl entry from /etc/modules and added back the ipw module to /etc/module.  still no good.
  
this leaves me with a few questions that i think will help...
  -wtf...how does something just slowly die like that? 
  -what wireless card do i have?  i can't remember from when i purchased it, but i am pretty sure that it was the cheap dell one (i am a poor student...not the first time it has bit me in the tush)
  -at what point is the connection failing?  can it connect, but not to the internet?  only to the local router?

any help you guys can give me here will be monumental!  

2) the dual headphone outs on the front are strange.  I haven't seen anyone talking about this problem, maybe it is just my machine :) what will happen is that if i plug into the leftmost jack my headphones will be working fine, normal volume, etc....but the second output will be totally shut off.  if i plug into the other output the volume will ALWAYS be at max.  this hurt a lot to find out....that login sound is like the growls of a hell beast when at full volume that close to your ear....when i am on my windows side (booo!) they work fine, both controlled by the master vol and in full parallel.  any ideas here?

3) an old version of audacious.  this isn't dealing with my machine in particular, but i am just curious why the version on the repository is REALLY old.  i looked at the website and it is at version 1.4.x (can't remember exactly) but the one that is easily dl-able is 1.3.x.  is there something i am missing?  is there any way to upgrade outside of the ubuntu means?  i tried to just dl it from the site, and install it directly, but i was defeated by it.  i was missing some packages and couldn't find them via the syn manager.  

4) who fixed the visual style problems that were plaguing this laptop?  and can i buy them a drink?!  thanks!

thank you for reading through all of this and any feedback you can give me would be REALLY helpful. as for my skills in linux...well...lets just say i am a skilled absolute newbie :)  thankyouthankyouthankyou!!!

---

### Post by notwen on 2008-03-13
1.
> -what wireless card do i have? i can't remember from when i purchased it, but i am pretty sure that it was the **cheap dell one** (i am a poor student...not the first time it has bit me in the tush)

This fix you applied blacklisting ipw/adding iwl is for the Intel 3945 wifi card.  Let's find out what card you do have.  Open up a terminal and type the following and paste back the output:

```
lspci
```

---EDIT---

If you do turn out to have a dell wifi card you'd need to read over the info on this [thread]("http://ubuntuforums.org/showthread.php?t=713227"), it appears Dell has finally released wireless drivers for their wifi cards.

2.
[This]("http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/Second_Headphone_Jack_Does_Not_Work") fix may/may not fix your issue.

3.
I use audacious myself and had to compile the source for the newest version.  What libs are you missing when trying to compile, maybe I can assist you.

---

### Post by thelonesquirrely on 2008-03-17
Thank you soooo much,
Sorry for the delay, i have been SWAMPED with finals work (tooo many projects...)

I am going to look into that post about the wireless, i do infact have a dell card (a dell 1490 to be precise)  thanks for the heads up, i might pester you again if i can't figure it out :) .

The information about the headphone jack 'fixed' it.  it means that now i can have both headphone jacks in (i think) but the second one is does not cut off the laptop speakers and it is driven by a completely different volume.  this isn't bad, just different.  thanks for the heads up again!


I dl the newest version of audacious (1.5 right?) and extract it onto my desktop. i then open the term and run a ./configure in that directory.  I am getting green lights across the board until i reach this point:  

> checking for glib-2.0 >= 2.14.0 gthread-2.0... yes
checking GLIB_CFLAGS... -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include  
checking GLIB_LIBS... -pthread -lgthread-2.0 -lrt -lglib-2.0  
checking for gtk+-2.0 >= 2.10.0... no
configure: error: Cannot find Gtk+2 >= 2.10.0

then it quits.....i tried looking for the packages via the synaptic package manager, but i don't really know what i am looking for.  any ideas?

---

### Post by Tsega on 2008-03-18
> **thelonesquirrely said:**
> .....i tried looking for the packages via the synaptic package manager, but i don't really know what i am looking for.  any ideas?

Why not go to Add/Remove Applications instead? It's right there just over Audacity Sound Editor, in the Sound & Video section.

---

### Post by notwen on 2008-03-18
> **Tsega said:**
> Why not go to Add/Remove Applications instead? It's right there just over Audacity Sound Editor, in the Sound & Video section.

The Ubuntu repos don't have the newest version of audacious available.  The repos have audacious (1.3.2-4), while the latest release is 1.5.0.

Curious, which version of Ubuntu are you running, Feisty or Gutsy?

---

### Post by thelonesquirrely on 2008-03-18
I have the older version of audacious installed, i just wanted some of the features of the newer one...and well...its newer :)  

i am running gutsy!

---

### Post by notwen on 2008-03-19
I'll try to compile mine on a fresh install on my tinker machine over the weekend, maybe sooner if I get enough time.  I'll post back any issues I run into and see if I can re-trace my steps to acquire all needed libs/packages.  Seems  like I had to manually download and compile 2-3 more packages that weren't in the Ubuntu repos.  =]

---

### Post by thorcik on 2008-04-04
a'propos the audio jacks - have anyone managed to get both jacks working simultaneously? so that i can plug in two sets of headphones. but when I plug into the leftmost jack, the middle one goes quiet. I played with the mixer settings but can't set it right.

---

### Post by drsaamah on 2008-04-04
Hm... my jacks work independently of each other, that is, they can both work at once.  The only problem I have with the headphone jacks is that the physical volume control on my laptop only controls the speakers and the left headphone jack.  So I use the left jack for headphones, and when I come home I use the right jack for my external speakers (since they have their own volume control).
IF this setup seems like something you guys would prefer let me know and I can give you a step by step on how to set it up like this.  However, if you want the headphone jacks to work exactly the way they do in windows we're going to have to find someone else to help us because I haven't been able to figure that out yet.

---

