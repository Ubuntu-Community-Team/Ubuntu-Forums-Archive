---
title: "Should forums have an exclusive grub-2 section?"
date: 2009-08-31
forum: Forum Feedback &amp; Help
---

### Post by kansasnoob on 2009-08-31
I don't know how to start a poll (maybe requires special privileges), anyway I think many questions are coming down the pike regarding grub-2 (I have many) and it seems that a new section in the "main" category would be desirable.

Then we could get some "sticky" notes with links to the Ubuntu wiki, etc, etc.

Otherwise the newbs section is going to be overrun with questions about grub-2 and folks will be struggling with appropriate answers.

Just a thought.

---

### Post by ronacc on 2009-08-31
sounds like a good idea when karmic goes release .

---

### Post by ranch hand on 2009-08-31
I know that I had a lot of quewtions about grub-legacy when I first joined here.

When 9.10 comes out EVERYONE is going to be a noob.

If you look at some of the posts here in "testing", where we may not be the smartest but are arguably adventurous, and see the pissing and moaning about grub2 it makes this idea seem reall good.

Advertised in BIG letters.  A special thread just for reactionary rants.

I like grub2 a lot and more just about every day, but I think a lot is going to hit the fan when 9.10 comes out.

I really think that this is a great idea.

---

### Post by kansasnoob on 2009-09-01
Well, to begin with, the first question regarding grub or boot issues will have to be: post the output of 'grub-install -v' so we can see what version they're running.

Quite honestly I don't like grub-2. Legacy grub works well on my hardware, so I lean towards staying with the "old"!

---

### Post by ranch hand on 2009-09-01
> **kansasnoob said:**
> Well, to begin with, the first question regarding grub or boot issues will have to be: post the output of 'grub-install -v' so we can see what version they're running.

Quite honestly I don't like grub-2. Legacy grub works well on my hardware, so I lean towards staying with the "old"!
I have come to love grub and its power.  I have no problem at all with your attitude.  

Two points;
This is a "done deal" we need to get used to it.

I really think that for future use, on many file systems, grub2 is much better.

Time will tell on that second one.  The symlink boot entry, I think will be what wins people over in the long run as it does not need ANY editing for kernal updates at all.

I have not been able to get the ISO boot entry to work but several folks have (I are simple).  I think this will be popular after we learn how to do it.

It is hard to believe but grub2 is, or will be, more flexible and powerful than grub-legacy.  Remember that when grub-legacy first came out folks were as upset as a bunch of us are now.  I am 57 and understand the reluctance (not saying this is the deal in your case, haven't a clue) by some to learn something new.

This is particularly understandable in view wf grub-legacies great functionality.

I still think a dedicated forum is a real good idea for this new boot loader.

---

### Post by VMC on 2009-09-01
If you go over to the regular Ubuntu forums there is still many topics regarding grub legacy issues.

 I thought a year ago it would be a good idea to have a grub forum. I was surprise to see no mention of it.

---

### Post by slakkie on 2009-09-01
I don't see a need for grub2 sections. If one would do that, you can do the same for:

* apache
* ssh
* apt/aptitude/update-manager/pkg managment
* any other topic that is somewhat popular

---

### Post by miegiel on 2009-09-01
> **ronacc said:**
> sounds like a good idea when karmic goes release .

If "we" start it now the sub-forum would have more content at the end of next month.

---

### Post by drs305 on 2009-10-16
I too support a forum for Grub 2. Initially I was thinking GRUB in general, but Grub 2 would merit its own forum, if for nothing else but to avoid confusion. 

The forum could always be deactivated at a later date once users became more familiar with it and more documentation became available. (Four months after 10.04 LTS is released would be my earliest recommendation.)

I've spent the better part of the last two days composing a G2 page for the official Ubuntu help pages but there are a still a lot of questions and a lot less documentation.

---

### Post by jpeddicord on 2009-10-16
> **slakkie said:**
> I don't see a need for grub2 sections. If one would do that, you can do the same for:

* apache
* ssh
* apt/aptitude/update-manager/pkg managment
* any other topic that is somewhat popular

+1.

A forum for a single topic (grub2) is way too specific and would filter out the support into another area. Where do we stop? It's a slippery slope.

---

### Post by VMC on 2009-10-16
I think it should be labeled Boot troubles or issues instead of specifically grub2. Newcomers don't know yet the difference between grub2 from grub-legacy, but they DO know when they can't boot.

Get them in the ball park and we can then ask or answer their questions.

---

### Post by 23meg on 2009-10-16
Moved to Forum Feedback & Help.

---

### Post by mabovo on 2009-10-16
Would be helpfull to explain the main differences between Grub and Grub2 at the time of Karmic release.

---

### Post by cariboo on 2009-10-17
I think kansasnoob, ranch hand and drs305 have done an execellent job explaining and sorting out grub2 problems. Maybe the threads should go in a megathread like was done for Intel graphics when Jaunty was released.

---

### Post by Elfy on 2009-10-17
not sure that would be such a good idea - there seem to be a fair sprread of issues and a mega thread would mix them up 

I have a 25s wait while grub is loading - others have diffeerent issues - just my tuppennies worth :)

