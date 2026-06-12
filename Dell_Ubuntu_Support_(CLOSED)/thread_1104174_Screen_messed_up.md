---
title: "Screen messed up"
date: 2009-03-23
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Wezel on 2009-03-23
Hey all,

I'm new to the ubuntu community. I've been using Ubuntu now for 2 days and I'm totally crazy about it !

Although, I have an issue that keeps me from enjoying this fine OS... At some random moments, my screen just flips out and I can't do anything anymore. The system doesn't hang, it still runs, but I can't see anything.

I've looked around here in the forum posts, and I've found [http://linux.dell.com/wiki/index.php/Ubuntu_8.10/Issues/No_Hybrid_graphics](http://linux.dell.com/wiki/index.php/Ubuntu_8.10/Issues/No_Hybrid_graphics) although it doesn't really conform with my problem....

Details:
[LIST]
[*]System
 Dell XPS m1710 (graphic card 7900GTX)
[*]OS
 Ubuntu (latest version, no idea how to see the actual version for I am new to linux)
[*]Problem
 Screen flips out on random moments. I have to reboot to get anything decent on my screen again. Flips out means it just displays grey colors and stuff, sort of like totally distorted.
[/LIST]

I have had this problem on XP loooong ago, but just a few times. In the very short time I've had Ubuntu now I've had it at least 3 times.

Does anyone have any idea on what to do to resolve this problem ? If you need any more details please let me know. I really look forward working with Ubuntu, without this annoying problem :-)

---

### Post by Wezel on 2009-03-23
It seems to be a Dell issue for I've found more people struggling with the same problem.

Although I find it strange that it appears this frequent now since I installed Ubuntu, maybe the drivers trigger something that windows didn't ?

No idea,

Wesley

---

### Post by sansor on 2009-03-24
you might try 
```
sudo dpkg-reconfigure xserver-xorg

```
I had some issues with the display and this solved the problem.

---

### Post by Wezel on 2009-03-29
Thanks for replying,

Tried it but it doesn't work.
I have googled it and it seems to be an issue with a graphics chip on this model. The weird thing is that it just started doing it this frequently on linux.

Well, I'll try dell support for now

---

### Post by armandh on 2009-03-29
try purging compiz 
it may be too much for the graphics card or chip

I have used it on a blacked screened Gateway and everything else worked thereafter.

---

