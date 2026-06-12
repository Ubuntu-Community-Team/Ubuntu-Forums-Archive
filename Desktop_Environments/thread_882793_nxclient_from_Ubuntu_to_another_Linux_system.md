---
title: "nxclient from Ubuntu to another Linux system"
date: 2008-08-07
forum: Desktop Environments
---

### Post by mr53308 on 2008-08-07
Hi,

This is a ridiculously specific scenario, but I'm going to go for it anyway...

I am on Ubuntu Hardy Heron, and run Gnome.  I use nxclient 3.2.0-14 to connect to an nxserver running on a CentOS system, where my remote user is also on Gnome.

I can connect without issue and get my desktop, but some things are broken.  When I launch an window:
*It is drawn without a titlebar
*It is drawn without borders
*It is stuck in the upper left hand corner of the desktop
*My mouse doesn't manipulate buttons in that window

I have no such problem when I connect from nxclient in Windows, or from  nxclient from another system running CentOS.

I've run the server in debug mode, the client (in as much as it gives you one), and there don't seem to be any errors at all.

I suspect it is mainly the difference between X implementations in the two distros, or perhaps fonts or something that is causing my problem.  However, I am afraid I have poor knowledge of Linux desktop environments, window managers, and font managers, having been stuck on only the command line for the last ten years or so!

Any suggestions as to where to further look, other debugging I could turn on that seems relevant to this scenario, etc to solve my problem would be quite welcome.

Thanks

Mr 53308

---

### Post by timcredible on 2008-08-07
my suggestion is quit running nx and use the XDM that's natively on every linux and unix machine to make the connection.  by using XDM, it doesn't matter what each machine's window manager is, it'll work just like you're on the console, because XDM is what you're using when on the console.  click on my signature link for a how-to.

---

### Post by mr53308 on 2008-08-07
> **timcredible said:**
> my suggestion is quit running nx and use the XDM that's natively on every linux and unix machine to make the connection.  by using XDM, it doesn't matter what each machine's window manager is, it'll work just like you're on the console, because XDM is what you're using when on the console.  click on my signature link for a how-to.

Thanks for the suggestion.   I am aware of XDM, and several other alternatives I might try like FreeNX or VNC.  

However, this is for work, XDMCP is not turned on, the server is not mine, and I'm stuck connecting to nxserver for now :)

---

