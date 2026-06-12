---
title: "Make VNC use KDE"
date: 2005-09-20
forum: Desktop Environments
---

### Post by blaha on 2005-09-20
Hello, I'm trying to setup a VNC server on my Ubuntu system. 
I use the command vncserver -gemoetry 800x600 to start the server. 
When I connect to the server with xvncviewer I get the Gnome desktop instead of the KDE desktop I'm normally using. How can I make VNC use KDE? I've already selected it as my default display manager.

---

### Post by mlomker on 2005-09-20
Have you tried using krfb?  It comes with KDE and is designed for that.

Are you logging in as yourself?  I should think that it'd take the default for the user.

---

### Post by blaha on 2005-09-21
> 
Have you tried using krfb? It comes with KDE and is designed for that.

Yes, but krfb requires me to login and create personal invitations. I like VNC better. 


> Are you logging in as yourself? I should think that it'd take the default for the user. 
I'm currently using ssh to login and start the server. What I would like to do, is to have VNC start when I boot the system and have one display ready for every user.

---

### Post by mlomker on 2005-09-21
>  start the server. What I would like to do, is to have VNC start when I boot the system and have one display ready for every user.

Ah, you want to create a terminal server.  That's a little beyond the scope of regular usage, but the general process is to start VNC with a different port number for each user.

I ran across [this how-to](http://gentoo-wiki.com/HOWTO_Xvnc_terminal_server) for Gentoo, but it should give you some ideas to look at.

---

### Post by blaha on 2005-09-21
> I ran across this how-to for Gentoo, but it should give you some ideas to look at. 
That looks complicated and I don't have xinetd. Do you think it is possible to add vncserver as a service with update-rc.d?  I'd also be interested in knowing if there are any graphical tools available for adding/removing services.

---

### Post by mlomker on 2005-09-21
> That looks complicated and I don't have xinetd.

Yeah, you'd have to download it in Synaptic.  No offense, but what you are trying to do *is* complicated.

---

### Post by taj on 2005-10-06
I would also like to connect with VNC/tightVNC and would like to see a kdm (kubuntu is what I use) login screen. Multiple users should be able to login and I had it working in Suse, but I cannot get it to work with ubuntu. I DO have xinetd installed, and I know some entries are needed in some files in the /etc directory

Could someone give a link or make a brief howto?
Thanks!

EDIT: I tried the Gentoo Howto, using kdm instead of xdm (that was not installed), but I get:
vncviewer: VNC server closed connection

---

### Post by savastux on 2005-10-06
Hi, just an Idea?
 
What if you just set you X server to respond tcp requests. 
Than you can have terminal servers, right? :confused: 
 
The only issue, is that you should do this in a LAN. Otherwise, this could be very slow...:( 
 
I've never needed to do this, but I think it's quite possible.

---

### Post by Sahtor on 2005-10-06
You could always try FreeNX

---

### Post by savastux on 2005-10-06
Yes, freeNX is very good, but what I understand, is that he needs a terminal service. So, that's why I suggest to use the X over tcp instead.
 
:c)

---

### Post by ewangr on 2005-10-06
[QUOTE=mlomker]Have you tried using krfb?  It comes with KDE and is designed for that.[/QUOTE]

Unfortunately, even in Breezy running krfb runs the CPU on the box close to 100%. SO I am also trying to figure out how to setup vncserver so that I can connect to the box and get decent response.

I gather the main problem after installing with kynaptic is to setup the startup script in the user account properly. But I haven't figured out what SHOULD be in the script to startup another KDM session.

---

