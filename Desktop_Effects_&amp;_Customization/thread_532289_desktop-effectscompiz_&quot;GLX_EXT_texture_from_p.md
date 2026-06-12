---
title: "desktop-effects/compiz &quot;GLX_EXT_texture_from_pixmap is missing&quot;"
date: 2007-08-22
forum: Desktop Effects &amp; Customization
---

### Post by KilianValkhof on 2007-08-22
Today i tried to "update"  from trevino's repositories to the GIT version of compiz fusion, first using the script provided here, and when that wasn't successful, following the tutorial on the compiz-fusion forum. Which didn't work out either. I uninstalled it all, and tried to install from trevino's repositories again. only, now both the command "compiz --replace"  and "desktop-effects" (the "basic" compiz in ubuntu 7.04) give me this error:
```

compiz (core) - Fatal: GLX_EXT_texture_from_pixmap is missing
compiz (core) - Error: Failed to manage screen: 0
compiz (core) - Fatal: No manageable screens found on display :0.0

```
with "desktop-effects" giving this:
```

nvidia hardware not available
compiz (core) - Fatal: GLX_EXT_texture_from_pixmap is missing
compiz (core) - Error: Failed to manage screen: 0
compiz (core) - Fatal: No manageable screens found on display :0.0

```

i've spent the entire afternoon searching these and the compiz-fusion forums, and found absolutely nothing (except a solution suggesting that i remove all the apps and files relating to compiz, which I did.)

i am running a fujitsu p7230 laptop with intel 945 integrated graphics with the 915resolution patch, running ubuntu 7.04.

Any help would be greatly appreciated :)

---

### Post by zero244 on 2007-08-22
Its been my experience that if you get the texture_from_pixmap failed error. Your best choice is to run Compiz with XGL if you want decent performance and stability.
There are How tos to install and run XGL.
Getting that error could indicate a defective video chip.
I personally had trouble using the restricted drivers that come with Feisty.
I used the Automatix2 drivers, which I think are pretty close to the same.
The Automatix drivers worked and the Feisty drivers didnt.
Now once you install the Feisty drivers you may have a problem installing the Automatix drivers.
If your sure your video card is ok.....its just a matter of getting the right drivers installed correctly.
To do that sometimes results in having to do a fresh install.
Good Luck.

---

### Post by KilianValkhof on 2007-08-22
Thank you, I was already fearing for a fresh install, but i'm keeping it till a last resort. on the compiz-fusion forums there might be some people with similar problems :)
(i also might add that up until this morning, compiz was running happily and without problems using trevino's repo)

---

### Post by jordanmthomas on 2007-08-23
It appears something has broken in compiz since yesterday or so.
I just reinstalled arch and was putting all the goodies back on, but compiz-git doesn't work for me either.  Just yesterday it was, so I would guess this is something that will be taken care of soon.  

I'm using i915, so our graphics are similar and we use the same driver.  (By the way, there's no proprietary drivers for intel cards, so don't worry about restricted drivers or anything like that)


**edit**  I have been searching around looking for a solution and almost everything I am finding is from the last couple of days, so this does appear to be a new development.

---

### Post by jordanmthomas on 2007-08-23
I've been looking around and I'm guessing that if you didn't already have some settings before the 19th, you're screwed for a while.

According to [this]("http://smspillaz.wordpress.com/2007/08/19/compiz-fusion-community-news-edition-12-for-august-19-2007-radical-changes/#comments") blog, you shouldn't update compiz-core for a while.  :(

---

### Post by KilianValkhof on 2007-08-23
i'm just going to do a fresh install and use amarath's repo, it seems, for now, the fastest and easiest solution :) thank you!

---

### Post by jordanmthomas on 2007-08-24
Well, I am glad you got a solution.  It won't work for me since I don't even use Ubuntu, so I had to find another one.

Luckily, the Gentoo wiki rescued me (yet again...probably one of the most helpful sites out there)

[http://gentoo-wiki.com/HOWTO_XGL/Troubleshooting#GLX_EXT_texture_from_pixmap_is_missing](http://gentoo-wiki.com/HOWTO_XGL/Troubleshooting#GLX_EXT_texture_from_pixmap_is_missing)
basically, all I had to do to get it working again was add:
```
LD_LIBRARY_PATH=/usr/lib
```
to my /etc/profile, log out and back in, and bingo...back in business.

I think what happened was somehow compiz was looking in the wrong places for the mesa libraries it needed.  I really missed compiz but I was kind of getting used to openbox.  :guitar:

Anyway, just thought I'd post this in case someone else comes by with this problem.

---

