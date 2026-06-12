---
title: "Neverwinter Nights and the Segmentation Fault"
date: 2009-04-21
forum: Game Specific Discussions
---

### Post by IAMSoylentGreen on 2009-04-21
I'm sure you guys have gotten this issue tons of times, so I apologize, I've just been working on this for about the whole day now, surfing the web and slowly solving each problem until now.

I did the linux client install, and used a guide that I found somewhere in this forum (which was wonderfully written and helped out tons).

So here's the deal once I try to open "nwn" this is the error I get in the terminal:

iamsoylentgreen@iamsoylentgreen-laptop:~$ cd ~/.Games/nwn
[email]iamsoylentgreen@iamsoylentgreen-laptop:~/.Games[/email]/nwn$ exec <nwn
[email]iamsoylentgreen@iamsoylentgreen-laptop:~/.Games[/email]/nwn$ #!/bin/sh
[email]iamsoylentgreen@iamsoylentgreen-laptop:~/.Games[/email]/nwn$ 
[email]iamsoylentgreen@iamsoylentgreen-laptop:~/.Games[/email]/nwn$ # This script runs Neverwinter Nights from the current directory
[email]iamsoylentgreen@iamsoylentgreen-laptop:~/.Games[/email]/nwn$ 
[email]iamsoylentgreen@iamsoylentgreen-laptop:~/.Games[/email]/nwn$ export SDL_MOUSE_RELATIVE=0iamsoylentgreen@iamsoylentgreen-laptop:~/.Games/nwn$ export SDL_VIDEO_X11_DGAMOUSE=0
[email]iamsoylentgreen@iamsoylentgreen-laptop:~/.Games[/email]/nwn$ 
[email]iamsoylentgreen@iamsoylentgreen-laptop:~/.Games[/email]/nwn$ # If you do not wish to use the SDL library included in the package, remove
[email]iamsoylentgreen@iamsoylentgreen-laptop:~/.Games[/email]/nwn$ # ./lib from LD_LIBRARY_PATH
[email]iamsoylentgreen@iamsoylentgreen-laptop:~/.Games[/email]/nwn$ export LD_LIBRARY_PATH=./miles:$LD_LIBRARY_PATH
[email]iamsoylentgreen@iamsoylentgreen-laptop:~/.Games[/email]/nwn$ 
[email]iamsoylentgreen@iamsoylentgreen-laptop:~/.Games[/email]/nwn$ ./nwmain $@
Segmentation fault
[email]iamsoylentgreen@iamsoylentgreen-laptop:~/.Games[/email]/nwn$ exit


Any help would be greatly appreciated.

EDIT: I'm running Ubuntu 8.10. I'm pretty new, but as long as you give me the code, I can obtain any information about my system you might need to help me.

---

### Post by Perfect Storm on 2009-04-21
It seems you havn't be following the guide correctly.


Neverwinter Nights and the Segmentation Fault

--------------------------------------------------------------------------------
I'm sure you guys have gotten this issue tons of times, so I apologize, I've just been working on this for about the whole day now, surfing the web and slowly solving each problem until now.

I did the linux client install, and used a guide that I found somewhere in this forum (which was wonderfully written and helped out tons).

So here's the deal once I try to open "nwn" this is the error I get in the terminal:

```

iamsoylentgreen@iamsoylentgreen-laptop:~$ cd ~/.Games/nwn
iamsoylentgreen@iamsoylentgreen-laptop:~/.Games/nwn$ exec <nwn
iamsoylentgreen@iamsoylentgreen-laptop:~/.Games/nwn$ #!/bin/sh
iamsoylentgreen@iamsoylentgreen-laptop:~/.Games/nwn$ 
iamsoylentgreen@iamsoylentgreen-laptop:~/.Games/nwn$ # This script runs Neverwinter Nights from the current directory
iamsoylentgreen@iamsoylentgreen-laptop:~/.Games/nwn$ 
iamsoylentgreen@iamsoylentgreen-laptop:~/.Games/nwn$ export SDL_MOUSE_RELATIVE=0iamsoylentgreen@iamsoylentgree n-laptop:~/.Games/nwn$ export SDL_VIDEO_X11_DGAMOUSE=0
iamsoylentgreen@iamsoylentgreen-laptop:~/.Games/nwn$ 
iamsoylentgreen@iamsoylentgreen-laptop:~/.Games/nwn$ # If you do not wish to use the SDL library included in the package, remove
iamsoylentgreen@iamsoylentgreen-laptop:~/.Games/nwn$ # ./lib from LD_LIBRARY_PATH
iamsoylentgreen@iamsoylentgreen-laptop:~/.Games/nwn$ export LD_LIBRARY_PATH=./miles:$LD_LIBRARY_PATH
iamsoylentgreen@iamsoylentgreen-laptop:~/.Games/nwn$ 
iamsoylentgreen@iamsoylentgreen-laptop:~/.Games/nwn$ ./nwmain $@

```

There is in the guide that explains that you need to make or edit a file, if you look back at the guide and re-read it I'm sure there's an explaination.

---

