---
title: "Can i switch displaynumber for a running program ???"
date: 2009-07-29
forum: Desktop Environments
---

### Post by tomcheng76 on 2009-07-29
Hello community,

I installed Xming X Server on my windows 2003, so that i can run Eclipse on Ubuntu and forward the X display to windows 2003 via ssh.

let's say Xming has display :10.0, Ubuntu has display :0.0
can i change the running eclipse's display number back to :0.0 so that i can turn off windows...It is building workspace and i don't know when will it stop....

Thanks :D

---

### Post by KermitTensmeyer on 2009-07-29
you could change the display number but why?

When one runs an X-Window server on a local work station (reflexion, cygwin, linux) the display is set 
to {host-name/ip-address}:x.y.  most often x.y is 0.0, and in general reflects that this is the first display and first window on that X-window server.
   [ x-window server is the machine that has the keyboard, mouse and screen] [x-window client is running the software, xterm, emacs, remote application etc] (in many cases, the server and the client run on the same machine)

Unless, you have a display waiting that will show client output, changing the display number will be the same as terminating the program. (strictly speaking, using nohup or otherwise disassociating the program from a display, will permit the program to continue running when the display disappears or changes)

 by default most linux workstations have 7 virtual consoles (alt-f1 - alt-f7) The standard graphic display will show up on virtual console 7 and is usually associated with :0.0.  It is possible to run X on another virtual console as well. The display for this console will be 0:1 or 0:2 as selected by the software

 Reflection (an X-window software package for NT, XP et.al.) has the ability to set the display value as part of the configuration)

  so only the software that will have {host}:0.3 as the display value will show up on the virtual screen that is associated with display 3.

  [[ background: in the deep-dark reaches of ancient history, unix-linux workstations could have multiple screens or terminals associated with each server, as a multi-user OS. Each graphic window would have a seperate display value. Some graphic crt's, lcd could have multiple virtual instances.
   so   X:Y  meant   $X was the physical screen and $Y was the virtual screen on the physical address
it should be presumed that once the X server starts, the set of distinct X:Y values available for use is fixed and will not change.

 most often if one needed to switch display's it would be because the value for {host} would change but not the X:Y value


just as an example of changing the display number, in emacs/xemacs there is an option for opening a new frame on a different display. Once the session with the new display has been established, the prior frame on the original display value can be changed while the program is still runnning

--
  this -may- answer your question...

   KT

---

### Post by tomcheng76 on 2009-07-29
Thanks for your detailed explanation.
> Unless, you have a display waiting that will show client output, changing the display number will be the same as terminating the program.
That's what i have, that's why i want to do this. Can you tell me how to change the display number?
My Linux has runlevel 5 and i just want to reset the forwarded program to use local X server instead of windows one. If i don't reset the display number and i turn off the windows pc, the program will be terminated.

It is not a console program, otherwise i should use screen or nohup :-)

---

