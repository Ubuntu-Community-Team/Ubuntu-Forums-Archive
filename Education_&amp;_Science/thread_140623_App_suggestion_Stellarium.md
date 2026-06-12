---
title: "App suggestion: Stellarium"
date: 2006-03-06
forum: Education &amp; Science
---

### Post by angkor on 2006-03-06
For those who are interested in astronomy / astrology, check out [COLOR=Blue][Stellarium]("http://www.stellarium.org/")[/COLOR]

Stellarium is a wonderful GPL cross platform app which renders realistic skies in real time with openGL.

I like it a lot so I thought I'd share it with those who haven't heard of it yet. 

It's in the universe repos btw:

sudo apt-get install stellarium.

Grtz,

Angkor

---

### Post by Ahriman on 2006-03-06
Nice. I've played around a bit with Celestia, but I'll give this a go.

Astronomy has been a hobby of mine since I learnt that the lights in the sky at night weren't alien invaders or fireflies, like my brother said ...

---

### Post by angkor on 2006-03-06
Cool, didn't know about Celestia, thanks! 

And it's also in the repos...I keep on being amazed how much free software there is in there...:)

---

### Post by quietglow on 2006-03-06
This has to be one of the nicest software packages I've looked at recently...thank you so much for pointing it out. These developers deserve some serious $ I think...did you see that one of them has a business selling planetariums? So cool...

Edit: OMG I just opened the program on my 1900x1200 23" Cinema Display and it was literally breathtaking...this is one incredible piece of work

---

### Post by LKRaider on 2006-03-07
I have problems running it. The text is all weird (like using a symbols font).

---

### Post by angkor on 2006-03-07
[QUOTE=quietglow]Edit: OMG I just opened the program on my 1900x1200 23" Cinema Display and it was literally breathtaking...this is one incredible piece of work[/QUOTE]

Ooo, that must be like having an extra window in your room! :) I'm jealous....I'm gonna get me a screen like that some day.

[QUOTE=LKRaider]I have problems running it. The text is all weird (like using a symbols font).[/QUOTE]

Any error messages when you start it from the terminal?

---

### Post by Sirin on 2006-03-07
[QUOTE=angkor]Ooo, that must be like having an extra window in your room! :) I'm jealous....I'm gonna get me a screen like that some day.
[/QUOTE]

If you think the 23" is nice, take a look at the 30" HD!

LEFT: 23" ; RIGHT: 30"

[IMG]http://images.apple.com/displays/images/indexcompdisplay06282004-02.jpg[/IMG][img]http://images.apple.com/displays/images/indexcompdisplay06282004-03.jpg[/img]

---

### Post by angkor on 2006-03-07
:shock: 

Man! And I thought 19" was quite large...

I'd probably hurt my neck playing frozen bubble on the 30" one though....;)

---

### Post by quietglow on 2006-03-07
> I'd probably hurt my neck playing frozen bubble on the 30" one though..

LOL!

Seriously, the next time I'm at compusa, I'm going to install this on their test machine with the 30" CD. You really have to turn your head from side to side when using that thing while sitting right in front of it. I imagine Stellarium on it would be incredible.

And yeah, it really is like a window. The effect in a dark room is so dang amazing. It also got me outside to do some stargazing last night for the first time in a couple of years: seeing the conjunction of the moon, saturn and mars (well almost conjunction)  was super neat.

Nice, nice software. We need to somehow come up with a way in which gems like this get some publicity.

---

### Post by LKRaider on 2006-03-08
[QUOTE=angkor]Any error messages when you start it from the terminal?[/QUOTE]

