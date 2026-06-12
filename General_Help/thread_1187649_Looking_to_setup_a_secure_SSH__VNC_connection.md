---
title: "Looking to setup a secure SSH / VNC connection"
date: 2009-06-14
forum: General Help
---

### Post by maxxum on 2009-06-14
I have two machines at work. One is my general purpose desktop, running Ibex (call it U904). Another is a workstation (call it WS) that needs to run XP x64 in order to run a proprietary scientific software. I would like to occasionally look into these machines from outside, say home. I could put a VNC server and use Terminal from home to see the U904 machine but I wonder how secure it is. The WS machine is not visible to the outside world but U904 can see it in the local network (and from U904, I can see its screen as it runs UltraVNC server on XP).
 
What I want: Log on to U904 from home, turn on a VNC server, log on to the VNC server and view U904's screen. Then if I need, I can look into the WS through U904. Then I want to be able to turn off the VNC server when I am done. 
Can someone guide me in a noob-friendly manner regarding 
1) how to setup a SSH server on U904.
2) Choose the best VNC server for U904 and how to turn it on and off.
3) Any other precautions.

Thanks. :o

---

### Post by blueridgedog on 2009-06-14
Ideally you should break this into two parts.  One is getting ssh to work on the Linux system.

I would start here:

[https://help.ubuntu.com/community/SSH?action=show&redirect=SSHHowto](https://help.ubuntu.com/community/SSH?action=show&redirect=SSHHowto)

Once installed and working (ie you can ssh into the system), then you can tunnel VNC as described here:

[https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)

Since the only (theoretically) port open to the Linux system will be ssh, the standard vnc that comes with Ubuntu will be fine.

---

### Post by Scotty Bones on 2009-06-14
I'm not trying to be rude here or anything, BUT (just a standard warning)...
You might want to check with your IT department or a supervisor first, just to ensure that you have authorization to do what you are attempting. If the business you work for has a dedicated IT department, they should be the ones setting this up (if authorized), as ultimately they are responsible for the performance, reliability and security of the network.

If I discovered an employee attempting to do what you are, without my authorization....no warning, no suspension, straight to termination.

---

### Post by maxxum on 2009-06-14
Thanks blueridgedog. I will try those things and report back. Scotty Bones, I appreciate your concern but this is just a lab in a university and my professor is only happy if my productivity increases if I can periodically check on my simulations at night or when on vacation etc.
This is no high security top secret stuff! :D But having said that, I wouldn't want to leave a VNC server running unsupervised for any capable one to hack into.

---

