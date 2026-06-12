---
title: "New User : Question with tightvnc and BitchX"
date: 2005-10-28
forum: Desktop Environments
---

### Post by Klainn on 2005-10-28
Hello.

I recently (this morning) switched distros to Ubuntu from Gentoo. I'm used to using tightvnc to remote desktop into the linux box and BitchX to chat on IRC. My question is, when I switched distros I no longer have either piece of software it seems.

Example :

```

root@COMMAND:/# apt-cache search vnc
tsclient - front-end for viewing of remote desktops in GNOME
vino - VNC server for GNOME
vnc-common - Virtual network computing server software
xvncviewer - Virtual network computing client software for X
krdc - Remote Desktop Connection for KDE
krfb - Desktop Sharing for KDE
libvncauth-dev - Virtual network computing authentication headers and static lib
libvncauth0 - Virtual network computing authentication library

```

I tried to apt-get install vnc-common but am told it's already at the latest version installed. I still have no vncserver command to run. Basically, I just need to know what I should be looking for to start a vncserver connection as I don't seem to have the option by default, I do have vncpassword and vncviewer though.

Lastly, BitchX ... I simply can not find it with any search combo. Anyone know what it might be listed under?

Thank you for reading. I searched but didn't find a thread for either that was really all that similier to what I needed to know.

---

### Post by psychicdragon on 2005-10-28
Hi,

I just did a search for those two packages and found them both. So, it looks like you need to enable extra repositories.

Here's a HowTo from the wiki: [AddingRepositoriesHowto]("https://wiki.ubuntu.com/AddingRepositoriesHowto")

---

### Post by Klainn on 2005-10-28
Thanks a ton, I'll try that right now. I'm missing a lot of stuff that I normally use so this is likely going to be ok. Thanks again.

Edit : Does anyone know of a console way to do this? I'm away from the machine now and only have the ssh console access. Thanks.

Edit2 : I found this link that may help other newbies like me [http://www.student.dtu.dk/~s971652/update.shtml](http://www.student.dtu.dk/~s971652/update.shtml) : this showed me how to update the repository without being on the box itself.

---

