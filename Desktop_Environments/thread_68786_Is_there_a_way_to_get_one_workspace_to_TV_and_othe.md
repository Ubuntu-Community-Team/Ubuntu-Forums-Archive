---
title: "Is there a way to get one workspace to TV and others working normally?"
date: 2005-09-24
forum: Desktop Environments
---

### Post by eduard0 on 2005-09-24
*I believe this belongs to this section...* 

Now that I finally managed to get ATI's display drivers and hardware acceleration to work, I'd like to know if there's a way to get one of the workspaces to TV and other 3 workspaces working normally.

TV-out works somehow, although there are some problems with resolution and such. I would like to get 1024*768 resolution to TV and 1280*1024 to my primary display at all times, even if I used mirrored or clone mode in TV-out. (I'd still like to get a customized tv-out mode as explained above...) How to do this?

And if it helps, I'm using Ubuntu 5.04 amd64.

---

### Post by Caboto on 2005-09-24
I'm already searching for something very similiar for a long time now... The problem lies within the ATI Driver. Nvidia has that TwinView Thingie. You can use different resolutions for TV-Out and the DVI/VGA Output. I hope ATI will work on their TV-Out driver for Linux...

I don't think, there's a solution with the 8.14.13 driver. Hopefully someone proves me wrong...

---

### Post by eduard0 on 2005-09-25
Have I understood this right, it's possible to run multiple instances of X at the same time? When I try command startx it says: 

Fatal server error:
Server is already active for display 0
        If this server is no longer running, remove /tmp/.X0-lock
        and start again.

Indeed, X is active for display 0 (which happens to be my primary display) but NOT for display 1 (which should be my TV). Is it possible to start another X to display 1?

And just one more thing. When I use Ctrl + Alt + FunctionKey (F1, F2...) the first 6 are text based terminals and 7&8 are supposed to be graphical? Number 7 is the default one, but how can I get the no. 8 working (preferably in my TV)?

*So many ideas but not a clue how to get them working.*

---

