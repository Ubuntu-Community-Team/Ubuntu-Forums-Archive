---
title: "VERY STRANGE: Attempting Remote Access - Password Does Not Work"
date: 2005-08-19
forum: Desktop Environments
---

### Post by appleman77 on 2005-08-19
I've run into this issue with both Kubuntu and Ubuntu so I don't think it is desktop manager specific.

Basically I've setup my Linux laptop to access remote desktop connections using VNC with the included applets (I forgot the names).  Anyway, I am able to connect at home from a Windows box no problem and I have done it remotely as well through SSH-tunnel to an OpenSSH server on a Linux appliance (NSLU2).

I have putty running on a Windows laptop at work which is port forwarding localhost:5900 --->  Laptop IP address:5900.

I am able to connect and it asks me for the remote desktop password.  I enter that and it brings me to my screensaver screen which then asks me for my desktop login password.  

I enter that and the password does not work!  I've tried with multiple VNC clients and I get the same problem with all of them.  Very strange.  On Ubuntu I got the DENIED message and on Kubuntu I recieved the "Can't unlock session" message.

THEN I GO HOME and I try and log in with my password and it doesn't work!  I've made sure caplock and numlock are not the problem.  So then the only way I can get into the laptop is to REBOOT and then enter my login/password normally and it works.

Can anyone explain this behavior?  Does it have to do with remote desktop?  Port forwarding?  

Very confusing!

Thanks for the help in advance.

---

### Post by majikstreet on 2005-08-29
I'm not sure about your problem, but I had a similar problem:
I setup a server using the server option. Then I setup SSH to connect to it from another machine. When I connected using my password, I couldn't get in. I finally found out that when I entered the password on the server itself, it replaces the capital E's and C's with lowercase ones. This may be the case with more letters that I don't know of. I have to make those letters lowercase when I login (i could change them but I am too lazy!)

majikstreet

---

### Post by usererror on 2005-08-29
mine works great from VNC Viewer on WinXP to both my Laptop with Ubuntu and my Server with Debian.

but i have only tried that from inside my network.  i haven't tried from the outside of the firewall.  could your port forwarding not be configured correctly on your router?

---

