---
title: "Vnc4server doesn't work with xinetd (remote login to desktop)"
date: 2008-01-31
forum: Desktop Environments
---

### Post by sola on 2008-01-31
Hi All,

I have a fresh Gutsy desktop installation which I would like to access from a remote computer (windows machine) through VNC. I cannot use vino (the default) because I don't wan't to allow my linux machine to automatically login (vino requires that) and I want to use different screen resolution on the client than the host machine (vino can only provide the resolution of the host).

I chose the xinetd solution because there were a lot of HOWTOs about it and it seemed ideal since it would have provided similar experience to Xming. (Xming is a proper X server for Windows but it is too slow on my wireless home network that is why I wanted a VNC solution which uses compression).

The HOWTOs were mostly for pre-Gutsy versions of Ubuntu and I didn't find Gutsy specific parts in them.

I tried all of the troubleshooting I could gather but none of them helped. So I think the xinetd working mode of the vnc4server is broken since the most I could get was a blank grey screen with a mouse cursor. I never managed to get a Gnome login screen with xinetd.

I managed to get a half-working gnome desktop if I start the vncserver from the main user but that is not enough because it is not a real login. I would like to have XDMCP-like operation.

Is there anyone who has a working Gutsy installation wit xinetd and GDM login?

I would really appreciate any help !!!

---

### Post by Andrew Stone on 2008-02-07
If you got a grey screen with a mouse cursor, then that means that the X server is running but the gnome desktop is not.  You need to get gdm to run on multiple X screens.  I wasn't sure how to do this, but found an answer in this forum which I've pasted below (note your screen might not be :1).


So, in the file :
/etc/X11/gdm/gdm.conf

please mention that u'll like it in both :0 and :1
That should be indicated as follows :
...
[servers]
# These are the standard servers. You can add as many you want here
# and they will always be started. Each line must start with a unique
# number and that will be the display number of that server. Usually just
# the 0 server is used.
0=Standard
1=Standard
# Note the VTAllocation and FirstVT keys on linux and freebsd.
# Don't add any vt<number> arguments if VTAllocation is on, and set FirstVT to
# be the first vt available that your gettys don't grab (gettys are usually
# dumb and grab even a vt that has already been taken). Using 7 will work
# pretty much for all linux distributions. VTAllocation is not currently
# implemented on anything but linux and freebsd. Feel free to send patches.
# X servers will just not get any extra arguments then.
#

---

### Post by sola on 2008-02-12
Thanks for the reply.

I believe, I already tried that but it didn't work. (I also suspected that the GDM configuration may be responsible)

Finally I stopped trying and installed FreeNX.

FreeNX didn't work either first only after installing a fresh Gutsy instance on that machine.

So, it is possible that Vnc4server was not the cause of the problem but I cannot prove it because the FreeNX server works perfectly now with OpenSSH so I don't want to touch it.

Thanks again

---