This is what it spits out:
```
lkraider@ubuntu:~$ stellarium

    -----------------------------------------
    | ## ### ### #   #   ### ###  #  # # # #|
    | #   #  ##  #   #   ### ##   #  # # ###|
    |##   #  ### ### ### # # # #  #  ### # #|
    |                       Stellarium 0.7.1|
    -----------------------------------------

Copyright (C) 2000-2005 Fabien Chereau et al.

Please check last version and send bug report & comments
on stellarium web page : http://www.stellarium.org

Loading configuration file /home/lkraider/.stellarium/config.ini ...
Locale is pt_BR.UTF-8
Loading location: "Paris", (landscape is: "guereins")
Loading Hipparcos star data (118218 stars loaded).
Loading nebulas data (73 deep space objects)...
Loading Solar System data...
Error opening /usr/share/stellarium/data/cardinals.por.fab
Using international star names.
Loading configuration file /home/lkraider/.stellarium/config.ini ...
Looking for startup script to run.
Script completed.
lkraider@ubuntu:~$

```

I have posted a bug-report @ [https://launchpad.net/distros/ubuntu/+source/stellarium/+bug/33988](https://launchpad.net/distros/ubuntu/+source/stellarium/+bug/33988) where you can see the screenshots of the problem.

Maybe it is my locale setting which is trashing the glyph display ?
Or maybe is because I'm running XGL?

---

### Post by angkor on 2006-03-08
I haven't tried it with xgl yet, I'll check later tonight and let you know if I experience the same.

---

### Post by angkor on 2006-03-08
Hm, doesn't even load for me with XGL enabled....I get to look at the splash screen for ages. 

It probably has something to do with xgl, could be something in the new dapper version though.

Edit: It does run without xgl but I get the same problem you have with unreadable text and strange symbols.

---

### Post by LKRaider on 2006-03-13
Could you confirm the bug at launchpad then? Whoever is supposed to take care of this package has given no attention as of yet : (

[https://launchpad.net/distros/ubuntu/+source/stellarium/+bug/33988](https://launchpad.net/distros/ubuntu/+source/stellarium/+bug/33988)

---

### Post by pisuke on 2006-10-26
problem solved.

---

### Post by BLTicklemonster on 2007-10-28
Problem solved? I got a pm from someone using xgl, and stellarium crashes when launched.

---

### Post by NoVista on 2007-10-28
Tried it on my setup and yup, three times booted me right out of the OS and the machine was logging out. On the  final time, it really messed something up, because even though I could boot back to the OS, I had   a black screen. (Not the usual ATI problem black screen). I think either compiz or even more so xgl was the culprit.

I would try running it again from terminal to get an output, but ssince it totally trashed my system, I don't dare. I spent an hour trying to get the OS back, and couldn't. Good thing I had an image file of my partition so I was able to get back to normal.

Dang, looks like a very sweet program.

And no, turning off XGL really isn't an option, as the latest ATI 8.42 drivers aren't mature enough to run without XGL.

---

### Post by BLTicklemonster on 2007-10-28
Dang. Have you tried using kstars? No where near as cool, but functional.

---

### Post by NoVista on 2007-10-28
No, I haven't. Thanks for the tip and I'll install it.
It better be XGL/Fusion friendly.

---

### Post by BLTicklemonster on 2007-10-28
I heard that!

just open a terminal, and type

sudo aptitude install kstars

---

### Post by NoVista on 2008-01-17
Well, well, well.

I just realized that it is not XGL being responsible for not letting me run Stellarium.
It's compiz-fusion. If I turn off CP, I can run Stellarium, and oh wow I can finally see what an absolutely great program this is! I wish I had all this when I was 12 years old.

---

### Post by gsss124 on 2008-04-04
Hi, 
I was having a similar startup crash (segmentation-core dump) problem, have no xgl and but compiz is there.
Found this while searching for a solution:
[https://bugs.launchpad.net/ubuntu/+source/stellarium/+bug/68724](https://bugs.launchpad.net/ubuntu/+source/stellarium/+bug/68724)

It says in the last posts by t3rmin4t0r:
Quick workaround:

bash$ LANG=C stellarium

But, Compz stops running on my system. 
But also, Stellarium is a wonderful program:). Hope this helps someone.

PS Is there any other non bash solution that keeps compiz running?

---

### Post by goggins on 2008-05-11
Stelarium looks like it might be really good, but the configuration panel is driving me crazy.  How do you select a location and make it stick?

---

