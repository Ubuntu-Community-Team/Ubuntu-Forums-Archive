---
title: "composite mode - desktop and playing movies full screen"
date: 2009-07-05
forum: Desktop Environments
---

### Post by matamoscas on 2009-07-05
Hello, 

I have recently moved over to (K)ubuntu full time, build a sweet rig, use most of the "bells and whistles," but whenever I try to watch a movie (with Dragon player or mplayer) in full screen the playback is very choppy for about 2-3 minutes..

Then, a little message shows up saying something about Composite mode (and unfortunately, just as quickly disappears), and the video playback in full screen is as I would expect -- very good.

When I go back to my desktop, many of the "effects" no longer work (desktop features, like Cube effect when I change windows)...=( I am assuming, something was turned off so that I can view the feature full screen.

I was curious, what key combinations or other alteration can I do that will allow me to toggle this "desktop composite -- or what not" so that I can view full screen video, but then also turn back on my composite mode.

Thanks in advance
matt

---

### Post by txcrackers on 2009-07-05
There appears to be a bug/conflict with the desktop effects and some video playback/full-screen applications. Once you've "lost" the effects, they won't come back until you log out and log back in. In between I usually restart X (from the login window) just to be on the safe side.

I consider it a *minor* annoyance at this time because even without the golly-gee-whiz effects, it still works just fine... ;)

---

### Post by matamoscas on 2009-07-05
thanks for the info =)

Little things like that will drive me batty trying to figure out -- even when there is nothing to figure out..hehe

---

### Post by krazyd on 2009-07-06
Hi matt,

The video is choppy because your graphics card is struggling to do compositing and video playback at the same time. The box which pops up is a message saying that KDE has detected a slow compositing frame rate and so it has disabled compositing. That's why effects are off when the video ends.

Whether or not you can play video fullscreen with compositing depends on your video card. What card do you have?

Also, there is no need to log out and in again. The key combo for toggling compositing is <Alt>+<Shift>+<f12>. I have an older graphics card and usually just switch off compositing using that key combo before I watch a movie or something.

---

