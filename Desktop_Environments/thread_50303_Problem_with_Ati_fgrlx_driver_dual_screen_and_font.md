---
title: "Problem with Ati fgrlx driver dual screen and font sizes"
date: 2005-07-19
forum: Desktop Environments
---

### Post by ghoshe on 2005-07-19
As the title says, i have that curious problem with my Kubuntu:

I have two monitors attached to my radeon 9550, i could have a dual screen desktop (via fgrlxconfig coping the driver configuration to my xorg.conf file), this was easy to do, but the only way to have a correct font size of some programs, like amsn or firefox (is this because i'm worried) is to make a "console login" otherwise, making a standard login the font size on firefox is very small, on the other hand amsn font size is enormous.
I though that was a problem with kdm, that was starting before other critical process in relation to font server or something, but i couldn't fix it. ](*,) 
Then tried with font server, and font type (like the problem with xmms menus with small font sizes), but i couldn't fix it too. ](*,) 

It's curious, but starting X with one monitor only configuration all the fonts are ok.
It's curious too, that if you start an X session with ati driver fonts are pretty, but if you start the session with fgrlx driver the fonts appear too "fat", i have tested this with my radeon 9550 and my laptop's 9700 Mobility Radeon.

So, i think that's a trouble with fglrx driver, maybe a driver option, i don't know.

If anyone knows how to fix this problem, PLEASE, answer me.

PD: Excuse my poor English  :roll:

---

### Post by JLTB on 2005-07-20
Hi,

This most likely has to do with the font dpi settings you are using.  Kubuntu/Ubuntu's defualt settings are tiny and/or too large for somethings.  Also if your dpi settings are not corrected for your big desktop resolution things will get skewed.

Check this tutorial and follow the dpi settings part.

[http://www.ubuntuforums.org/showthread.php?t=20976&highlight=fonts+cleartype](http://www.ubuntuforums.org/showthread.php?t=20976&highlight=fonts+cleartype)

---

