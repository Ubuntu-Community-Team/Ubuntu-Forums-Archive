---
title: "VNC: Desktop sharing and multiple TTYs"
date: 2016-03-21
forum: Desktop Environments
---

### Post by petwri on 2016-03-21
I am trying to connect to my running ubuntu server using vino. I have two running ttys, one with a plain xserver, the other one has a unity session. From within that unity session, I start the desktop remote server.

So far so good, I can connect, and the current unity session pops up on the VNC client. When I change to the other terminal on the server, the remote connection freezes and doesn't seem to work anymore. Also, when I am on the xserver terminal, a connection to the server is possible, but only shows a blank screen. Changing the the unity tty gets the remote connection to work again.

So, question: does vino only support one TTY? If yes, is there a workaround?

---

### Post by gordintoronto on 2016-03-22
What VNC client?

I don't know, but it makes sense to me that if you start the remote server from within Unity, it will only serve the Unity session.

I've set up remote desktop hosted by Xubuntu, but that was a much easier configuration than what you are trying to do.

---

