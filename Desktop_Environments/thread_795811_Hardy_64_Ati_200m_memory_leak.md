---
title: "Hardy 64 Ati 200m memory leak?"
date: 2008-05-15
forum: Desktop Environments
---

### Post by jbruceca on 2008-05-15
Hey guys,

I just recently installed Hardy 64 on my dv5000. I didn't have any problems wiith the drivers installing fglrx thru ENVYNG with ease. I rebooted, and immediately the card recognized the card and driver thus enabling affects as shown below:

OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon Xpress Series
OpenGL version string: 2.1.7412 Release

Now this is where it get's tricky and I cannot seem to wrap my head around this. When idling with Desktop manager enabled compiz just EATS at my ram (512mb) going at about 8 mb a min or so. When I disable this of course the issue is gone and the ram is returned. Well I did some research and apparently it is a card issue with handling OpenGL. Well I decided to test this..So I ran GLXgears for 10 minutes, the FPS was fine the whole time...Memory didn't move one inch. So my theory of this being leaky GL is now out the window...I'm not TO sure what to do next, Now I am not sure what to do, as my Video runs fine, Glxgears runs fine, Full Screen video playback is fine...Just Compiz is leaking...And It's a shame that I cant enjoy this feature. Any help or ideas will help.On a side note GLXgears does max my cpu, not really slowinganythign down just running it at 100%

---

