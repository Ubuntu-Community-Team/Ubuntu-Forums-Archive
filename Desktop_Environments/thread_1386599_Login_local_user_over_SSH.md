---
title: "Login local user over SSH"
date: 2010-01-20
forum: Desktop Environments
---

### Post by fdiz on 2010-01-20
I've searched the forums and can't find an answer to this so I don't know if it's possible, but I thought I'd ask anyway in case anyone has some ideas.

Here is the setup:
I have a Ubuntu box running Karmic. I also have a remote host.

I want to issue a magic packet to the Ubuntu box to have it power on by wake-on-lan (I have this part working). 

When I do this, the box loads and presents the login screen. I want to SSH into the box from the remote host while the login screen is up, and remotely login the box so a local user can use it (e.g. over SSH I would log the local user into the box). Is there a way to do this?

---

### Post by myth1914 on 2010-01-20
I don't specifically have the answer, but to satisfy curiosity, why not just have the session auto-login?

If the local user is at the machine and requires a different user session, can they not log in themselves?

---

### Post by majickmann on 2010-01-20
Ensure ssh is running specifically ssh-server.
Ensure your firewall is not blocking port 22 (ssh).
Ensure no other firewall is blocking port 22 (ssh).
Ensure your user have a valid user account on your server.

Presuming the above is true, your user should be able to ssh to your server using an ssh-client.  Depending on the remote host, one may be using OpenSSH client, putty, etc.

There are some other considerations, but for now presuming the nodes are on the same network.

Hope this helps...
:-)
--majickmann

---

### Post by fdiz on 2010-01-20
That would be the preferred option except there are multiple user accounts on the box and I need to be able to choose which one to login for the user.  The box is running scientific modeling software, and I'm trying to keep the users separate because it keeps everything more orderly (and I can reset individual users more easily).

A side goal is to allow me to establish VNC connections to the box from a windows pc. I realize there are other methods which are more efficient, but I'm used to VNC. I can't VNC into the box unless a user is logged in - so if I can SSH into the box and login to a user account, then I can VNC in and work in that user account's environment.

---

### Post by fdiz on 2010-01-20
> **majickmann said:**
> Ensure ssh is running specifically ssh-server.
Ensure your firewall is not blocking port 22 (ssh).
Ensure no other firewall is blocking port 22 (ssh).
Ensure your user have a valid user account on your server.

Presuming the above is true, your user should be able to ssh to your server using an ssh-client.  Depending on the remote host, one may be using OpenSSH client, putty, etc.

There are some other considerations, but for now presuming the nodes are on the same network.

Hope this helps...
:-)
--majickmann

I think you misunderstood my problem. I want to SSH into the Ubuntu box while I'm the remote host (I have no problem doing this - it's how I admin the box most of the time). I want to login the user sitting at the box into their account on the box so they can then use the box (e.g. they will see the login screen, I will login for them, and they will then see their desktop).

---

### Post by fdiz on 2010-01-20
I managed to find a post where the poster was trying to do what I am: [http://ubuntuforums.org/showthread.php?t=780203](http://ubuntuforums.org/showthread.php?t=780203) Unfortunately, nobody posted an answer that worked.

---

### Post by fdiz on 2010-01-21
Any ideas?

---

### Post by jennil on 2010-02-24
I have roughly the same problem. We have a simulator with about 40 computers with different users for different simulations. Sometimes all shall be logged in as the same user other times we run parallel exercises so we login different users on different computers.  
 

 The solution we have today is to modify /etc/kde4/kdm/kdmrc (we are using Kubuntu) to enable “auto login” for a particular user and then restart kdm (/etc/ini.d/kdm restart) all done by scripts that automate the process. You can probably do something similar with gdm if you are using Ubuntu. This solves the problem for us but I don't feel it's a very elegant solution. Also for us it requires us to put the password in the kdmrc file since we are using NIS and that is not very secure.

 

 So if anyone have a better solution I would also be very interested.
 

 Regards
 jennil

---

