---
title: "Xine playback too bright / washed out!"
date: 2006-06-21
forum: Desktop Environments
---

### Post by dvranizan on 2006-06-21
Hi there everyone!

First off, thank you ahead of time for the help!  This problem has been bugging me for awhile!

Xine (using totem, any other xine-ui, or from the console) playback is very bright and washed out!  Even using the display settings and putting brightness at 0% leaves it ugly!  This occurs for any type of media playback (DVDs, DivX, Xvid... etc).  Any way to fix this?!

I got my codecs from PLF, could that be an issue?

This is occuring on a Presario 2200 notebook, w/ the integrated Intel video card!

Thanks again; I love this community!!!!

---

### Post by olsonar on 2006-06-21
do a
```
sudo gedit /home/yourusername/.gnome2/totem_config
```
find the part that starts with this:
```
# video driver to use
# string, default: auto

```
and replace the next line with this
```
video.driver:xshm
```
save and exit. start totem and playback should be different, hopefully better.

---

