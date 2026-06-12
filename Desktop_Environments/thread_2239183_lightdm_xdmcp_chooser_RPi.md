---
title: "lightdm xdmcp chooser RPi"
date: 2014-08-12
forum: Desktop Environments
---

### Post by e_defranco on 2014-08-12
Hi to all !

I have this problem: I have 3 client Raspberry Pi with raspbian that I would like to connect to 4 xubuntu desktop on the lan via xdmcp.

I would like choose the server where I connect on the client or, in other words, I would like to see what server is up before connecting.

I remember that on old Mandriva 9.2, I get a chooser that permit me to connect on one or other server, showing only list of server that was up.

I have read more doc. on xdm, xdmcp, lightdm (no find more realy about it) and, if I have understand correctly, when the client send an indirect broadcast query, the first server that reply answer with a chooser and the list of the server available.

But lightdm have no chooser application ...

I have also installed on a raspbian "server" (an image without any graphical application) Xorg and xdm thinking that maybe local xdm can display the chooser but I don't know how to configure xdm for this.

Finaly, desperate and despondent, I have created a "stupid user" on the client RPi and a bash script that start automaticaly after login that ping the server on the lan and not permit to choose the server that is not responding: is more functionaly and working fine, but is no more nice to see ...

There are some one that can help me with the configuration of xdm for displaing the chooser localy ?

In alternative, how I can do starting a graphic window with my chooser ?

Thank in advance, 

Emilio

---

