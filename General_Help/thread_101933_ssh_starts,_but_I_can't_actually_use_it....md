---
title: "ssh starts, but I can't actually use it..."
date: 2005-12-10
forum: General Help
---

### Post by korkow on 2005-12-10
So, I *finnaly* got ssh to start. But when I go on another computer to try and connect, it's a failure. The connection is "refused". I am SURE I'm using the right IP. I think something out there is trying to keep me from using ssh :razz: !

---

### Post by invalid on 2005-12-10
Where is this "other computer"?

If it is outside of your network, you may have something blocking access to your machine (like a cable modem or a router). If this is the case, you need to set an exception rule or some port forwarding.

Cb

---

### Post by korkow on 2005-12-10
actually, it's a computer about 5 feet away from this one. (It's my brother's). Iv'e used ssh before, so I'm  pretty sure I'm not screwing up.

---

### Post by DaMasta on 2005-12-10
By finally getting ssh to start, I'm assuming you have the daemon running? /etc/init.d/sshd start?

---

### Post by korkow on 2005-12-10
yes... thats what I was implying

---

### Post by Eleaf on 2005-12-10
I'm guessing that your computers firewall is blocking port 22 for ssh'ing correct?  Download firestarter or something and have it stop blocking ssh.  You may also need to have it stop blocking port 22 on the system you are using to ssh into your computer.  
= p

---

### Post by jrib on 2005-12-10
have you allowed connections to port 22 in your firewall?

---

