---
title: "edgy+beryl+aiglx ?"
date: 2006-10-31
forum: Desktop Environments
---

### Post by louis_nichols on 2006-10-31
Hi folks! I just made a very not uneventful upgrade from dapper to edgy. Now, apart from a couple of things not working (yet, hopefully). I am intrigued by this one thing.

Background: I had beryl running in dapper with XGL and was very happy with it. After the upgrade, my xorg.conf remained the same, and some other config files, I suppose.

After the upgrade to edgy I tried installing beryl again, using aiglx this time, which they say that, being native, should work even better. But I wasn't able to. All I was getting was a freezing desktop everytime I tried to start beryl. I ended up starting it the old xgl way, which works ok.

Still, I would like to be able to use it with aiglx. Does anyone have any idea what I might have done wrong?

---

### Post by 23meg on 2006-10-31
What's your video hardware? If it's nVidia, you need the latest beta driver.

---

### Post by louis_nichols on 2006-10-31
> **23meg said:**
> What's your video hardware? If it's nVidia, you need the latest beta driver.

yes, its an FX5200 with the latest driver form the 8xxx series.

beryl's site has 3 kinds of installing beryl: on top of XGL, on top of AIGLX and then directly over nvidia's beta driver. So te last 2 methods are actually the same? I kind of suspected that...

---

### Post by 23meg on 2006-10-31
For it to work with Edgy's xorg 7.1 without XGL you need the 9625 beta driver.

---

### Post by StomUK on 2006-10-31
and to find the beta driver incase you cant find it (you probably can but it may help others)..
[http://www.nzone.com/object/nzone_downloads_rel70betadriver.html](http://www.nzone.com/object/nzone_downloads_rel70betadriver.html)
bottom of that page

---

### Post by louis_nichols on 2006-11-01
Thanks for the replies, guys! I was a little reluctant to install the beta driver at first. Now I installed it and, even after removing xserver-xgl. beryl works. Well... sort of. All the effects are in place and working fine, but emerald is nowhere to be seen. I mean, windows just don't have a border. I can move and resize them by using the right-click menu from the taskbar and they even wobble when moved, but this is not enough.

Plus, I don't see real improvements in performance, as I was expecting... I might go back to my old setup. What do you think?

---

### Post by 23meg on 2006-11-01
With what command do you start Beryl? Try ```
emerald --replace
```afterwards.

---

### Post by StomUK on 2006-11-01
not sure if this i the problem I was having or not now, mine were flickering allthe time until I killed the manager on startup and then it runs fine for me.

Just found a script on the beryl project homepage though, posted by 'biker' about half way down: [http://forum.beryl-project.org/topic-5682-titlebar-blinks](http://forum.beryl-project.org/topic-5682-titlebar-blinks)
Not sure if that will work for you or not, the Emerald part works really nice here for me.

---

### Post by louis_nichols on 2006-11-01
emerald --replace doesn't do it. Nor is there any output in the console...
StomUK, thx for the idea, but I uninstalled xgl altogether. I was having that problem, too, but it would go away after replacing the window manager with something else and then back to emerald.

---

