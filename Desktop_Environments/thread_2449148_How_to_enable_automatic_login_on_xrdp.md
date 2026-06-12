---
title: "How to enable automatic login on xrdp"
date: 2020-08-20
forum: Desktop Environments
---

### Post by nitishraja on 2020-08-20
We are using ubuntu 16.04+xfce4. I am not able to enable automatic login for xrdp.
Tried all possible ways of modifying the lightdm.confg file.

For reference 
[https://askubuntu.com/questions/530072/how-to-auto-login-in-xubuntu](https://askubuntu.com/questions/530072/how-to-auto-login-in-xubuntu)

Please suggest .

---

### Post by TheFu on 2020-08-21
Don't use xrdp. Use **x2go** with ssh-keys for authentication.

---

### Post by ActionParsnip on 2020-08-21
What are you doing on the remote system that needs the full desktop? There may be a sleeker solution to what you are trying to do

---

### Post by TheFu on 2020-08-21
> **ActionParsnip said:**
> What are you doing on the remote system that needs the full desktop? There may be a sleeker solution to what you are trying to do

Agreed.  Most definitely.  Remote X11 works well on a LAN, assuming a shell script over ssh doesn't handle everything.

---

### Post by nitishraja on 2020-08-23
We are migrating a Robotic Project from On-premise to Cloud that's why need xrdp.
Robotic Simulator need a xrdp session always, so once the server rebooted there is no existing session and hence all test case fail.
x2go need server client setup. Any other suggestion.

---

### Post by TheFu on 2020-08-23
Use ssh tunnel. Force vncserver to only accept localhost connections.
Connect from client to server using ssh, then connect via vnc through that tunnel. automate using a script.
Many guides for doing this that google finds.
[https://www.techrepublic.com/article/how-to-connect-to-vnc-using-ssh/](https://www.techrepublic.com/article/how-to-connect-to-vnc-using-ssh/) is one.

rdp is for Windows connections, not Linux.

---

