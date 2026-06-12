---
title: "GLFrontier"
date: 2009-02-02
forum: Gaming &amp; Leisure
---

### Post by Headcrash on 2009-02-02
Hi all

You'll have top forgive me as i'm a newbie to Linux, having been a slave to windows for years. I'm struggling with installing most games, but i really want to play Frontier. All the links to the game i have found are on sites forbidden by Virgin. Can anyone point me at a working link?

Thanks,

HC

---

### Post by eragon100 on 2009-02-02
> **Headcrash said:**
> Hi all

You'll have top forgive me as i'm a newbie to Linux, having been a slave to windows for years. I'm struggling with installing most games, but i really want to play Frontier. All the links to the game i have found are on sites forbidden by Virgin. Can anyone point me at a working link?

Thanks,

HC

Forbidden by Virgin????? ???? ???? Excuse me???

A provider *can NOT* block acces to websites they think are bad! :confused:

I don't know a link tough :(

---

### Post by Headcrash on 2009-02-02
A copy of the blurb when i try:

PWP - 403 Error
You are not authorized to view this page

This site is forbidden for you to see.

Note:
Do you need a copy of the original game to play it?

---

### Post by cthulhu_54 on 2010-08-04
I've played the first three versions of Elite but now I _really_ want to get my hands on this OpenGL-remake:
[http://tom.noflag.org.uk/glfrontier.html](http://tom.noflag.org.uk/glfrontier.html)
But the download link is dead! Nothing happens.

Or does anyone know what happened to the author of the code?

**EDIT:** Never mind, I restarted my FireFox and now it works! Commence download!

---

### Post by 2Karl on 2010-08-04
It's not so much a remake as a port of the Atari ST version. Does the trick, mind you :)

---

### Post by cthulhu_54 on 2010-08-04
yea, I noticed that once I got the source. 

Why-why-why isn't there an open source remake on this beautiful game?

Oolite is nice, it's very nice, but it suffers greatly from the limitations of the original game. Like only one planet in each system, (almost) no Newtonian-mechanics when flying, etc... 

Going back to that after playing Elite II or III is not feasible.

---

### Post by 2Karl on 2010-08-04
if you have a decent system, you could try X2: The Threat [http://www.tuxgames.com/details.cgi?&gameref=131](http://www.tuxgames.com/details.cgi?&gameref=131)

or X3: Reunion [http://www.tuxgames.com/details.cgi?&gameref=143](http://www.tuxgames.com/details.cgi?&gameref=143)

they're both very good games, though you may be able to find them cheaper elsewhere. Be advised that they were both released forst on Windows, so make sure if you're buying from other places that you're getting the right versions ;)

---

### Post by cthulhu_54 on 2010-08-04
Thanks.
BTW I downloaded the Privateer remake a while ago, but it complained I was lacking a lib. and when I google it it doesn't exist! (got 1 or 2 hits on Fedora RPM), so I just play the ascii-version of Privateer:
[www.asciisector.net](www.asciisector.net)
it's far superior to the original game. Well, not the graphics, but the game play certainly is.

---

### Post by 2Karl on 2010-08-04
Forgot to mention, there's free demos of both X2 and X3 here: [http://demofiles.linuxgamepublishing.com/](http://demofiles.linuxgamepublishing.com/)

---

### Post by cthulhu_54 on 2010-08-04
Yes, I noticed them (on the Linux Linux Game Publishing-site), but I don't know if my computer has the necessary hardware. It's an old laptop. :-s

---

### Post by hilz on 2011-04-20
I know this thread is old. But I've found a working link to GLfrontier here: [http://tom.noflag.org.uk/glfrontier.html](http://tom.noflag.org.uk/glfrontier.html)

However I haven't been successfully compile any of the source files. According to this thread there may be dependency issues:
[http://ubuntuforums.org/showthread.php?t=1265647&highlight=glfrontier](http://ubuntuforums.org/showthread.php?t=1265647&highlight=glfrontier)

On further investigation I was able to find the dependencies for compiling the C source file:
(gcc-3.3*)
freeglut3-dev
libsdl1.2-dev
libogg-dev
libvorbis-dev

* Ubuntu 8.04LTS needed gcc-3.3 but 10.04LTS worked with the default version.
To use gcc-3.3 I had to change the sym-link as follows:
  $ sudo su
  # rm /usr/bin/gcc
  # ln -s /usr/bin/gcc-3.3 /usr/bin/gcc

(After compiling, If you want to change gcc back to the latest version you will need to check the sym-link before doing the above)

---

### Post by weasel fierce on 2011-04-25
If all else fails, there's always playing the original Frontier Elite II in either dosbox or UAE (for the amiga version)

---

### Post by oldrocker99 on 2011-04-25
Or Oolite (in the repositories):)

---

