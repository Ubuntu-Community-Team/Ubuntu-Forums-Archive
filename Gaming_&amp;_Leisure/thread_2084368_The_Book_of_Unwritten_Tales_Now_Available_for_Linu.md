---
title: "The Book of Unwritten Tales Now Available for Linux"
date: 2012-11-15
forum: Gaming &amp; Leisure
---

### Post by newbie2 on 2012-11-15
> Nordic Games has released The Book of Unwritten Tales as a Linux title, now available for download via Steam Linux Beta. A recipient of countless awards and highly acclaimed by fans and critics alike, The Book of Unwritten Tales enables the Linux gaming community to fully immerse itself in Tux’s version of Aventásia.
Linux is definitely a great opportunity to make our games available to a broader audience and we are pleased to say that The Book of Unwritten Tales is simply the first of them to be developed for the Linux platform,” said Reinhard Pollice, Business and Product Development at Nordic Games.
[IMG]http://electronictheatre.co.uk/images/thebookofunwrittentales/thebook_ofunwritten_tales_2.JPG[/IMG]
[http://electronictheatre.co.uk/pc/pc-news/27096/book-unwritten-tales-linux](http://electronictheatre.co.uk/pc/pc-news/27096/book-unwritten-tales-linux)
:popcorn:

---

### Post by Carborundum on 2012-11-15
I own it on Steam. It runs perfectly under Ubuntu 12.10 64-bit, on Ivybridge Mobile graphics. I can definitely recommend it to fans of the point-and-click adventure genre.

---

### Post by weasel fierce on 2012-11-17
Thanks for the recommendation. It's truly a golden age for Linux gaming

---

### Post by offgridguy on 2012-11-17
Thank you from here as well.

---

### Post by oldrocker99 on 2012-11-22
I purchased TBoUT today, and got segmentation faults. I edited the .sh file as recommended on the game forums, and copied some .so files to a hidden ~/.lib directory (also recommended). Now the game keeps asking if I want to install ialibs32 (of course it's installed, but Steam does install dependencies for every Windows game it installs, so I'd expect something similar for a Steam Linux install) over and over again and exits](*,).

Grrrr.

---

### Post by Shannon_VanWagner on 2012-12-06
@gdbGamer over at the steam forums provides a workaround... Works for me!

> **gdbGamer said:**
> Here is my workaround for Ubuntu 12.10 on x86-64:

```

Step 1: Change directory to The Book of Unwritten Tales
$ cd ~/Steam/SteamApps/common/The\ Book\ of\ Unwritten\ Tales/

Step 2: Start the game in gdb
$ LD_LIBRARY_PATH=./lib/32/ gdb ./bin/32/kAGE

Step 3: Set a break point in the problematic function that will jump over the bad code
(gdb) break Ogre::GLXGLSupport::refreshConfig if !($eip = $eip + 1056)

Step 4: Confirm that you will set the break point on a pending symbol
Make breakpoint pending on future shared library load? (y or [n]) y

Step 5: Run the game
(gdb) run

```

This workaround is super fragile and will likely break if and when KING Art updates libOgre. 

Note: You might want to keep an eye on the [thread (link here)]("http://steamcommunity.com/app/221410/discussions/0/882966057043010094/#c846938351123449442") in case they make changes...

Right on @gdbGamer!

---

### Post by oldrocker99 on 2012-12-06
Shannon, THANK YOU! I hadn't seen the solution before you posted it, but I've been able to play the game now; in fact, I played it until the Getting The Bag Of Gold screen (with the showman/fortune teller) for hours today.

It's kind of a rigamarole to get the game running, but...it runs!

You get a GOLD STAR for this post!

---

### Post by Shannon_VanWagner on 2012-12-07
@oldrocker99 - No problem at all. I was searching for the answer to the problem myself and I found this post. So I figured since you took the time to put the issue out there to begin with - I could at least share what worked for me. Glad it helped!

Actually, there might be an even easier fix than the work around. Try this simple fix instead:

**Uncheck - Steam>Settings>IN-GAME>Enable Steam Community In-Game**

Then try to start the game again. Works for me. Someone had mentioned it at the link I posted previously.

Hope you have a great holiday season! Cheers!

---

### Post by oldrocker99 on 2012-12-07
Yers, disabling Steam Community did the trick! 

This is a most amusing game, and frustrating as well (winning the money). I'm eagerly awaiting for Steam to put out more; the other Source Engine games are hopefully first on the list. I, myself, am holding out for Skyrim.

---

### Post by rudeboyskunk on 2012-12-07
> **Shannon_VanWagner said:**
>  **Uncheck - Steam>Settings>IN-GAME>Enable Steam Community In-Game** 

This worked perfectly!  But like most people, it crashed when entering "Settings." :(

---

### Post by oldrocker99 on 2012-12-08
Yeah, I'm not touching "settings" until after an update, either. Aside from that rather glaring bug, the game runs perfectly. And a fine little game it is, too.

---

### Post by rudeboyskunk on 2012-12-08
I'm still stuck in the first level and can't figure out how to open the crate with the robot inside...  Any hints?

---

### Post by oldrocker99 on 2012-12-09
> **rudeboyskunk said:**
> I'm still stuck in the first level and can't figure out how to open the crate with the robot inside...  Any hints?

Keep looking and mousing around. Objects you need to interact with or look at will show when the mouse is over them. There is a crowbar on the bar counter.

There are several walkthroughs for this game, which may help to alleviate frustration. Try GameFAQs.com for nearly any game, on any platform, even (I just checked) Amiga!

---

### Post by Davsdu on 2013-01-21
Nice! Love the old point-and-click adventures so might give this one a try. :)

---

