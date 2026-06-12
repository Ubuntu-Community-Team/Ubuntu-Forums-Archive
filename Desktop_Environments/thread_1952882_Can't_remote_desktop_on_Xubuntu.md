---
title: "Can't remote desktop on Xubuntu"
date: 2012-04-05
forum: Desktop Environments
---

### Post by Azyx on 2012-04-05
Hi.
I'm trying to learn how Xubuntu work, but I cannot get any working remote-desktop to my Xubuntu machine. 
 I have Ubuntu 64bit i bottom, and the Lubuntu and Xubuntu. My plan is to run 12.04LTS,cand unfortually lubuntu do not have thyat. Ubuntu (Unity and Gnome3) are very slow with remote desktop from Ubuntu LTS, so I want to get Xbuntu working, But I am not able to connect thrue VNC (my locall network) When I'm logged in as Unity, Gnome3 och Lubuntu i can connct, but when I'm in Xubuntu I can not connect. The vino-preferences i Xubuntu look ok, and are the same as in Lubuntu/Ubuntu

/Cheers

---

### Post by Jose Catre-Vandis on 2012-04-05
Try this:

[http://bimma.me.uk/2010/01/31/xubuntu-904-quick-and-dirty-vnc-remote-access/](http://bimma.me.uk/2010/01/31/xubuntu-904-quick-and-dirty-vnc-remote-access/)

You might want to try Remmina as a vnc client

---

### Post by Azyx on 2012-04-06
> **Jose Catre-Vandis said:**
> Try this:

[http://bimma.me.uk/2010/01/31/xubuntu-904-quick-and-dirty-vnc-remote-access/](http://bimma.me.uk/2010/01/31/xubuntu-904-quick-and-dirty-vnc-remote-access/)

You might want to try Remmina as a vnc client

Thanks :) Worked wery well to just add:
```
/usr/lib/vino/vino-server

```
In the 'Settings'->'Settings manager'->'Session and startup' and the tab: 'Application Autostart'

Cheers and Happy Easter :)

---

### Post by DumpsterCat on 2012-04-08
Alternatively, you may not really need all the overhead of a remote desktop session.  All you may really need is a particular application, e.g. VirtualBox.  

Assuming that VirtualBox is installed on the remote host and ssh (secure shell) is installed on both, you might just try 
ssh -X -l yourUserID remoteHostIP

and, upon login 
VirtualBox &

Hope this also helps...

---

### Post by Azyx on 2012-04-08
> **DumpsterCat said:**
> Alternatively, you may not really need all the overhead of a remote desktop session.  All you may really need is a particular application, e.g. VirtualBox.  

Assuming that VirtualBox is installed on the remote host and ssh (secure shell) is installed on both, you might just try 
ssh -X -l yourUserID remoteHostIP

and, upon login 
VirtualBox &

Hope this also helps...

What is the advances of that? and how do I do? Run one ubuntu and the another in VirtualBox that I controlled by ssh???

---

### Post by Jose Catre-Vandis on 2012-04-09
It got confusing for a moment when referring to Virtualbox! What Dumpstercat means is that if you are accessing remotely from a linux machine running X and your "server" is also running X, you can ssh -X and run the application you need on your client machine as if you were on the server. For example, you could run Thunar from your server on your client. So taking Dumpstercat's example, you could run a a Virtualbox session on your client, but its all happening on the server. It's very clever :)

---

### Post by Azyx on 2012-04-11
> **DumpsterCat said:**
> Alternatively, you may not really need all the overhead of a remote desktop session.  All you may really need is a particular application, e.g. VirtualBox.  

Assuming that VirtualBox is installed on the remote host and ssh (secure shell) is installed on both, you might just try 
ssh -X -l yourUserID remoteHostIP

and, upon login 
VirtualBox &

Hope this also helps...

Ok, but I want the same desktop from remote as local. Other wise it's end up with a lot of 'desktops' running on the machine.

---

### Post by Azyx on 2012-04-11
> **Jose Catre-Vandis said:**
> It got confusing for a moment when referring to Virtualbox! What Dumpstercat means is that if you are accessing remotely from a linux machine running X and your "server" is also running X, you can ssh -X and run the application you need on your client machine as if you were on the server. For example, you could run Thunar from your server on your client. So taking Dumpstercat's example, you could run a a Virtualbox session on your client, but its all happening on the server. It's very clever :)

Ok. but I just use it for just remote, when I don't want to go to my living room ;)

---

