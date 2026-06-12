---
title: "help starting simultaneous X servers"
date: 2006-01-04
forum: General Help
---

### Post by phlosipher on 2006-01-04
I want to be able to run simultaneous X servers on the same monitor using two different displays.

At least I think I do. Maybe you all have better suggestions. What I really want to do is be able to switch "environments" with a hotkey (in this case hitting the CTRL-ALT-Fn). One environment might be my normal login. Another might be a QEMU session running a different OS. A third environment would be a NX session on another computer. I used to use this kind of strategy with win4lin for example, with great success.

The reason that I dont just use normal hotkeys is because both QEMU and NX client grab the keyboard (except the functions keys available with the virtual consoles!!!!) so I cant just program in a normal response to a hotkey. Once displaying the QEMU or NX session, the keystrokes are intercepted by QEMU or NX rather than passed to my original desktop session, where I could do something with them.

So, I have been trying to start up extra servers on VT8 or VT9. I am trying commands like startx or X but I dont have the magic. Here is the output from entering commands into an xterm.

Wed@10:41[240]:startx -- :1 vt8
xauth:  creating new authority file /home/pjr/.serverauth.31598
X: user not authorized to run the X server, aborting.
xinit:  Server error.
Couldnt get a file descriptor referring to the console

or

Wed@10:41[241]:X :1 vt8
X: user not authorized to run the X server, aborting.

I can  get this working by switching to VT1, logging in and then issuing the commands. Everything works OK that way. But I cant do it from xterm. I figure that I either have to set something in the GDM config file, set something for xauth, or some something in analogy to the /etc/X11/xdm/Xservers file but I cant find any info on how to do so. Can somebody help me out?

Thanks

Phil

---

### Post by schilcha on 2006-01-04
Not sure, if I understood your needs correctly, but maybe Xnest can help you (I don't have practical experience with it)

Here's the package description:
> 
nested X server
Xnest is an X server that is itself an X client.  This allows you to run a
server within a server; this is occasionally useful for testing new window
managers and other X clients.

Xnest relies upon its parent X server for font services.


---

