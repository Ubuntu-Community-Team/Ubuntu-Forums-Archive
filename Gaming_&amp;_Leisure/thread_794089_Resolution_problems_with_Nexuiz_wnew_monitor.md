---
title: "Resolution problems with Nexuiz w/new monitor"
date: 2008-05-14
forum: Gaming &amp; Leisure
---

### Post by timzak on 2008-05-14
Just got a new widescreen monitor (1440x900).  Previously I was running a CRT @ 1280x960.  When I fired up Nexuiz, I had a couple of problems:

1) there's a banner floating around the screen telling me to upgrade Nexuiz to the latest version.  I'd rather only update through the repositories, so how do I get rid of this?

2) the game seems to have problems with 1440x900 and it won't let me change resolutions to any other.  

I'm currently in a state that when Nexuiz loads, I see three sections (setup, single-player, multiplayer) and I can't access any of them.  I'm not sure if this is related to the resolution issues, or if somehow the game has locked me out until I upgrade to the latest version.  Is Nexuiz going commercial?  This seems like one of those shareware limited-play things, but I could be wrong.

Any help appreciated.

Thanks.

---

### Post by Perfect Storm on 2008-05-14
1) I dunno how you get rid of the banner, but I have a guide on how to install the latest.
[http://gaming.gwos.org/doku.php/guides:64bit:nexuiz](http://gaming.gwos.org/doku.php/guides:64bit:nexuiz) works also for 32-bit. It's simply unzip the package and the launcher from your home directory. The guide just put it in a covnient place and set up a launcher with icons etc.
If you choose, it might be a good idea to uninstall the previous version first.

2)
```
gedit ~/.nexuiz/data/config.cfg
```

at the buttom there's something called;
vid_height "XXXX"
vid_width "XXXX"

---

### Post by disturbedite on 2008-05-14
you didn't mention which version of nexuiz you're using.  you might try to update to the new version  (2.4.2) if you're not using it already.

---

### Post by timzak on 2008-05-14
> **disturbedite said:**
> you didn't mention which version of nexuiz you're using.  you might try to update to the new version  (2.4.2) if you're not using it already.

I'm using the latest version in the Hardy repositories (I installed from Synaptic).  I prefer to install only from repositories, to automate updates, etc.

Does the floating upgrade banner make the game unplayable until you update to latest version?

---

### Post by Perfect Storm on 2008-05-14
Well, I guess if you want to play against other people on the net, you need the latest. You do know that Nexuiz in the repo will get updated first in the next release of Ubuntu?

---

### Post by timzak on 2008-05-14
> **Artificial Intelligence said:**
> Well, I guess if you want to play against other people on the net, you need the latest. You do know that Nexuiz in the repo will get updated first in the next release of Ubuntu?

Hmmm...didn't realize that.  I thought that updated versions of Nexuiz get submitted to Ubuntu developers for testing, then eventually become available in repositories and shoot out via Update Manager.  If that's not the case, then what is the point of having Nexuiz in the repositories at all if the version there is unplayable?

---

### Post by Perfect Storm on 2008-05-14
I don't know if it's unplayable, but my thought is that everyone have updated theirs Nexuiz plus servers, it might be pointless using a version noone else uses.


But if no releases are made the one in the repo will be fine for the purpose. You can also wait untill getdeb make a .deb package - but I don't know how long it will take.

---

### Post by disturbedite on 2008-05-15
> **timzak said:**
> Hmmm...didn't realize that.  I thought that updated versions of Nexuiz get submitted to Ubuntu developers for testing, then eventually become available in repositories and shoot out via Update Manager.  If that's not the case, then what is the point of having Nexuiz in the repositories at all if the version there is unplayable?
no, that isn't the way it works.  it may only get updated if there is a security issue or a backport or something like that, unless you're testing a pre-release.  (intrepid in this case).
fyi, the latest version in repo is 2.4 for intrepid, i didn't look at what the other versions of ubuntu have.
2.4 works fine for me.

---

### Post by timzak on 2008-05-15
Okay, I got the resolution problem fixed, which was the main problem.  When I set the game to my monitor's native resolution (1440x900) the game opens in a full-screen window (it's full screen, but I see my desktop panels above and below).  This prevents me from using the in-game mouse cursor, which keeps me from navigating in the game.  My solution was to set the resolution to *any resolution BUT 1440x900*.  Why this works, I don't know.  But when I select any other resolution, the game magically works in 1440x900 full-screen.  

Since I am having a similar problem in other 3D games (Planet Penguin Racer, TORCS), I think this is related to the new version of Xorg that comes with Hardy.  Just a guess, I could be wrong.  I'm guessing this because everything worked in Gutsy fine, and my hardware hasn't changed at all.

So now that I can access all the in-game menus, I can see that the upgrade banner does not impede me from playing the game.  I just couldn't tell what was going on without being able to navigate the game menus--I thought maybe the game wasn't letting me do anything until I upgraded, but it turned out to be video-related instead.

And FYI, the version in Hardy's repositories is 2.4.1 and the latest version is 2.4.2.

Thanks for the feedback, guys.

---

### Post by disturbedite on 2008-05-15
no, its 2.4-1 NOT 2.4.1 just like intrepid.

---

