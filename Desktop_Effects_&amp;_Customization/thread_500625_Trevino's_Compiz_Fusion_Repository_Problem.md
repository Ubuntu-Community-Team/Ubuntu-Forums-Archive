---
title: "Trevino's Compiz Fusion Repository Problem"
date: 2007-07-14
forum: Desktop Effects &amp; Customization
---

### Post by pt123 on 2007-07-14
When I installed compiz fusion I used Trevinos repository. 

[http://3v1n0.tuxfamily.org/dists/feisty/eyecandy/](http://3v1n0.tuxfamily.org/dists/feisty/eyecandy/)

Every few days there would be a bunch of new deb files in the repos. 

But the last two updates have made my compiz really sluggish. 

How do I go back/replace to the update that installed before. 

Also is there a thread in here that keeps notes on the daily builds at Treviino's so we can pass our experiences on?

---

### Post by hyperair on 2007-07-14
Looks like I'm not the only one facing this problem. While I doubt there is a clean way we can push all the packages backwards, I expect that a few updates down the road should bring some improvements. Compiz Fusion is after all a software in development and is considered unstable.

---

### Post by andrewsomething on 2007-07-14
> **pt123 said:**
> 

Also is there a thread in here that keeps notes on the daily builds at Treviino's so we can pass our experiences on?

You might want to try over at the Compiz/Fusion forums: [http://forums.opencompositing.org/](http://forums.opencompositing.org/)

This thread is about his packages, and he seems to be around frequently:
[http://forums.opencompositing.org/viewtopic.php?f=14&t=131&start=360&st=0&sk=t&sd=a](http://forums.opencompositing.org/viewtopic.php?f=14&t=131&start=360&st=0&sk=t&sd=a)

---

### Post by pt123 on 2007-07-15
Thanks for the info and damn the update today has made Expo even slower.

---

### Post by hyperair on 2007-07-15
Are you sure? After today's update, my Expo and Cube rotation speeds are soaring again. But Trevino's repository debs gave me a whole lot of version mismatches and plugins refusing to load. I wonder why that only affects some people..

Anyway I fixed my version mismatch problems by updating to the debs provided by the vorian repository:
```

deb http://debs.vorian.org feisty extras

```

---

### Post by deepclutch on 2007-07-15
^ but for that remove trevino's repo first!I am using the above repo too.

---

### Post by hyperair on 2007-07-15
Actually I have both repo's enabled. =)

---

### Post by pt123 on 2007-07-16
To use that repo do I have to uninstall compiz-fusion, or would it recognise the new debs with sudo apt-get update, and automatically update compiz-fusion.

Edit: Ok found on his blog the instructions.

[http://vorian.org/?p=82](http://vorian.org/?p=82)

---

### Post by hyperair on 2007-07-17
Don't worry about it. You can just add both repo's like I did, and let them race xD

---

### Post by AlexenderReez on 2007-07-17
hm....

> [http://forums.opencompositing.org/viewtopic.php?f=14&t=131&st=0&sk=t&sd=a&start=380](http://forums.opencompositing.org/viewtopic.php?f=14&t=131&st=0&sk=t&sd=a&start=380)

---

### Post by ThrobbingBrain66 on 2007-07-17
@pt123, hyperair, reez0105:

It really is a bad, bad idea to enable two repos that provide the same packages.  It may work now, but in the end you're just asking for breakage and general unpleasentness.  Also, Trevino's repo (and maybe the others too) come straight from git.

I believe Trevino has warnings posted that there may be breakage (and lots of it) from use of these repos.  You must be willing to accept this when working from a git repo.

---

### Post by hyperair on 2007-07-17
But the debs were pretty much generated in the same way, so they should technically be the same. As of now they haven't screwed up anything so I'll leave the tidying up for later, or I might run into those version mismatches again.

---

### Post by ThrobbingBrain66 on 2007-07-17
That's what I'm saying, there's a good chance you'll run into version mismatches...one repo updates some packages and the other repo updates some different packages.  Pretty soon you're all messed up cause you're using two repos offering different versions of the same packages.  

Anyway, you can do what you want with your install. Personally, I wouldn't want to deal with the hassle and headaches.

---

### Post by nikoPSK on 2007-09-26
Hmmmm. I don't know how to use the repository (download-wise) and if you're running 7.04 If you want to get updates/ unofficial/ unsupported plug-ins just go to synaptic and search compiz and some plug-in packages should appear. (I think the unsupported one includes snow!!!):popcorn:

---

