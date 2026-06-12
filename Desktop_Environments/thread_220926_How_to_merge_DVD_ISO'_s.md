---
title: "How to merge DVD ISO' s ?"
date: 2006-07-22
forum: Desktop Environments
---

### Post by mendieta on 2006-07-22
Hi

I have a bunch of smal DVD Iso's (from a mini-dvd camcorder). I would like to somehow merge each 3 of them into a big ISO, and then burn to a regular DVD. Is this possible ?

Note that you can rip the individual videos, and use a DVD authoring program to put together a DVD, with your customized menues, etc. But unfortunately I have no time for that. I need a quick way to wrap the three ISO's into one. The closest thing I found is this thread: 

[http://ubuntuforums.org/showthread.php?t=111984](http://ubuntuforums.org/showthread.php?t=111984)

But there are no follow-ups, I am not even sure this is a viable solution.

Another alternative could be to use a DVD Authoring program to simple have three items in the menu, each of them loading one of the small-DVD isos. But this doesn't seem possible.

Any suggestions will be greatly appreciated. Cheers !

---

### Post by Dubbayoo on 2006-07-22
> **mendieta said:**
> Hi

I have a bunch of smal DVD Iso's (from a mini-dvd camcorder). I would like to somehow merge each 3 of them into a big ISO, and then burn to a regular DVD. Is this possible ?

Note that you can rip the individual videos, and use a DVD authoring program to put together a DVD, with your customized menues, etc. But unfortunately I have no time for that. I need a quick way to wrap the three ISO's into one. The closest thing I found is this thread: 


By the time you get a workable solution from this thread you could have done just that.

[http://smorgasbord.net/convert_video_linux](http://smorgasbord.net/convert_video_linux)

views best in Opera

---

### Post by mendieta on 2006-07-22
> **Dubbayoo said:**
> By the time you get a workable solution from this thread you could have done just that.

[http://smorgasbord.net/convert_video_linux](http://smorgasbord.net/convert_video_linux)


Thanks a lot Dubbayoo. However, I am trying to avoid decoding/encoding. I really want to **keep the existing menues for each of the mini-DVDs**. These are created automagically by the camcorder, and are very convenient. What I really need is a menu that lets me load each of the mini-DVD's (with its own Menu). Let's see if there are any other suggestions.

---

### Post by mendieta on 2006-07-22
By the way, I already have the iso's for each mini-dvd stored in the hard drive (mostly as a backup procedure). If anyone is interested, this can be done easily from **k3b** (*Copy DVD* option)

---

### Post by mendieta on 2006-07-22
Just for the record, I tried the solution mentioned in the thread I mentioned above:

[http://ubuntuforums.org/showthread.php?t=111984](http://ubuntuforums.org/showthread.php?t=111984)

It works pretty well for **data**. It does not work for video DVD's though. A DVD is expected to have a certain structure, with video_ts and audio_ts subdirectories, etc. This is not preserved using the method suggested in that thread. Oh well. I'll probably give up and burn small DVD's in regular DVD-R media.

---

### Post by JoWilly on 2006-07-22
What you are trying to do is complicated, even in windows.

What you need to do is reauthor a new dvd with a main menu that will call each of the mini-dvd menus. This will be a completely new dvd structure. For this you need a powerfull dvdauthor. I believe Sonic Scenarist can do this (import existing menus and reauthor the full structure), but this is a very expensive app.

With the readily accessible apps it is much easier to author a new dvd with a new menu and importing the videos.

---

### Post by mendieta on 2006-07-23
> **JoWilly said:**
> What you are trying to do is complicated, even in windows.

What you need to do is reauthor a new dvd with a main menu that will call each of the mini-dvd menus. This will be a completely new dvd structure. For this you need a powerfull dvdauthor. I believe Sonic Scenarist can do this (import existing menus and reauthor the full structure), but this is a very expensive app.


This is a great summary of what I need (and why I failed so far)! Oh, BTW, many things are actually more complicated in Windows (I have to use it at work :twisted: ). But I know what you mean, third party commercial application availability.

> 
With the readily accessible apps it is much easier to author a new dvd with a new menu and importing the videos.

Agreed, that's the conclusion of my search. But I went this way, and there is always a problem or two, and authoring each DVD takes too long for the (unfortunately) little vailable time I have to spend on it. ](*,) 

For the time being, I'll keep backups of the mini-isos, and burn them in regular DVD's (DVD-R media is extremely inexpensive these days if you buy a 50 unit pack). I only produce a few (2, maybe 3) DVD's a month on average. 

At some point, soon I guess, there will be much higher capacity DVD type media (blue-ray, whatever). At that point, even 4.7 Gb DVD's will be obsolete. And, hopefully, eventually there will be some software to take, I dunno, 10, 100 DVD isos and make a large DVD dead-easy. Or even some standard mechanism for a DVD player to Navigate through the sessions of a multi-session DVD. We'll see. In the meantime, it is essential to keep HD backups of the movies, since optical media is known to fail over time.

Many thanks for the help **JoWilly**!

---

### Post by JoWilly on 2006-07-23
Yep, you're right. As dvdrs are now about 20c each, its not really worth the trouble :) 

By the way, if you are looking for a **very** good dvdauthoring app that is working on linux, get dvdlab (works with wine and crossover).

The pro version can do what you need (multi vts, multi menu, ... and much more). I think dvdlab is the best you can get working on linux, short of running sonic scenarist in a vmware virtual machine.

[http://www.mediachance.com/dvdlab/dvdlabpro.html]("http://www.mediachance.com/dvdlab/dvdlabpro.html")

[http://www.mediachance.com/dvdlab/comparison.html]("http://www.mediachance.com/dvdlab/comparison.html")

---

