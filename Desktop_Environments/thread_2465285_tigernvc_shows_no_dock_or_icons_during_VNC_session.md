---
title: "tigernvc shows no dock or icons during VNC session"
date: 2021-07-28
forum: Desktop Environments
---

### Post by roper12345 on 2021-07-28
I am running GNOME on Ubuntu 20.04. When I initiate a VNC session, I can see my desktop as well as the top menu bar, but my dock and all of my icons are gone. This only seems to be happening when accessing my desktop over the internet as opposed to my local network, but I could be wrong. Any ideas what the problem might be? I have checked to make sure the full window is being shown in my client.

---

### Post by ActionParsnip on 2021-07-28
I hope you are using an SSH tunnel then connecting using that. VNC is not encrypted and not secure.
What are you doing on the remote system once you get connected? What are you connecting to the remote system to achieve? There may be a sleeker solution to what you want to do

---

### Post by roper12345 on 2021-07-29
Yes, I am tunneling through SSH. I am just trying to use tigervnc as a remote desktop solution.

---

### Post by robert48 on 2021-07-30
Hello
May I listen in please? I want to remotely connect to and control, with user consent, Ubuntu machines that I build for them. I am looking for the best server/client solution.

I have found a source of latest problems with TigerVNC on [https://github.com/TigerVNC/tigervnc/labels/bounty](https://github.com/TigerVNC/tigervnc/labels/bounty)

You might also try [https://remmina.org/how-to-install-remmina/#ubuntu](https://remmina.org/how-to-install-remmina/#ubuntu)

I have had some success with remmina over a LAN but currently untried over WAN.

---

### Post by ActionParsnip on 2021-07-30
> **roper12345 said:**
> Yes, I am tunneling through SSH. I am just trying to use tigervnc as a remote desktop solution.

Yes, but to achieve what? Lets say you get connected to the desktop OS...what are you gong to do on the desktop?

---

### Post by roper12345 on 2021-07-30
Sorry, I'm not sure why that's relevant to my question.

---

### Post by roper12345 on 2021-07-30
In any case, the easier solution was to enable screen sharing directly in Ubuntu settings -> sharing. I also had to disable encryption in dconf (there is a known bug) and turn off scaling and lower my resolution to 1080p (another known bug).

---

### Post by ActionParsnip on 2021-07-31
> **roper12345 said:**
> Sorry, I'm not sure why that's relevant to my question.

Because people immediately start grabbing at VNC as soon as they start getting the idea about remote access. A lot of the time there is no need for VNC. 

As an example, one guy was VNCing to the remote system to then open a Web browser to [http://localhost](http://localhost)

Another just watched an SSH connection but was wanting to VNC over to open a terminal....

Stuff like that, so I always always ask.

Why do you need to connect to and access the full desktop? If there is a better solution then you don't even need to setup or run VNC because a better solution exists.

---

### Post by robert48 on 2021-08-01
My basic requirement is to assist and maintain a Ubuntu installation on a remote PC, accessible over the internet. I have built the machine for my wife's cousin at the tender age of 21 for the 36th year. The idea is to show him how to do things when he and the machine are 200 miles away.

---

### Post by ActionParsnip on 2021-08-02
> **robert48 said:**
> My basic requirement is to assist and maintain a Ubuntu installation on a remote PC, accessible over the internet. I have built the machine for my wife's cousin at the tender age of 21 for the 36th year. The idea is to show him how to do things when he and the machine are 200 miles away.

Ahh remote desktop assistance with the user sat at the system. Is this the requirement? If. So then VNC is a great solution here.

---

### Post by robert48 on 2021-08-02
Thanks, how do I make VNC secure over the Internet? I have used VNC with the Remmina client over a LAN. Is there a better client to use? Both client and server machines are AMD64 20.04 LTS. I have allowed sharing on the server machine but not added any other networking tools than those standard with a new installation. I have Remmina on the client machine.

Also found this for others following:- [https://askubuntu.com/questions/438002/best-vnc-remote-desktop-application](https://askubuntu.com/questions/438002/best-vnc-remote-desktop-application)

---

### Post by ActionParsnip on 2021-08-02
This shows how to SSH to the VNC port which then secures it.
[https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-vnc-on-ubuntu-16-04](https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-vnc-on-ubuntu-16-04)

You will need to port forward 22/TCP from outside to the internal system. I recommend using SSH keys as the only authentication method and use fail2ban

---

