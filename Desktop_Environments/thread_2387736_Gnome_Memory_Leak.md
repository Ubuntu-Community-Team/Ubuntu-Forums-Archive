---
title: "Gnome Memory Leak"
date: 2018-03-23
forum: Desktop Environments
---

### Post by galacticstone on 2018-03-23
Link - [https://www.omgubuntu.co.uk/2018/03/gnome-shell-has-a-memory-leak-and-it-might-not-be-fixed-for-ubuntu-18-04-lts](https://www.omgubuntu.co.uk/2018/03/gnome-shell-has-a-memory-leak-and-it-might-not-be-fixed-for-ubuntu-18-04-lts)

Link - [https://fossbytes.com/gnome-3-26-memory-leak-issue-no-fix-ubuntu-18-04/](https://fossbytes.com/gnome-3-26-memory-leak-issue-no-fix-ubuntu-18-04/)

This has me a bit worried because I use Gnome and I only have 4g of RAM. I plan on updating to 18.04 when the stable release version becomes available, but now I am considering a switch to different desktop (possibly MATE, Xfce or similar).

Does anyone know if this issue will be fixed in time for the 18.04 release?

---

### Post by exploder on 2018-03-23
If you like using Gnome Shell I would not be that concerned about that article. I read the article the other day and watched the video, who is going to do that? I am running 18.04, testing it and am not having any problems because of a memory leak. Even so, somewhere down the line if it is a real issue, I am sure it will be addressed. Try 18.0 when it is released in April and decide for yourself.:)

---

### Post by kerry_s on 2018-03-23
I've never had that problem.
i'm using ubuntu 18, which is using gnome snaps.
I've used gnome on many different distros & don't see leaking.

---

### Post by vanadium on 2018-03-23
I am pretty convinced now after testing that this is a real issue, although not of direct practical concern in many scenario's. For users with plenty of ram, it is not a practical problem - As a laptop user regularly turning it off, I would never have noticed it were it not for the article. On normal use, memory use of gnome-shell would increase from about 350 MB to about 800 MB in about four hours. On my 16 GB system, there is plenty of memory left.

In a same scenario, it even might not be a really noticeable issue for users with only 4 MB. You still can make it through the through the day. It becomes an issue of practical concern for users that keep their systems on or suspend them. If the increase would continue to be linear according to my observations over three hours, about 3.3 G would be taken by the gnome-shell process after 24 hours. With heavy tests (very frequent opening/closing of overview/applications (scripted of course), loading many applications ... ) I was able to increase memory use to close to 2 GB. 

Will it be fixed? Not sure at all. Hopefully, this "press" will now lead to more intensive attempts of stopping this and similar issue that are being reported on Gnome since many years.

---

### Post by galacticstone on 2018-03-23
Thanks for the responses. So this might be another case of much-ado-about-nothing. Given my average usage, this shouldn't be much of a problem if the issue is as described above.

Given that this is a known issue that is not new, I would hope the devs would fix this - we'll see. It won't stop me from trying out 18 when it's released though.  

If worst comes to worst, I can always ditch Gnome - although I would hate to do that because I am comfortable with it now.

---

### Post by again? on 2018-03-23
I didn't mind gnome-shell but did notice this memory leak
and as an avid watcher of my system through conky it continually irritated me.
Also don't like the way gdm3 implelements the tty consoles. (that's 100mb alone)

I rationalized what I use and need and moved to Xubuntu with lightdm, plank and kupfer.
Also use a script from bunsen labs to implement hot corners.
First time booted up to less than 500mb mem use in years.

Unexpected bonus: xfce4-terminal --drop-down

---

### Post by friarlawless on 2018-03-23
I actually had been running into random error messages in Gnome (when I used 17.10) and wondered what was up. Now I'm curious if this was related. I do tend to sleep/suspend my laptop for days on end. Haven't noticed it in 18.04 beta yet, but I'm playing around with XFCE at the moment.

---

