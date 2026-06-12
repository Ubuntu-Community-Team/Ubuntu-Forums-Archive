---
title: "export windows desktop to ubuntu x server"
date: 2009-01-20
forum: Desktop Environments
---

### Post by linezfanatix on 2009-01-20
Hi,

I am relatively new to the Ubuntu family. I dont if this question has been asked earlier or not. What I really want to do is run some program in my windows xp machine (some kind of x-server or client) and export my windows desktop to my ubuntu x server.

There are couple of questions here.
first and fore most is there any such program for windows xp to export the display. I know for sure there are windows based x server which can be used to export display from *nix based system.
If there is such a program what additional stuff would i be needing to configure the X server running on my ubuntu box to be able to capture my windows xp screen.

Any help with be highly appreciated.
~ Amit

---

### Post by oaqster on 2009-01-20
not sure if i fully understand what you mean by "exporting" your xp desktop/display.  if what your trying to do is control your xp machine from the ubuntu one, there are a couple of solutions.

if you have XP Pro it would come with something called Remote Desktop, right click on My Computer -> Properties -> Remote and enable Remote Desktop.  there are quite a few packages will let you connect to a windows RD, i personally like gnome-rdp, cuz it lets me add vnc & rd connections in the same application, to install run this

sudo apt-get install gnome-rdp

and launch Applications -> Internet -> Gnome-RDP, provide your connection information and you should be good to go.

if you have XP Home then you could try installing a VNS server on the xp machine and connect from ubuntu using a VNC client

hope this is what you were looking for
- oaqster

---

### Post by ugm6hr on 2009-01-20
> **linezfanatix said:**
> I know for sure there are windows based x server which can be used to export display from *nix based system.

This terminology is unclear.  As oaqster says - you may be talking about remote desktop software.

To clarify, let us know some examples of the Windows software that you know exists.

---

### Post by linezfanatix on 2009-01-20
Thanks oaqster,

I think i kind of understand now that windows does not have the concept of so called X server. What I ended up doing is to install tightVNC server on my windows XP box and use the client to hook into my xp machine.

Thanks for your help.

---

### Post by linezfanatix on 2009-01-20
> **ugm6hr said:**
> This terminology is unclear.  As oaqster says - you may be talking about remote desktop software.

To clarify, let us know some examples of the Windows software that you know exists.

Sorry for loosely using jargons. Xming is one of the software I know, which can be installed on windows and you can hook ur linux based x clients to it.

---

