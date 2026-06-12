---
title: "XBMC and Ubuntu-Desktop via VNC"
date: 2009-04-04
forum: General Help
---

### Post by MP3HiFi on 2009-04-04
Hi all,

I would like to say hello because this is my first post. 

I have a questions setting up a htpc for mutlimedia. What I like to do is running autostart xbmc (XBox Media Center). That is no really great problem. Additionaly I want run an Ubuntu-Desktop where I can connect via VNC.

I have tested a lot but I am not able to get I running. The first attempt was creating autologin in event.d via mingetty. The file bash_login in the home folder of the two users were

[LIST]
[*]xinit gonme-session -- :0   for ubuntu and
[*]xinit xbmc -- :1    for xbmc
[/LIST]

That havent worked. Is there an ohter easy solution for my problem. I have figured out a workaround with running a virtual machine for the ubuntu-desktop but I think there must be an other solution. I am not fixed to Ubuntu. XUbuntu or KUbuntu would be fine too.

If you have any question please ask.

Thank you
Martin

---

### Post by chuckheron on 2009-11-24
Hi,
You can just start a vncserver session.

vncserver :1 -geometry 1200x900

This will start an ubuntu-desktop on hostname:1
that you can connect to with your vnc client.

-chuck

---

### Post by MP3HiFi on 2009-11-24
Thanks for replying. I have changed to run XBMC on Ubuntu Server and a VMWare with an Ubuntu-Desktop. It is much better to handle.

---

