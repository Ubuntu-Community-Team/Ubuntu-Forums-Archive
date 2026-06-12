---
title: "Ubuntu Desktop Server Platform"
date: 2009-02-24
forum: Desktop Environments
---

### Post by RaymondBeaudoin on 2009-02-24
Hello there,

I was discussing an interesting proposal with a client of mine regarding Linux and Over-the-internet desktop systems, and as I thought on this, I realized the best place to start would be UbuntuForums, so here we go.

What I am trying to accomplish is building a fully-function Ubuntu Server /w GUI that would be able to be access anywhere in the world via internet. When accessed, you screen into the system and are presented with the Ubuntu Login screen. Upon logging in you have your full desktop just as you would if you were local.

Now, you could use some Remote Desktop like LogMeIn, but I'm looking for an installable solution not a website system.

Hope I explained it alright, I am excited to hear back from you!

Ray

---

### Post by veloce on 2009-02-24
> **RaymondBeaudoin said:**
> Hello there,

I was discussing an interesting proposal with a client of mine regarding Linux and Over-the-internet desktop systems, and as I thought on this, I realized the best place to start would be UbuntuForums, so here we go.

What I am trying to accomplish is building a fully-function Ubuntu Server /w GUI that would be able to be access anywhere in the world via internet. When accessed, you screen into the system and are presented with the Ubuntu Login screen. Upon logging in you have your full desktop just as you would if you were local.

Now, you could use some Remote Desktop like LogMeIn, but I'm looking for an installable solution not a website system.

Hope I explained it alright, I am excited to hear back from you!

Ray

xdmcp is already installed so access to your "server" via an ubuntu machine is as simple as turning it on and directing your client to the right ip address.

---

### Post by RaymondBeaudoin on 2009-02-25
> **veloce said:**
> xdmcp is already installed so access to your "server" via an ubuntu machine is as simple as turning it on and directing your client to the right ip address.

But I want to have it accessible by any system, not just other Ubuntu Users. As large as the Ubuntu Community is, there are still many with other desktops.

---

### Post by veloce on 2009-02-25
> **RaymondBeaudoin said:**
> But I want to have it accessible by any system, not just other Ubuntu Users. As large as the Ubuntu Community is, there are still many with other desktops.

There are x servers for windows available that will provide access to the ubuntu desktop.

What flavour desktop are you talking about providing? 

Or are you talking about a new generic desktop that works within a browser?

I think Windows provides this as an addon to rdp - you can access a terminal server session (and desktop) using an internet browser.  It was pretty klunky from memory.

---

### Post by RaymondBeaudoin on 2009-02-26
I'm trying to build a solution that would allow access to Ubuntu System Remotely. I was thinking over it last night and thought I might be able to just setup a VNC and create accounts that way, allowing users to login to the screen and then the system, but any other ideas?

Thanks for the replies,

Ray

---

### Post by veloce on 2009-02-26
> **RaymondBeaudoin said:**
> I'm trying to build a solution that would allow access to Ubuntu System Remotely. I was thinking over it last night and thought I might be able to just setup a VNC and create accounts that way, allowing users to login to the screen and then the system, but any other ideas?

Thanks for the replies,

Ray

Have you seen this: [http://www.powerlan-usa.com/webtermx.html](http://www.powerlan-usa.com/webtermx.html)

Now if you could provide that functionality from the ubuntu host side (rather than requiring a $250 piece of software for every machine you want to use) you'd have something really nice.  Can't find anything like that though.

---

### Post by NTolerance on 2009-02-26
[NoMachine NX](http://www.nomachine.com/select-package.php?os=linux&id=1) provides the closest thing I know of to a "Terminal Services" way of operating.  Each user uses their own account to log in, it's encrypted via SSH, and it's faster than VNC or X11 forwarding.  Client software is available for Windows, Linux, and Mac OS.  The free edition is limited to two simultaneous client connections.

---

### Post by andrea000 on 2009-02-27
I agree a linux terminal server would be the way to go i have been experimenting some with mine but still learning.I do know that you can get free vnc client software like tight vnc check the web there are a lot of free client one's out there for any os so what they run wouldn't be a problem.I think logmein is a windows only client or runs from there website in a browser but i could be wrong on that and i have only heard of NoMachine NX
but i am going to check it out now that i heard it was faster. 

good luck

XOXOXO

---

### Post by RaymondBeaudoin on 2009-03-17
Sorry for such a late reply, I have been extremely busy coming up with a gigantic project for learning linux flavors: ubuntu and debian, and it has taken a chunk of my time along with school and work. 

Everything looks great, and I was thinking the same road as the last two posters. I will have to experiment more and expand, but I must say you have all greatly excited my interest in learning even more!

---

