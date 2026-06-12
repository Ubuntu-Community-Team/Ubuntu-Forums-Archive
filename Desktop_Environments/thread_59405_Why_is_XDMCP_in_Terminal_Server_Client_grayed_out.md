---
title: "Why is XDMCP in Terminal Server Client grayed out?"
date: 2005-08-23
forum: Desktop Environments
---

### Post by gcmartin on 2005-08-23
I need to access a Linux server on my LAN. I am using "Ubuntu" LIveCD version 5.04 for Intel x86. I have run across a phenomenom I never seen before.

When the Terminal server client opens on the desktop, it does offer me the ability to use it to connect to the Linux server. The Terminal Server Client has XDMCP grayed out. WHY? (Terminal server client version number is 0.132) 

What must I do to get the terminal server client to open allowing XDMCP to be available to get the logon screen from my remote Linux server?

thanks

---

### Post by gcmartin on 2005-08-26
Problem exists because Ubuntu never installed a required package before created the LiveCD distro.I got this straight from the Terminal Server Client author. He says: "If you want XDMCP as an option, you'll have to install the xorg XNest package.  That should enable it."

I followed his directions and did the following:
1. apt-get upgrade
2. apt-get install xnest

Then, I went to Start...Internet...Terminal Server Client....XDMCP..."voila", I can now sign on to my Linux Terminal server on my local LAN. Ubuntu with XDMCP is a wonderful solution for home, or schools or ...

Now does anyone know how to get this message to the Ubuntu developers, so that they can properly set  this up in the LiveCD's ISO  package?

I appreciate ANY help here. Thanks

---

