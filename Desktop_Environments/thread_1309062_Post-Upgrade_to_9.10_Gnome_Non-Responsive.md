---
title: "Post-Upgrade to 9.10: Gnome Non-Responsive?"
date: 2009-11-01
forum: Desktop Environments
---

### Post by hexbomber on 2009-11-01
So, after I did the net upgrade of 9.04 to the current 9.10 some weird things started happening.

When I boot up, everything starts normally, bringing me to the GDM, however if I try and start a gnome session, it shows me a loading bar, and brings up my gnome-panels (top and bottom), and then freezes. At this point I can't drop to ttyX to try and command line stuff, and I have to reboot.

If however, I drop to ttyX (ctrl-alt-f1), before logging in through the gdm, then I can actually get to a command line. At this point I tried to do an apt-get install gnome, to see if there were any updates, or anything I was missing, but it says I've got the latest version.

If I choose instead, to go start a "failsafe gnome" session, then it starts normally, (minus conky and my screenlets + compiz)

Not sure what this would be, since I never had any issues before.
It's an Inspiron 1525, with 4gb of RAM, and never given me any problems before.

"apt-get install gnome"
> The following packages have unmet dependencies:
  gnome: Depends: gnome-desktop-environment (= 1:2.22.2~4ubuntu8) but it is not going to be installed
         Depends: gnome-vfs-obexftp but it is not installable
E: Broken packages


"apt-get install ubuntu-desktop"
>  Already the newest version... 
Thanks for any help!

---

### Post by BenRip on 2009-11-01
I'm having the same problem. When I try to login the progress bar appears for about one second, then the screen flashes like three to four times and I'm back at the login screen. Using failsafe works, but is of course not the way I want to use ubuntu.

Trying

```
apt-get install gnome
```

leads to the the same result that hexbomber described.

I have beed using 9.10 (and it's latest update) the whole yesterday, but this morning this error appeared.

Hope some of you might be able to help these busy days, anyways thanks for your help!

---

### Post by hexbomber on 2009-11-01
Talking to quite a few people, it seems this is a fairly common problem, this is why I'm not sure why there hasn't been a fix to it yet, it looks like it's been occuring through all the betas and everything.

---

### Post by BenRip on 2009-11-01
I just downgraded to 9.04. Unfortunately Karmic Koala seems to be buggy for daily usage :(.

---

### Post by sdb2028 on 2009-11-01
How do you downgrade back to 9.04?

---

### Post by BenRip on 2009-11-01
Just get rid of 9.10 and start with a fresh install of 9.04 :-D.

---

### Post by hexbomber on 2009-11-01
I'd like to avoid a fresh install if possible.... Anyone know what's causing this error in 9.10? I've always been really impressed with updates, ubuntu seems to get better every ver.

---

### Post by DominicF on 2009-11-06
Has anyone seen a solution to this?

I came into this problem from running Mythbuntu and installed the gnome desktop from within Mythbuntu control centre.

I can only get to a working desktop through failsafe mode.

I'm running this on my main Desktop PC but I've also seen this problem on my Dell laptops when I tried the beta and RC versions of ubuntu.

I'm really feel like packing it all in, I spend so much time trying to fix these problems for myself and then deciding to wait for the next release and of course the next release comes and has some other issue to fix!

---

