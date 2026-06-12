---
title: "amaroK eq greyed out"
date: 2005-07-30
forum: Desktop Environments
---

### Post by Bluefire on 2005-07-30
I installed Kubuntu, got mythtv working, and love it so far.  I have run into one problem though.

I absolutely love amaroK, but I am having one problem with it.  When I go to the tools menu, the Equalizer is greyed out.  Its been like this ever since I installed kubuntu.

Does anyone have any suggestions?  I've tried removing and reinstalling using apt-get.

---

### Post by royg1234 on 2005-07-30
I think it has something do with what engine you're using.  Try changing engines and see if the equalizer comes back.

---

### Post by Bluefire on 2005-07-30
[QUOTE=royg1234]I think it has something do with what engine you're using.  Try changing engines and see if the equalizer comes back.[/QUOTE]
 I only have aRts engine installed, should I install a different one?  and if so, whats the apt-get name?

sorry, I'm a linux newb :D

---

### Post by Loungefly on 2005-07-31
If you're new to Linux I'd highly recommend using Synaptic instead of the console when installing packages etc. It's a nice user friendly front end for apt. (just 'apt-get install synaptic' from the command line if you don't have it already)

You'd need the Xine engine for amarok in order to use the equalizer (I think the Gstreamer engine supports it too, not 100% sure about that though).

I can't remember what the exact apt-get name for the xine engine is off the top of my head (I'm not using Linux at the moment otherwise I'd be able to check right now), but if you use Synaptic you just have to search using simply "amarok' and it will give you a list of the amarok related engines to install. It's pretty self self explantory from there Once you install the plugins you can select the Xine engine in engine settings in Amarok and you'll be able to use the equalizer :)

---

### Post by samuraisam on 2005-07-31
[QUOTE=Bluefire]I installed Kubuntu, got mythtv working, and love it so far.  I have run into one problem though.

I absolutely love amaroK, but I am having one problem with it.  When I go to the tools menu, the Equalizer is greyed out.  Its been like this ever since I installed kubuntu.

Does anyone have any suggestions?  I've tried removing and reinstalling using apt-get.[/QUOTE]
 What you want is:

```
apt-get install amarok-xine
```

You may also want to install "libxine1."

Enjoy! :)

-Sam

---

### Post by Bluefire on 2005-07-31
Thanks guys!

You were right about using the package manager, it installed the packages I needed for Xine.

It sounds awesome now with an eq ;)

Thanks again everyone!  Oh, and btw, (k)ubuntu 4 life.   \\:D/

---

### Post by Mishura on 2005-07-31
I use GStreamer, myself, and Equalizer works for it.  Just noting for future reference.

---

### Post by Freddy on 2005-07-31
Using the Gstreamer engine is what the amaroK team recommend.

---

