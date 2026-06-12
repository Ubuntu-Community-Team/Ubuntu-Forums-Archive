---
title: "[SOLVED] [Help!] XPS M1210 Openglx Strange Problem"
date: 2007-12-13
forum: Dell  Ubuntu Support
---

### Post by creatorlarry on 2007-12-13
Hi, I've been using Ubuntu on my Dell M1210 laptop for several years and I'm currently running Gusty Gibbon. Everything worked perfect when I upgraded to Gusty Gibbon except that opengl programs became quite unstable.

I first found this when I was playing 3D game, the performance would drop drastically after about 7 minutes of playing. The CPU usage would become 100% and the movement of mouse became choppy. Then the screen would blink intermittently. (I recorded this using my mobile, I can upload it if it is needed) And again about 7 minutes later, all would become normal and run as smooth as before.

First I speculated this was due to high temperature of CPU or GPU because this didn't happen instantly I ran the program. I installed gkrellm to monitor both temperature of my CPU and GPU but found that the temperature didn't changed a lot when I was running those games (CPU: about 75C~85C and GPU 75~100C) and it was a bit lower when the slowdown occurred. I also tried to change and monitor CPU frequency scaling, and it wasn't the problem either.

Later I found that, even glxgear cannot run for more than 7 minutes. It will run smoothly at  2300~2400 fps with 60% cpu usage for about 7 minutes and then hang the system and the symptoms I described will occur again. Finally it recover after about 7 minutes.

So I am just so confused about what is happening here. I think maybe there is some kind of job that is running in a 7-minute cycle or sth like that.

I just want to know if anyone else also experienced this problem and if there is someone knows how to solve it.

My System:
CPU: Core Duo T7200 
Memory: 1G
Video Card: nvidia Go 7400
Ubuntu: Gutsy Gibbon
Kernel: 2.6.22-14-generic
NVIDIA driver: 169.04 (stable version has the same problem, I tried)
xorg.conf: see attachment

---

### Post by creatorlarry on 2007-12-22
An update of this problem.

Now I changed to 64-bit ubuntu, the problem is somehow relieved. Glxgears can run for about 10 minutes now, but will still slow down and hang up the system after that. 

One more problem, I can only use Gnash to play flash files instead of Adobe player in 64 bit firefox. Gnash has the same problem as glxgears', but adobe flash player doesn't have this problem. I am not quite sure if Gnash also uses opengl as output while adobe doesn't. Or maybe this is caused by some other stuff.

---

