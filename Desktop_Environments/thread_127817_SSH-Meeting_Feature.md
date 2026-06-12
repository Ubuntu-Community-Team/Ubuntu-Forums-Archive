---
title: "SSH-Meeting Feature"
date: 2006-02-09
forum: Desktop Environments
---

### Post by SuperMike on 2006-02-09
If this feature doesn't exist yet, or SourceForge doesn't have a project, I think it would be like mega cool to have.

You know Microsoft NetMeeting? With that, even though my company has a very tight firewall, I'm able to provide vendor tech support with a way to take control of my server while I watch (and speak to them on the phone). My vendor can then fix my Microsoft server or hardware issue before my eyes. I've even used the technique  in combination with Putty in order to give a Linux vendor access to a Linux server.

I was wondering, without VPN, across the Internet, is there a way I can do the same thing but on Linux and with the command line only, providing a remote console experience for a technician? (Call this SSH-Meeting, for instance.)

The way the NetMeeting thing works is that it goes through the firewall and uploads screen, mouse, mousepointer, and keyboard data to a remote server on the Internet. Likewise, the technician logins to this remote server on the Internet and sends his mouse and keyboard data to it. The data is then passed down through my firewall to my local server, where my client app processes it and returns data back to the remote server and then on to him. Even though he and I have subnets and firewalls, I'm able to give him the helm.

It would just be nice to be able to hand over the Linux command console helm in this same way to a technician, provided I was on the phone live with him, could see what he was typing, and could stop it at any time.

---

### Post by Akita on 2006-02-09
Maybe I don't understand what you're asking but... SSH already does forwarding. So you can go from your workstation to SSH on a server and out to a workstation from there. For instance, I have port 22 on my router forwarded to my Linux server (running SSH). I can hit my router from outside and have SSH on my server connect me to any workstation in my house. FYI you can tunnel and forward anything that's a TCP connection, so it works for Windows shares (use Simon Tatham's PuTTY on the 'Doze side) and what-not.

---

### Post by cwaldbieser on 2006-02-10
[QUOTE=SuperMike]If this feature doesn't exist yet, or SourceForge doesn't have a project, I think it would be like mega cool to have.

You know Microsoft NetMeeting? With that, even though my company has a very tight firewall, I'm able to provide vendor tech support with a way to take control of my server while I watch (and speak to them on the phone). My vendor can then fix my Microsoft server or hardware issue before my eyes. I've even used the technique  in combination with Putty in order to give a Linux vendor access to a Linux server.

I was wondering, without VPN, across the Internet, is there a way I can do the same thing but on Linux and with the command line only, providing a remote console experience for a technician? (Call this SSH-Meeting, for instance.)

The way the NetMeeting thing works is that it goes through the firewall and uploads screen, mouse, mousepointer, and keyboard data to a remote server on the Internet. Likewise, the technician logins to this remote server on the Internet and sends his mouse and keyboard data to it. The data is then passed down through my firewall to my local server, where my client app processes it and returns data back to the remote server and then on to him. Even though he and I have subnets and firewalls, I'm able to give him the helm.

It would just be nice to be able to hand over the Linux command console helm in this same way to a technician, provided I was on the phone live with him, could see what he was typing, and could stop it at any time.[/QUOTE]

You can do this after a fashion, with the "linuxvnc" package in the repositories in conjunction with ssh.  linuxvnc essentially exports a tty as a vnc session.  So you could run it from a terminal, and someone outside should be able to ssh in and port-forward the appropriate port (usually 5900).  They will get your terminal in their vnc viewer, and you can see what they type and visa versa.

---

