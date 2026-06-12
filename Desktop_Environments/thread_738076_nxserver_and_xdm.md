---
title: "nxserver and xdm"
date: 2008-03-28
forum: Desktop Environments
---

### Post by lorandsm on 2008-03-28
Hi,

I'm using nxserver to do remote desktop on my debian testing box and kde works fine but I want to run xdm also so I can select whatever window manager I want to use, window maker for example, but without success because I get this message when I try to run xdm with nxserver:

The XDM host that was contacted by the NX server doesn't seem to be able to start the session. Please check your server configuration.

Do you have any ideea what's wrong?

---

### Post by scottro on 2008-03-28
I have a Fedora centric page on NX server--I don't know if you can do xdm, but you should be able to do Windowmaker. 

Try [http://home.nyc.rr.com/computertaijutsu/rhnx.html](http://home.nyc.rr.com/computertaijutsu/rhnx.html).  I go through the settings there--it's something like custom command and then put the whole path to wmaker (or whatever the Window Maker script is called--I've not used it in a few years, so I fear I've forgotten.)

No guarantees it will solve your problem, but I was able to use the method I give there to get fluxbox working.

---

### Post by lorandsm on 2008-03-28
Thanks, this is working... but still it would be nice if I could run xdm also.

---

### Post by lorandsm on 2008-03-31
Managed to make XDM work. Two changes were necessary:

1. Modify /etc/X11/xdm/xdm-config and change DispalyManager.requestPort from 0 to 177

2. Uncomment the following line from /etc/X11/xdm/Xaccess:

# *                                                                   #any host can get a login window

---

