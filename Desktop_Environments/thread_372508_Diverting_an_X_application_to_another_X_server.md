---
title: "Diverting an X application to another X server"
date: 2007-02-28
forum: Desktop Environments
---

### Post by hartz on 2007-02-28
Hi,
I work with a lot of X-Windows apps runnign on servers, having their display connected to the X-server on my workstation.

Sometimes I wish I could "move" the display to another X-server.

Example

login to remote server.
set DISPLAY=my-ip-addr:0.0
start x-client
work on client app
Decide that it would have been better if I had the display set to another machine in my cubicle
run some command which causes the display to be replicated onto another X-server and then remove the connection to my current X-server.

In the above situation, after moving the display to the "other" x-server, there must be no dependency left on the initial X-server.  Is there some software to enable this?  Maybe an X-proxy that I can run on the remote machine, so that the DISPLAY is initially set to connect to the proxy (local), which forwards the x-requests to my workstation, and then can take a command to switch it to send that client's x-requests (x-session) to another x-server on the network?

A related situation is where I run an app on the server's directly attached display, and then decide I want to have that display diverted to my workstation across the network.  Most often this is for xterm sessions with long-running commands.

If I could get the "screen" command, but for the X-traffic, that would be more-or-less what I am thinking of!  Only, it needs to do more than just pseudo-terminal IO.

Thanx.

---

### Post by milton1 on 2007-02-28
you could just use x-forwarding in ssh

ssh -X you@yourserver

---

### Post by hartz on 2007-03-05
Hello milton1,

I regularly use x-forwarding, in particular to do server-hopping.  I am not aware of how this can be used to move an application's existing window from begin displayed on one x-server to another, while the applicaiton is running.  Can you please explain more?

I am starting to believe that it is not possible to do what I need.

Thanx!

---

### Post by milton1 on 2007-03-05
Sorry, moving an existing window without terminating the application is beyond my knowledge, if it is possible. I misread your original post.

---

### Post by hartz on 2007-03-12
No problem. :)

---

### Post by zero-9376 on 2008-01-07
for anyone interested and my own reference you may want to look at an application called xmove to allow moving the app from one x to another

---

