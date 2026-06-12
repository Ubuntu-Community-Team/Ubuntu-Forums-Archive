---
title: "NXClient - How to continue with local session?"
date: 2006-08-30
forum: Desktop Environments
---

### Post by pimpaulogy on 2006-08-30
I have installed NXClient and server and everything is running fine.  However, I would like to be able to continue with the session that was running when I was sitting in front of the remote box.  Basically, I use the box at home, and have some apps open that I am using.  I then leave and go to work.  I want to be able to log into that box and continue working with those apps as if I were still at home.  Right now, I log in, using NXClient, with the same user name and password, and I get my desktop setup, but none of the apps are visibly open.  In addition, for example, it knows I had firefox open already because it tells me there is already one instance of firefox running and I should close that before running another.

Hopefully there is a short answer to my long question.

---

### Post by mpx on 2006-09-10
bump..

I face the same problem. It is really annoying and it defeats the idea of seamless remote connections. Any ideas?

---

### Post by crazymonkey on 2006-09-10
The only way i have been able to use NXClient to connect to my opened session was by using VNC instead of Unix/Gnome in the client settings and having the remote desktop activated with a password on my machine.

It pass the VNC connection through the ssh tunnel. The results are not amazing (really lagging) but it allows me to do basic things on my opened session (closing Firefox to allow me to have it open on my NX session for example) and you can use both protocol at the same time.

Hope this helps.

---

### Post by mpx on 2006-09-11
crazymonkey, could you shed more light on how to use VNC instead of  Unix/Gnome in the client settings?  Do you mean to use VNC seperately (independent of NX) to close Firefox, etc, or you do this via NX?

---

### Post by crazymonkey on 2006-09-11
> **mpx said:**
> crazymonkey, could you shed more light on how to use VNC instead of  Unix/Gnome in the client settings?  Do you mean to use VNC seperately (independent of NX) to close Firefox, etc, or you do this via NX?

I'm using VNC trough the NX client, the main advantage to this is that NXClient route all traffic trough the ssh tunnel which gives some security.

In the NXClient choose VNC in the desktop section and open the Settings window to enter the connections details... Host address should be the same as the server address in the previous window and the screen should be 0. 
ie: 192.168.11.11 : 0

When you connect this session NX will make a ssh tunnel to you computer and then connect to vncserver trough ssh and you will have your current session in NX.

I have yet to experiment with the other NXClient Desktop setting but i think the Unix > Custom setting might be the solution to see the opened session without using VNC.

---

