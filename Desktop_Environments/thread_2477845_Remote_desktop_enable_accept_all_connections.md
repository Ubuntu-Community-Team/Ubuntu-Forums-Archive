---
title: "Remote desktop enable accept all connections"
date: 2022-08-08
forum: Desktop Environments
---

### Post by yuri-weinstein on 2022-08-08
Hello

I enabled remote desktop access on 22.04 but when I try to connect from a VNC/remmina client I see on the desktop "Accept" prompt

How can I enable   accept all connections by default?

Thx

---

### Post by ActionParsnip on 2022-08-08
How did you setup the remote desktop?

What are you wanting to do on the remote system that needs the full desktop session? There may be a sleeker solution to what you want to achieve

---

### Post by yuri-weinstein on 2022-08-08
> **ActionParsnip said:**
> How did you setup the remote desktop?

What are you wanting to do on the remote system that needs the full desktop session? There may be a sleeker solution to what you want to achieve

I did not do anything fancy - enabled remote desktop via settings.

I was hoping to avoid installing any other packages (x11 etc) as I do have this working fine on 20.04, but 22.04 adds more security I guess.

I just want to do a full desktop connection on as needed basis.

Thx for the reply.

---

### Post by ActionParsnip on 2022-08-08
[https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-vnc-on-ubuntu-22-04](https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-vnc-on-ubuntu-22-04)

Digital Ocean do fab guides.

Yes you will have a desktop remotely accessible but what will you do when you connect to the desktop? Why bother?

---

### Post by yuri-weinstein on 2022-08-08
> **ActionParsnip said:**
> [https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-vnc-on-ubuntu-22-04](https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-vnc-on-ubuntu-22-04)

Digital Ocean do fab guides.

Yes you will have a desktop remotely accessible but what will you do when you connect to the desktop? Why bother?

So the answer is that the remote desktop installed by Ubuntu does not have an option to enable all connections by default? 
(it's hard to belive)

As I said I'd like to avoid installing any new packages if possible.


 Why bother?  - I guess I am old-fashioned, just of habits :)

---

### Post by ActionParsnip on 2022-08-08
Not sure. I just know of the guide. Microsoft have one for xrdp too
[https://docs.microsoft.com/en-us/azure/virtual-machines/linux/use-remote-desktop?tabs=azure-cli](https://docs.microsoft.com/en-us/azure/virtual-machines/linux/use-remote-desktop?tabs=azure-cli)

But I'm betting that there is a better solution to what you want to do than logging in to the remote desktop. File management (for example) can be done via SSHFS and mapped to a drive, or Samba installed and a location shared. Updates can be installed using SSH too..... So... What are you wanting to do on the remote system once you connect using VNC / RDP?

---

### Post by yuri-weinstein on 2022-08-08
> **ActionParsnip said:**
> Not sure. I just know of the guide. Microsoft have one for xrdp too
[https://docs.microsoft.com/en-us/azure/virtual-machines/linux/use-remote-desktop?tabs=azure-cli](https://docs.microsoft.com/en-us/azure/virtual-machines/linux/use-remote-desktop?tabs=azure-cli)

But I'm betting that there is a better solution to what you want to do than logging in to the remote desktop. File management (for example) can be done via SSHFS and mapped to a drive, or Samba installed and a location shared. Updates can be installed using SSH too..... So... What are you wanting to do on the remote system once you connect using VNC / RDP?


Thx

Usually I keep my work desktop on and if i need to see some IRC messages or similar it's easier to do via RD, that's all, in one word avoiding pain setting up all VPN connections

---

### Post by ActionParsnip on 2022-08-08
OK, how do you see these IRC messages? What application do you use?

---

### Post by yuri-weinstein on 2022-08-08
> **ActionParsnip said:**
> OK, how do you see these IRC messages? What application do you use?


Pidgin

---

### Post by ActionParsnip on 2022-08-08
Great app. Are you launching pidgin to use IRC or do you have pidgin running all the time and you jump back in to the conversations?

---

