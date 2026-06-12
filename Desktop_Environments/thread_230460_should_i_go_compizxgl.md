---
title: "should i go compiz/xgl?"
date: 2006-08-06
forum: Desktop Environments
---

### Post by Mooie on 2006-08-06
Hi, I have been a very happy Ubuntu user since the day after dapper came out.  After a week or two I switched to Kubuntu 6.06 dapper amd64, which was really nice.  The only thing I like more than my eyecandy is gaming.  Using xgl/compiz looks like it IS the future of the linux gui, though through what I have read it needs quite a bit more work. I saw a video of it (in gnome) and it looked fantastic, though I have never seen it in kde (does it even work in kde, and w/ a 64-bit os).

can I get my games (native and through cedega) to work with xgl (if you know of any good howto posts could you please link them)? will I take a huge preformance hit?

I have a pretty nice system:  amd64 4200+ x2,  nvidia xfx 7900gt (256mb vid ram),  2.5gigs of dual channel ddr ram

any help/info would be greatly appreciated, and thank you for your time :D 
(I hope i posted this in the right section btw)

---

### Post by Mooie on 2006-08-06
i have read a few articals, and it looks like there are many ways to play games w/ xgl active, some dont look like they would work w/ cedega, and some of the ones that do might not be able to get steam to work because cedega launhes a window that launches the game.

I dont mind doing a little bit of work to get my games to play, as long as they all work...

thanks for the help :D

---

### Post by Shay Stephens on 2006-08-06
I just installed xgl/compiz yesterday.  It is awesome for sure.  I do notice a slow down in UT2004 as well as a graphics change in the look of the game since installing xgl (both for the worst).  So my thinking is I need to find a way to turn off xgl before playing the game or any openGL type application.  I have not researched any of that yet.

---

### Post by _simon_ on 2006-08-06
To play games under XGL:

[http://www.ubuntuforums.org/showthread.php?t=176636&highlight=XGl+opengl+games](http://www.ubuntuforums.org/showthread.php?t=176636&highlight=XGl+opengl+games)

This method does work, I use it all the time. It also works with cedega games.

---

### Post by Shay Stephens on 2006-08-06
Thank you so much for the link.  That did indeed fix it.  Now I have my cake, and I am eating it with abandon :-D

Thanks a bunch!!!

---

### Post by Mooie on 2006-08-06
cool, thanks for the info, I will look into it and probably install xgl and compiz, I found a nice looking howto on setting it up with kde.

---

### Post by Mooie on 2006-08-06
also, could you please post your system specs and the fps before and after you installed xgl/compiz? thanks :D

---

### Post by peabody on 2006-08-07
To my knowledge, you can always bypass xgl by launching something from the shell with DISPLAY=:0 set in the enviroment.  This bypasses the xgl server and goes directly to the X server.  I use it to watch video in xgl with mplayer.

You can kind of think of xgl as one big window that runs in the X server.  Instead of apps displaying directly to the X server, they display to the xgl server which then displays it in its window with all the eyecandy.  This is why it looks like hardware acceleration isn't turned on while you're inside xgl (even though it really is).  This can by illustrated by launching a gnome-terminal with DISPLAY=:0.  Then launch metacity from that new terminal.  A giant window gets drawn around the xgl desktop.  You can then move the xgl desktop around.

---

### Post by orb9220 on 2006-08-07
XGL Install and General Tips For Gnome and Nvidia 
[http://www.ubuntuforums.org/showthread.php?t=131267](http://www.ubuntuforums.org/showthread.php?t=131267)

---

### Post by Mooie on 2006-08-07
awesome, I will try it out soon.  Thanks for the information and links :D

---

### Post by hotani on 2006-08-07
At the risk of raining on someone's parade... I would recommend against using XGL/Compiz under any circumstances. Here's why: It might work when you first set it up, but then something will not be the way you want it. So you'll attempt to "fix" this. Then you'll find that there is no easy way to "fix" anything in compiz. After a couple of hours of scouring the forums, you'll find some obscure CLI solution to your problem as another one pops up in its place. 

I have had compiz running quite happily for maybe 2 or 3 days before something would randomly change without asking me, or maybe it would just stop working completely. I finally found the best solution to the headaches, which was: "metacity --replace"

Compiz is cool, the "future of..." blah, blah and all that good stuff. But in the end, at this point in time, it is a swirling torrent of pain that should be avoided. Unless you're into that sort of thing. Now that I'm not spending 3 or more hours a day farting around with Compiz, I'm getting an insane amount of work done! It's amazing! :D

Oh yeah, and it was pretty cranky about MythTV. When running mythfrontend, the gnome menu bars were still visible. For a while I attempted to get a script to work that would kill compiz and start metacity before running Myth but it never really worked very well. In the end, once again, the best solution was to just not use Compiz.

---

### Post by bulldog on 2006-08-07
Sorry to hear that Xgl/Compiz didn't workout for you.
I have it running for about 2 months now and didn't experience any trouble at all.
I use the cgwd and the cgwd_themes to and it works like a charm.
Maybe you should try another script?
I use the python.py script and changed it to work with cgwd and the themes.

---

### Post by Mooie on 2006-08-07
hmmm...    I guess I should wait a bit before I try to set it up.  It does seem like it is (or should) still be in testing, and w/ myself being a (big) gamer, it might be wisest to wait untill it has more features and has been stabled out a bit.  thanks for your warning.

---

