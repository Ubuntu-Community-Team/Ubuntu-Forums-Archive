---
title: "Two computers, one monitor and one set of input devices?"
date: 2006-03-03
forum: Desktop Environments
---

### Post by MaX on 2006-03-03
Is it possible?

I have a computer in my livingroom (sam) running Ubuntu and a computer that I dualboot (lillemor) in my bedroom. I want to be able to log in via the network on the sam computer and preferably have it on my second desktop but using CTRL+F8-F9 would be good too.

How do I do a remote login while keeping my own X-server running on the lillemor computer? I've looked at synergy but then I need multiple monitors which I can't afford and don't have room for.

I don't want to get another set of cables and use a KVM switch either.
So does anyone have any pointers?

---

### Post by stuporglue on 2006-03-03
Is VNC acceptable? I'll bring up the remote computer in a window (can also do fullscreen though).

---

### Post by adam.stokes on 2006-03-03
Lookup xdcmp works pretty good if you only want it on the local network, but has security risks.. will allow you to use the function keys to switch between desktops.. think of it like a software kvm

---

### Post by MaX on 2006-03-04
[QUOTE=adam.stokes]Lookup xdcmp works pretty good if you only want it on the local network, but has security risks.. will allow you to use the function keys to switch between desktops.. think of it like a software kvm[/QUOTE]
You don't happen to have a good tutorial or Howto for it?
The one's I found seemed kind of Redhatish, I got the xdmcp server set up all right (I think) but how do I discover it from my main computer?

---

### Post by hw-tph on 2006-03-04
I have a similar setup but I don't feel the need for a complete second desktop. I just ssh to the remote machine (with X forwarding) and start whatever programs I want and have them displayed on my local computer (usually my laptop). So the other computer can stay in the closet. :)

Use **ssh -X user@host** to log in to the remote host, then simply start programs from the shell like usual: **firefox &** - the ampersand will make the application detach so you can continue using the shell. screen is recommended as well.


Håkan

---

### Post by MaX on 2006-03-06
[QUOTE=hw-tph]I have a similar setup but I don't feel the need for a complete second desktop. I just ssh to the remote machine (with X forwarding) and start whatever programs I want and have them displayed on my local computer (usually my laptop). So the other computer can stay in the closet. :)

Use **ssh -X user@host** to log in to the remote host, then simply start programs from the shell like usual: **firefox &** - the ampersand will make the application detach so you can continue using the shell. screen is recommended as well.


Håkan[/QUOTE]
This is how I do today, but I want to be able to do Alt+F2 and using the menu etc, not being limited to starting all my programs in the terminal.

---

