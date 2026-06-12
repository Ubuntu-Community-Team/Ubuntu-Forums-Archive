---
title: "twinview VS sdl-windowed mode"
date: 2009-08-03
forum: Desktop Environments
---

### Post by dal on 2009-08-03
Hey all,

I have a dual monitor setup running under nvidia twinview. I'm wanting to be able to fire up SDL apps (games) in windowed mode to run maximized on one of the screens and have xine playing back a video on the other. The monitor layout is my secondary monitor on the left running at 1680x1050, main one on the right at 1920x1200.

The problem I'm running into is that twinview doesn't play nice with SDL apparently - on startup, most linux games I've tried (warzone 2100, openarena) display a 3600x1200 fullscreen-style window starting from the main monitor (and as the secondary is to the left rather than the right, I only see a little over half of this window). These games offer a windowed mode, but when I select it I can't change the resolution from 3600x1200 (nor can I change the res when fullscreen is selected).

The only work around I've found so far is to set a metamode in xorg.conf along the lines of "NULL,1920x1200" but of course that would turn off the secondary screen instead of allowing me to use it for video playback. Google turned up something called Xnest that would apparently let me run another X server inside a window (sounds good) but apparently it doesn't play nice with 3d acceleration (not so much). I also saw mention of running simultaneous instances of X, but the article I found that mentioned doing that was about running them on different ttys, which again would leave me unable to see the instance of X that was running the video on my secondary monitor for instance if I were to run another instance on my main monitor just for the SDL app.

Is anyone aware of a way to achieve what I'm trying to do, short of seeking out windows versions of these programs and forcing wine to window them for me?

---

