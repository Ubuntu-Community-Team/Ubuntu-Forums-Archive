---
title: "MUD Set-up and Me"
date: 2010-01-02
forum: Gaming &amp; Leisure
---

### Post by theneowind on 2010-01-02
So I know what platform I want to set-up my MUD in. I have it all zoned, out, decripts written for rooms, mobs, objects, shops and the whole like... The onle thing is. I can't figure out for the life of me how to get the bloody thing to work.

It is tbamud, a continued development of  the codebase formerly known as CircleMUD.  I have worked with it on muds before.

But hosting is new to me.  I'm not wanting to host on the internet just my LAN, but still can't even get the bloody thing to open.

---

### Post by theneowind on 2010-01-18
So I have compiled the program, but I still can not get it to work?  Anyone have any idea as to how I might be able to do this?

A walkthrough would be very helpful.

---

### Post by a-guitarist on 2010-01-20
I'd like to help but, unfortunately, my only experience in building a MUD on an Ubuntu machine used various version of the ROM sources (FastROM, QuickMUD, FLcodebase, etc.).  If it is at all the same, you're going to need the package 'build essentials'- but that was years ago when I was doing this sort of thing.  Before 8.04.  At least I think.

While I understand you've got experience, please don't take anything I say as an insult to your knowledge.  I'm just not sure where your problem is.

When I'd do it, I'd have to set the port in a specific file in the source- I'm not sure if it's the same for circle.  But after that, I'd have to do a make file, then ./startup & (basic build stuff)

After that, I'd just connect to the IP of my local machine (127.0.0.1) with the port I selected  (Rom Default was 4000, I think).  If I wanted to connect to it from another machine on my network I would just put in that machines IP.

At the tbaMUD website, I caught a snippet of info saying "For compiling under Ubuntu, read /doc/README.UNIX (from the MUD's root directory)", so I'd suggest checking that out.  I don't have the ability, right now, to download and check it out myself- but if you get stuck drop another post here and I'll see if I can help some more (which is supposing I helped at all right now ;:D )

---

### Post by sedition on 2010-01-23
After you've compiled, you cd into the main folder and run
```
./autorun
```or
```
sh autorun
```
That will start the server on the default port of 4000. You then need to telnet to 127.0.0.1 on that port to connect in another window or with a mud client. The first log-in will be designated as the implementor. If you run into any other tbaMUD specific issues, I'd recommend their forums. The community there is great and ready to help for any platform.

---

