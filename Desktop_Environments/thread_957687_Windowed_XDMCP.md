---
title: "Windowed XDMCP?"
date: 2008-10-24
forum: Desktop Environments
---

### Post by tilapia on 2008-10-24
I'd like to access my Debian machine, which is used as a development server, from my Ubuntu Intrepid Ibex machine via XDMCP. I've set up XDMCP on the Debian box and can login to the machine via Ubuntu no problem. It's surprisingly usable, and it's easy to forget that it's all being done over the network. 

However, rather than logging out of my Ubuntu session every time I want to use the Debian box I'm wondering whether it would be possible to created a windowed XDMCP session, or a full screen session on one of my virtual desktops?

I've considered setting up a basic virtual machine and running that in Virtualbox to allow me to access the Debian box, but I'm wondering if there's a less bloated way to do this. 

Any ideas anyone?

---

### Post by tilapia on 2008-10-25
I've discovered Xnest and Xephyr, which both do the job, although seem a tad buggy. I might go with the VM route after all.

---

