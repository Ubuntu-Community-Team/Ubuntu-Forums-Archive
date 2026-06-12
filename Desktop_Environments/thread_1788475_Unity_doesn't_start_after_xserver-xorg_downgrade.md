---
title: "Unity doesn't start after xserver-xorg downgrade"
date: 2011-06-22
forum: Desktop Environments
---

### Post by RikoW on 2011-06-22
Dear all,

since the intel graphics drivers shipped with Maverick there is a problem with running wine/CXoffice application under Ubuntu. The problem didn't exist in Lucid:

[http://ubuntuforums.org/showthread.php?t=1602422]("http://ubuntuforums.org/showthread.php?t=1602422")

So again I resolved to downgrading the xserver-xorg packages to Lucid (unfortunately I need to set priorities!). However, after doing that Unity is not starting anymore. I see notifications (for example when network-manager establishes a connection) but nothing else - blank desktop.

Ubuntu Classic with Compiz effects enabled however works just great. Is that a "known" incompatibility or is there a chance to fix it?

Thanks and cheers,
          Riko

---

### Post by RikoW on 2011-07-02
OK, after hours of playing with it and trying to get Unity back to work, I'm ready to give up! Too bad, because I really would like to get to know it better - keep an open mind, you know :)

Anyway, I tried all hints to get the panel and the launcher back, including following all advises here:

[http://ubuntu4beginners.blogspot.com/2011/04/missing-top-and-side-panels-in-unity.html]("http://ubuntu4beginners.blogspot.com/2011/04/missing-top-and-side-panels-in-unity.html")

I also created a new account and tried to login (just in case the unity profile in Compiz is somehow screwed for my account), but with the some effect: empty desktop - no panel, no launchers.

From the mentioned test, I don't see that the down-grade should have effected the possibility to run Unity (see attached UnityTest.txt). Compiz with effects in Classic gnome runs great.

Maybe somebody can make any sense from the .xsession-errors file I attached as well. You guys are my last hope! :)

Thanks for listening and cheers,

                  Riko

---

### Post by RikoW on 2011-07-05
Indeed it seems some incompatibility with the xorg-xserver packages. I re-installed the default natty packages again and now Unity starts again without further action.

We see how long it takes until those black areas start to annoy me too much :)

Cheers,

             Riko

---