---

### Post by kansasnoob on 2009-10-17
> **drs305 said:**
> I too support a forum for Grub 2. Initially I was thinking GRUB in general, but Grub 2 would merit its own forum, if for nothing else but to avoid confusion. 

The forum could always be deactivated at a later date once users became more familiar with it and more documentation became available. (Four months after 10.04 LTS is released would be my earliest recommendation.)

I've spent the better part of the last two days composing a G2 page for the official Ubuntu help pages but there are a still a lot of questions and a lot less documentation.

Well, that is my thought also.

Consider in only a few days your thread and ranch hand's thread are going to be inundated with questions about grub2.

It can be very, very hard to follow a specific poster as the op is in that case you or ranch hand. I think we've all been trying to help someone at some time or other and someone else "hijacks" the thread rather than starting their own and it can get very confusing trying to sort out who's posting what info.

That said, I've just recently found that under some circumstances starting with a fresh grub2 seems to cure a lot of things. Not hard to do, just rename the old /boot/grub something like /boot/grub_backup and mkdir a new /boot/grub, then purge-remove grub-pc & grub-common, then reinstall the works.

---

### Post by ranch hand on 2009-10-17
> **drs305 said:**
> I too support a forum for Grub 2. Initially I was thinking GRUB in general, but Grub 2 would merit its own forum, if for nothing else but to avoid confusion. 

The forum could always be deactivated at a later date once users became more familiar with it and more documentation became available. (Four months after 10.04 LTS is released would be my earliest recommendation.)

I've spent the better part of the last two days composing a G2 page for the official Ubuntu help pages but there are a still a lot of questions and a lot less documentation.
Is that your work on custom entries?

What else?

---

### Post by maestrobwh1 on 2009-10-17
> **ranch hand said:**
> ... but I think a lot is going to hit the fan when 9.10 comes out.

I really think that this is a great idea.


Yes, it is going to hit the fan.  One of the things I "used" to be able to do when my boot got messed up was to insert any old live linux distro, run grub, then do 

find /boot/grub/menu.lst
(hd1,5)
then 

root (hd1,5)
setup (hd1)

and boom, it was fixed.

I would have NO idea how to save a system if grub decided to point itself to the wrong partition to find its config files:-0

I have been using Kubuntu Karmic since alpha 3.  I am getting used to grub 2.

---

### Post by ranch hand on 2009-10-18
If you can boot to the OS you want from anywhere (I have several 9.10 installs and some grub-legacy using OS' on my test platform) all you have to do is;
```

sudo grub-install /dev/sda

```
You will have to edit the "sda" to suit your needs.  That is all there is to it.  No LiveCD needed.

---

### Post by drs305 on 2009-10-18
> **ranch hand said:**
> Is that your work on custom entries?

What else?

If you are referring to the Title Tweaks - I wrote it but haven't spent a lot of time on them in the past week. The wiki people realized there was no 'official wiki documentation' at the Ubuntu help site - just a link to the regular wiki site. So I've been trying to piece it all together. Every time I think I'm 85% done another 30% jumps out at me. I haven't posted it anywhere but in my 'sandbox'. It should be done in a few days and definitely before the 29th.

I've been tacking the stuff onto my Grub Basics post, although the title is now Grub 2 Guide once you get inside the thread. 

Links in signature to both.

I know there will be a lot of questions on release day, but hopefully Grub 2 will "just work" for most newbies and it can slowly be assimilated into the whole Linux learning experience.  

As for the geeks, there is definitely enough info out there to give them (us?) at least a general clue as to what's going on.

---

### Post by ranch hand on 2009-10-18
YES, the info is coming together.  Being a new as I am the process of incorporating a new thing into Ubuntu has facinated me.

I suppose that the official documentation is always going to lag  just from the nature of the beast.

---

