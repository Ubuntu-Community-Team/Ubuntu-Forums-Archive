---
title: "Multiple VNC to one server?"
date: 2009-02-26
forum: General Help
---

### Post by philip142au on 2009-02-26
Hi,

Is it possible to have multiple clients VNC to a single server and each client sees a different screen - their own screen and desktop.
If client disconnects, they can resume their desktop?

Why I want to do this is that it seems like a good idea for a group of us friends, we have many old computers, we wanted one powerful central computer which we could VNC to do programming. Since the whole network is local here in the room, we just buy one powerful computer and install java and a IDE on there and we could all VNC to it.

Rather than throwing out the old computers, use them as "terminals" to the central computer which has a lot of GIG of ram and disk and speed.
(A green idea, and save money too)

Any suggestions or ideas about this?

Thanks! Phil

---

### Post by Peter09 on 2009-02-26
Your best bet would be to use NXFree as it allows you to login to the server and establish a Desktop.

Here is the site

[http://www.nomachine.com/download.php](http://www.nomachine.com/download.php)

How many of you a single machine could support at once is interesting....

---

### Post by philip142au on 2009-02-26
A corei7 with 12gb of ram might handle a few of us.
What do you think?

Honestly its cheaper than giving everyone a new pc.

---

### Post by Peter09 on 2009-02-26
Yes,
obviously it does depend on what you are doing but its worth a try. Download the FreenX packages. You need to install openssh-server on the server as NX uses it as a secure transport protocol.

Install the NX client on the client and all three packages (client, node, and server) on the server. After that it should work.

If you open the ssh port on your internet router you'll get a very good desktop across the internet as well. Make sure you all use secure passwords on the server.

---

### Post by philip142au on 2009-02-26
Just Java programming in an IDE, Eclipse.

The idea to support 3 of us- we use second hand computers to work on that computer. It seems cheaper than 3 of us all getting 2 or 4 gb ram and high end machines.
Also we can use the machine as a server - if we are crazy enough to do so.

---

### Post by Peter09 on 2009-02-26
Yes, seems a good idea. Have you had a chance to install any of the packages?

---

