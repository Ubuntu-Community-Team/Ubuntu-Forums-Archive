---
title: "How can I get something like XPRA to work with Blackbox"
date: 2012-10-06
forum: Desktop Environments
---

### Post by sulpherdragon on 2012-10-06
I have xorg on an ubuntu server and I'm forwarding X applications to my windows PC to Xming. I can forward blackbox/fluxbox easily but I want to keep the session alive after I close it. I've been trying to get xpra to work with blackbox because that kind of solution would be great, but it seems that they both want to be windows managers and take up the display port.

Is there any way to attach blackbox to xpra after blackbox has started?

I essentially want to run something like Windows RDP where people can remote desktop into a machine. It doesn't have to be very user friendly but I think VNC is overkill to run on the server.

Does anyone have any suggestions?

---

### Post by LewisTM on 2012-10-06
I'm a bit confused here. Is blackbox on the client or the server? You start by saying that Windows is the client but then you want to attach backbox to xpra.

I don't know if blackbox behaves differently from other WMs. Basically you need to 

1) Start an xpra server on the machine that will run the program
```
xpra start :7
```
2) Attach the client to the server
```
xpra attach ssh:user@server:7
```
3) Launch an X application remotely, typically inside an ssh+screen session
```
DISPLAY=:7 command
```

Cheers!

---

### Post by sulpherdragon on 2012-10-06
blackbox is on the server.

DISPLAY=:7 nautilus

This works fine but I want to run the actual desktop environment in xpra.
Like this:

DISPLAY=:7 blackbox

This does not work because it seems blackbox is a windows manager as well as a desktop shell and xpra is also a wm. I might need an alternative to black box. Perhaps I'm misunderstanding how this stuff works.

Thanks

---

### Post by LewisTM on 2012-10-06
Yeah, you got it right. Xpra is meant to run regular apps, not full WMs. What you need is some sort of shell to launch your apps, something not too tied to a given DE. Maybe a dock like Docky or Cairo, or the tint2 panel.

For a lightweight remote desktop solution (where you see the entire desktop) I'd recommend [X2Go]("http://www.x2go.org"). That should be able to run BlackBox remotely.

---

