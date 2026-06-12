---
title: "setting up a box for vnc &amp; ssh only"
date: 2006-01-03
forum: General Help
---

### Post by nkoplm on 2006-01-03
so ive just installed ubuntu. The intent for the machine is to be a file server on my local network. so most of the time it will sit in a dark room monitorless and keyboarless.

i would like to set it up so that on boot, i will be able to 
- log in via VNC
- or log in via X session forwarding.

i am familliar with VNC, and would like to know just 2 things.
1 - is it possible to log in after connecting with VNC (as opposed to logging into a running user session.)
2 - how can i start VNC as a service so i dont need to manually start it every time.

X session forwarding I am much less familliar with. I dont know if this is even possible over 2 different linux OSes. As i will be connecting via a Fedora machine, this is important to know.

any information that you can help me with would be appreciated. and if i need to clarify anything, please let me know.

thanks.

---

### Post by AndyCooll on 2006-01-03
Not absolutely sure about my facts, as I'm just getting my head round these issues myself (see my ssh problem post just below this!). However...

When I log in to my file server I use xdmcp (which can operate similar to vnc or logging on to your other pc just as you would logon to the pc your sat at) as I found that you need to have  running session for vnc to operate (unless someone on these boards knows otherwise)

X session forwarding just requires ssh installed and running on each machine I think. You'll have to edit a couple of files (mentioned on these forums).

And then "ssh -X AndyCooll@serverpc" at the CLI logs you on and theoretically after that when you type the name of the app it opens on the screen in front of you. :cool:

---

