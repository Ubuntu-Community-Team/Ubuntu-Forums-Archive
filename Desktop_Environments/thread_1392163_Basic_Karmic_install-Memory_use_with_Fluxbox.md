---
title: "Basic Karmic install-Memory use with Fluxbox?"
date: 2010-01-27
forum: Desktop Environments
---

### Post by GeneralSpecific on 2010-01-27
Does anyone have a basic **Ubuntu Karmic** install that they are using **Fluxbox** with?

**[COLOR="Blue"]Could you post the results of "top" or "htop"?[/COLOR]**

I am currently running a _command line Ubuntu install_ built up with Fluxbox and 'nautilus --no-desktop", and I would like to compare how much memory I have saved compared to a full Ubuntu install using Fluxbox.  Plus a comparison of some of the services that run in the background.

Currently I am only using about 40MB RAM with no programs other than "htop" running.  I'll gladly post mine if anyone is interested.

Thank You

-Ryan

---

### Post by Rodney9 on 2010-01-27
I love Fluxbox for its minimalist simplicity.

$ top

top - 12:18:14 up 28 min,  2 users,  load average: 0.02, 0.11, 0.07
Tasks: 128 total,   1 running, 127 sleeping,   0 stopped,   0 zombie
Cpu(s):  1.0%us,  0.7%sy,  0.0%ni, 98.4%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   8194608k total,   961476k used,  7233132k free,   124276k buffers
Swap:  6385796k total,        0k used,  6385796k free,   368116k cached

Htop

---

### Post by GeneralSpecific on 2010-01-27
Thank you for your quick response!

Here is my "htop"

As you can see I am striving to run Ubuntu on a **low RAM machine - 256MB**.  I know that new ram is cheap, but it is sort of a personal challenge to see how fast I can get it to run the way it is.

Anyone else?  Especially with _as few other programs running as possible_ - so I can get an idea of the minimum memory used running Ubuntu w/ Fluxbox.

Thanks

-Ryan

---

### Post by Rodney9 on 2010-01-27
I worked out how to take  a section screen shot with scrot, so here is my htop again -

---

### Post by GeneralSpecific on 2010-01-28
Thanks!

WOW...what a contrast:

[B][COLOR="Blue"]Memory[/COLOR]
48/256
450/8000[/B]

Is that a _basic_ Ubuntu install (using fluxbox of course) or do you have a lot of other things running?

It may be hard to compare, when you have a lot more RAM than I do.  
I seem to remember reading that the more memory you have available the more memory will be used - Your computer doesn't need to conserve ;)

-Ryan

---

### Post by snek on 2010-01-28
Wouldn't it be better to paste the output of *free -m* instead of (h)top?
Quite a difference though, curious what other people post..

---

### Post by GeneralSpecific on 2010-01-28
*free -m*  could work fine...

I am a fan of *htop*, and a little curious about some of the_ top processes_ that are taking up memory.

Thanks for the reply, I hope we can get a few more full screen shots of htop.

-Ryan

---

### Post by Rodney9 on 2010-01-28
$ free -m
             total       used       free     shared    buffers     cached
Mem:          8002        540       7461          0         68        171
-/+ buffers/cache:        301       7701
Swap:         6236          0       6236

---

