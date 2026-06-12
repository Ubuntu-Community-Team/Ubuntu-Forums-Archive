---
title: "Another, yet different,  'nvidia-glx-new is not enabled' problem"
date: 2008-04-12
forum: Desktop Effects &amp; Customization
---

### Post by nge on 2008-04-12
Hi all.

I installed Gutsy in my laptop which has an nVidia GeForce Go 7900 GS. 

Then I installed the nVidia drivers from nVidia's website (not from the repositories) (the NVIDIA-blah-blah-blah.RUN file). The driver installed perfectly, Compiz animations working fine except the cloaking titlebar which is fixed perfectly by filling in 'gtk-window-decorator' in the appropriate box in CompizConfig.

The problem is, I accidentally pressed 'No Animation' in Desktop Settings dialogue. All animations ceased. Then, I pressed 'Normal Animation', and the the 'nvidia-glx-new is not enabled' bug appears. 

Although enabling all repositories and installing nvidia-glx-new could do it for some other people, I presume that it will get me into wasting another precious amount of bandwidth to download some files from the reps and reinstalling another driver that is rather outdated, plus probably is not aimed to my card, which is a GeForce **Go**.

*note*: running compiz from /usr/bin **DOES** enable all the animations again, but who wants to do that manually at every boottime?

Is there any solution to this ?

Since it is a fresh install, I could do a reinstall in another 20 minutes, but the point is all about learning, isn't it ?

thanks,

-nge

---

### Post by Half-Left on 2008-04-12
Add it to the gnome session, System--->Preferences--->Sessions and add the command ```
compiz --replace
```

---

### Post by nge on 2008-04-12
Thanks !

although, I accidentally edited the xinit.rc file and my ubuntu won't go into GDM. So I decided to reinstall; now it's up and running again smoothly.

I'll remember this in case of future problems.

---

