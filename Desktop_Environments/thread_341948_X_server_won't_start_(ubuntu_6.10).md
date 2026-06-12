---
title: "X server won't start (ubuntu 6.10)"
date: 2007-01-19
forum: Desktop Environments
---

### Post by .Mo on 2007-01-19
Hey guys,

ok I've been playing around with Linux for about a month now, so I'm pretty new to it. I figured it'll be nice to see some cool 3D effects so I installed the nvidia driver with envy. It worked nicely for a couple of days, but suddenly it just won't startup anymore.

When it starts up the nvidia logo shows up for about a second, then the screen get black and I only can see the mouse. But not for long, cause then it starts over again. It does that endlessly. So I log in with alt + ctrl + F1 and stop gdm. When I do "startx" then the Screen becomes black with alot of small white dots und the cursor becomes an X. That's it. So I stop the xserver and log in as root  (I know that's not the way to do it in ubuntu but so what). When I do "startx" then the xserver starts and everything works fine... except that i can't switch to my normal user account, neither restart or shutdown the pc.

So... any suggestions? Whats the difference between logging in as a "normal" user and as root (except for the rights of course)? They use the same xorg.cof right? So there shouldn't be the mistake, but where else? :confused: 

Thanks in advance; Mo

---

### Post by NeoLithium on 2007-01-19
Well, dependin gon which guide you used, did you make a backup?  If you did, all you'd have to do is boot into recovery mode; and type:
```

sudo cp <backup name> xorg.conf

```
and that'll restore the configuration that you had before you changed it.

---

### Post by Greevous on 2007-01-19
What can we do if we don't happen to have a backup of the xorg.conf? I screwed with the mouse settings (actually followed my own advice from one of my posts a little while back) and now my scroll button is mapped to "Back" and "Forward" in Firefox. It's driving me nuts! I try to scroll up and it sends me back 3 or 4 pages! Arrrrgh.

The story is I changed Input device options for my mouse which is a M$ Trackball optical, so I could have support for a 5-button mouse. What I did was exactly what I had done before, making the xorg.conf mouse entry the same exact thing as I had it, but now things are pretty bad and I can't get them back to normal. 

I'd give up my forward and backward buttons any day, as long as my scroll button will simply scroll UP and DOWN and page instead of to and fro. ](*,)

---

### Post by Kangaroo on 2007-01-19
You can reconfigure your X-Server manually 

Enter 
```
 sudo dpkg-reconfigure xserver-xorg 
```

and answer the questions to the best of your knowledge
(Automatic is mostly not a bad choice) 

Maybe try out the "nvidia" and the "nv" driver (nv = NO 3D Acceleration)

---

### Post by r4ik on 2007-01-19
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) for drivers.

---

### Post by .Mo on 2007-01-20
Yeah, I backed up my xorg.conf but using it didn't make a difference, expet that the nvidia logo disappers when it starts up, since the old .conf uses the nv driver instead the nvidia one. So I don't think the problem is the xorg.conf.
As root I can do ```
startx
``` and the Xserver works fine, only when I try to start it as a normal user it crashes. So what's the difference? Are there configuration files for the x serer for every individual user?

---

