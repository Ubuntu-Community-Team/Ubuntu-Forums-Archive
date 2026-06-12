---
title: "VNC Server Authentication Problems"
date: 2006-05-18
forum: Desktop Environments
---

### Post by dflek on 2006-05-18
Hi,

I am having trouble authenticating  a vnc viewer session from a Windows client. The connection works OK, but every time I connect a message pops up on the screen of the Ubuntu box saying "Another user is trying to view you desktop" and asks for the connection to be allowed / refused. This is not so good for me, as I would like to be able to access the box over a VPN (will be trying to set up Mambo CMS this weekend).

I am running a pretty standard install of Ubu, however for some reason I have no /etc/vnc directory. My ~/.vnc/config looks like:

[I]UserPasswdVerifier=UnixAuth
AllowedUsers=$USER:f[/I]

I  have talked to a support guy at TightVNC and he told me to make sure QueryConnect is disabled, but I can't find where to do this. 

I know that this is probably posted somewhere already, but I have been struggling to find any info.

Any help would be greatly appreciated.

---

### Post by Sniffer on 2006-05-18
Sorry for the question...

But on ubuntu - remote desktop do you have require autorization enabled...

I have VNC working on mine just perfectly..only ask me for the password i have defined on remote desktop.

Sniff.

---

### Post by dflek on 2006-05-18
Thanks mate.... I'm an idiot.

Have got it sorted now.

---

