---
title: "monitor driver problem after EnvyNG"
date: 2008-10-11
forum: Desktop Environments
---

### Post by helionaut on 2008-10-11
Hi everyone, I'm running Ubuntu 8.04 and tried downloading and installing EnvyNG so I could make my desktop extra shiny, but there was an error when I tried to automatically detect my drivers. I chose the manual option, and it seemed to work. However, after I restarted, Ubuntu said that the screen properties couldn't be found, and that it wanted to run in safe mode. I uninstalled the envyng packages through synaptic package manager, but after I restarted again, the screen was split into four very narrow screens with black bands running through them so I could barely see anything, and definitely not read any text.

I'm running 7.10 on the LiveCD now. If anyone knows if I can fix this, what should I do? The vast majority of my personal files is backed up so it wouldn't be a COMPLETE disaster if I had to do a fresh install+upgrade (from 7.10 to 8.04 again), but I'd prefer not to if at all possible.

I am able to use the terminal mode just fine; only the graphical environment is affected. (well, maybe the text is a little smaller than it used to be)

Help?

-N00B

EDIT: I reconfigured my xorg.conf file, and was somehow able to boot and get my desktop to show normally. However, if I try to do anything like open files or folders or move windows around, it's clear that something is not right - the resolution of the window rapidly switches and then adjusts to normal (1024x768), and then is VERY slow and choppy, but otherwise normal. Setting the "Visual Effects" to "none" seems to help somewhat.

---

