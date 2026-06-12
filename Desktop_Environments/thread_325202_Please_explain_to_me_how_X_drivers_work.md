---
title: "Please explain to me how X drivers work"
date: 2006-12-25
forum: Desktop Environments
---

### Post by hartz on 2006-12-25
Hello Guru's.

I have a basic understanding of how X-windows work (The server has got the Keyboard, display and mouse as basic resources, and clients request that they be drawn by the server).

But how does the drivers work?  I've just compiled the 2.6.19.1 kernel with some options, and then after reading many guides, got the nvidia driver to once again work (was stuck with either using nv or falling back to my old kernel for a bit).

What I want to know is basically where is this nVidia module, by what does it get loaded (Seems it is not the kernel, though there is a kernel modules called nvidia), why did it want to rebuild the module (Why can't it use the one I had with my 2.16.17-10 kernel)

I get the impression that there is a difference between a kernel module or driver, and an x-windows "driver".  And more over, I get the idea from hints in some news group postings that Xorg version 7 and later is meant to (has) drastically altered how these modules are used (by not being monolithic).

Can I get the nVidia X-Windows driver to be a statically loaded module, permanently part of my kernel?  Does any of the new Xorg 7.x architecture revisions mean that the communications overheard between the display server, the client and the rendering engine (the x-windows driver?) will be eliminated?  Is that what "DRI" is meant to be?

Basically, I want to understand how the other side of the X-server works, after the client connected to the x-server, and the x-server has received a request to draw something, how does the flow work to get to the screen?

Something like
1. X-server
2. back-and forth between composition manager, display-manager, and x-server until everything is in place
3. X-server calls XYZ
4. XYZ calls the X-driver
5.  The X-driver passes calls the Kernel API
6. The kernel loads some hardware device driver if necessary
7. The API passes the instructions on to the loaded kernel module
8. The kernel module talks to system ports and the hardware does it's thing.

Basically, can someone flesh-out and correct my understanding of the above please.

Thanx,
  _Hartz

---

