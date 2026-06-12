---
title: "i need help getting compiz installed...."
date: 2007-11-13
forum: Desktop Environments
---

### Post by baphomet420 on 2007-11-13
OK...
I have been trying to get beryl (now compiz) to run since new years on 4 different distros...  never have successful gotten a 3d desktop to load...

I have
3.2 g P4 w/ 2 gig ram
on board 256 shared VIA video (is this my problem)???

I just loaded ubuntu studio7.10 3 days ago, I have been sleeplessly trying to get compiz running since...  from what I read, I should be straight on requirement???

right now when I try to enable desktop effects, I get an "desktop effects could not be loaded" error box...

this is what I have tried so far...
first I download the compiz config setting manager... 
then I went to synaptic manager and got everything that had compix in the title...

At this point I could open the settings and change them, but I couldn't load the effects...

I have since then tried installing from multiple repositories...  usually with no luck on even completing the installations...

I even tried actual compiz fusion, and tried their ubuntu install scripts...  Im still without 3d desktop???

anybody have any suggestions???  im totally lost...

---

### Post by rundee_f on 2007-11-14
follow this link brother..

[http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion](http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion)

---

### Post by baphomet420 on 2007-11-14
> **rundee_f said:**
> follow this link brother..

[http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion](http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion)

that site would be awesome if i could get compiz to load...
however I can't...  Thats the problem...

Im not needing help navigating, I'm needing help running...l

---

### Post by baphomet420 on 2007-11-16
bump.........

---

### Post by PeterJS on 2007-11-16
Ok, well lets see if we can put to rest any questions about graphics card drivers. Run:
```

glxinfo | grep direct

```
To see if direct rendering is set up. Let us know what that outputs and we'll see where to go from there.

---

### Post by baphomet420 on 2007-11-16
no rendering :(

now I know :)

thanks for the help...    

does anybody know if compiz keeps a list of cards that are sure to work???

> 
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: Mesa GLX Indirect


---

