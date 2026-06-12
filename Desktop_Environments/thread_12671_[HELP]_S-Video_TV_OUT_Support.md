---
title: "[HELP] S-Video TV OUT Support"
date: 2005-01-26
forum: Desktop Environments
---

### Post by iCara on 2005-01-26
Hi all!!

This is my first post here, nice to meet you!

I'm pretty new to GNU/Linux and like Ubuntu very much.
One of my friends has an old pc (x86). 
His win98 crashed so i suggested him Ubuntu.

He accepted!! It is now his only O.S. ... a total switcher, congratulations!!
He's not a pc-expert, so he accepted only because i took total responsibility of what he was doing. 

I can say i learn by helping him.

Now we :) have this problem.

He has this video card "S3 Savage 86c390 3d/mv", that Ubuntu well supports with savage driver.
It has a s-video out plug and he would like to see movies on tv.

We bought the s-video cable and plugged it.

Now i started "googling", but i got lost.

I understood we have to change XF86Config-4 adding the TV as second screen, but not sure how to modify (not nano /etc/..., what to write!), and that file is so important i do not want to make a mess.

I think savage driver supports tv out (s-video), how can i make sure?

And then, in Gnome, is there a "Screen" menu to make the two screens in Twin View or we have to do it command line?

Thanks for long attention...we need smthg like a "road map".  :?

---

### Post by machiner on 2005-01-26
Search this forum - you will find your answers.

Luck and don't give up.

---

### Post by iCara on 2005-01-27
I searched again the forum (had already done it) and found something interesting.

First, TwinView is only for nvi, but is what we need to do.

We tryed S3Switch utility, from this page:

[http://www.probo.com/timr/savage40.html](http://www.probo.com/timr/savage40.html)

It says: 

Devide attached: CRT TV
Device active: CRT TV
TV System: PAL

All right!! On crt when we activate TV resolution goes smaller (seems like 800x600 or better 832xsmthg) and on TV only a grey screen, maybe refresh or dunno what problem. Changing resolution from Gnome menù causes on tv (AV channel) red or other color.

On a reboot we could see on TV a portion of Ubuntu Login (that i think uses a different video driver, or not?).

I still didn't understand if we need to add tv monitor and screen on XFConfig-4 or not. And if yes, what is the minimum required to make it work, without strange options, so we can work on it? 

I found also about Xinerama and i think it needs this editing, but maybe it is not necessary for our simple aim.

A little advice?

---

