---
title: "OpenArena on Acer Aspire One 751?"
date: 2009-09-06
forum: Gaming &amp; Leisure
---

### Post by ginsong on 2009-09-06
Hi guys, first time poster here.

Well, basically, the problem is this.

I recently bought an Aspire One netbook because of its small size and price, installed Ubuntu Jaunty on it, and while I am really happy with it for the most part, I can't seem to play any 3D games.

They load up perfectly fine, but they are slooooooooooooow.  Hello slideshow!

I understand an Intel GMA500 isn't going to run anything worth squat, but I figured OpenArena (given the extremely low minimum specs) should at least run decently with all Graphical Options turned low.  As it is now, the graphics are choppy as well as the sound.

I checked out this thread:

[http://ubuntuforums.org/showthread.php?p=7775498#post7775498](http://ubuntuforums.org/showthread.php?p=7775498#post7775498)

and followed the instructions of post #9, but that only succeeded in preventing Ubuntu from loading up, with some sort of bug and stack error.  (?)  I removed the mem=786 and it started again.

Any suggestions?  Or am I SOL?  It isn't the end of the world if I can't play OA or other 3D games (I should be doing HW anyway lol), but it would be nice.

Thanks in advance.

---

### Post by X10N on 2009-09-06
> **ginsong said:**
> Hi guys, first time poster here.

Well, basically, the problem is this.

I recently bought an Aspire One netbook because of its small size and price, installed Ubuntu Jaunty on it, and while I am really happy with it for the most part, I can't seem to play any 3D games.

They load up perfectly fine, but they are slooooooooooooow.  Hello slideshow!

I understand an Intel GMA500 isn't going to run anything worth squat, but I figured OpenArena (given the extremely low minimum specs) should at least run decently with all Graphical Options turned low.  As it is now, the graphics are choppy as well as the sound.

I checked out this thread:

[http://ubuntuforums.org/showthread.php?p=7775498#post7775498](http://ubuntuforums.org/showthread.php?p=7775498#post7775498)

and followed the instructions of post #9, but that only succeeded in preventing Ubuntu from loading up, with some sort of bug and stack error.  (?)  I removed the mem=786 and it started again.

Any suggestions?  Or am I SOL?  It isn't the end of the world if I can't play OA or other 3D games (I should be doing HW anyway lol), but it would be nice.

Thanks in advance.

I don't think Intel GMA500's are supported in Linux. There is some legal issue or something. Sorry :(

---

### Post by ginsong on 2009-09-06
Ouch.  Just like that?

I had Vista on this computer before Ubuntu, and OpenArena ran just as slow on that OS.

Ah well, at least I can play SNES games.  >_N

---

### Post by ginsong on 2009-09-07
I did a quick Google search for Linux GMA500 drivers, and I came across this site, if anybody is interested.

[http://www.happyassassin.net/2009/01/30/intel-gma-500-poulsbo-graphics-on-linux-a-precise-and-comprehensive-summary-as-to-why-youre-screwed/](http://www.happyassassin.net/2009/01/30/intel-gma-500-poulsbo-graphics-on-linux-a-precise-and-comprehensive-summary-as-to-why-youre-screwed/)

Rather concise, and rather disappointing.

::big sigh::

Again, though... OpenArena was slow as petrified batshit on Vista as well, so it may just be the fact that the GMA500 won't run anything other than Rise of the Triad on low settings.

---

### Post by zackdk on 2009-11-04
Hello Everyone!
I have Ubuntu Netbook for Acer Aspire 751!
I managed to install it properly, it also really smooth for GMA 500 poulsbo!
I know everyone at issues with it, as far as i am concern it does work properly for me, perfect resolution, and all video works better than under Win Xp...So i'm really happy!

Here is what i did, only works for ubuntu 9.10:
Open your terminal and then copy paste each of this!
DO IT ONE BY ONE, then say yes when they ask for install it without verifying, it's fine...It works for me so far... :)


wget [http://poulsbo-karmic.angelfire.com/files/poulsbo1.tar.gz](http://poulsbo-karmic.angelfire.com/files/poulsbo1.tar.gz)

tar -zxvf
poulsbo1.tar.gz

cd poulsbo1

sudo ./install.pl


At the end, just reboot!

just type reboot in the terminal, that's it, enjoy guys :)

---

### Post by jbernardo on 2009-11-05
Why are you posting Lucazade's script, renamed? The original is [here]("http://ubuntuforums.org/showpost.php?p=8182373&postcount=87"), and you have only posted two messages to the ubuntu forums, both advertising this repackaging of [Lucazade]("http://ubuntuforums.org/member.php?u=242850")'s work.

---

### Post by zackdk on 2009-11-05
Because i had lots of trouble finding the right information for acer aspire 751 and linux with no step by step explaination...i thought that could help!!!
Anyway i'm not stealling someone's work, just making easy to pass this informations....

---

