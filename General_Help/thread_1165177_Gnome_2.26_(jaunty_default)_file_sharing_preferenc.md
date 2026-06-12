---
title: "Gnome 2.26 (jaunty default) file sharing preferences"
date: 2009-05-20
forum: General Help
---

### Post by Psychopump on 2009-05-20
Hello all,

According to [_[COLOR="Navy"]these release notes[/COLOR]_]("http://library.gnome.org/misc/release-notes/2.26/#rnusers.gnome-user-share") file sharing has been made easier in 2.26.

It should be easy to share files over LAN, HTTP and Bluetooth.
Can anyone explain to me how to share files or folders over HTTP using Gnomes built-in capabilities?

Eternal gratitude guaranteed!

):P

---

### Post by urmomsgoat on 2009-05-28
$ sudo apt-get install gnome-user-share

And then navigate to "System" > "Preferences" > "Personal File Sharing"

---

### Post by Psychopump on 2009-05-28
> **urmomsgoat said:**
> $ sudo apt-get install gnome-user-share

And then navigate to "System" > "Preferences" > "Personal File Sharing"

Thanks for your reply!
I installed gnome-user-share and it allows me to specify whether or not I want to share public folders over a network, but how do I allow a remote user (in a different country, using HTTP or FTP) to access the files?

---

### Post by rhodry on 2009-05-28
To some extent, it depends on the protocol you want to use and how secure you want to be?

gnome-user-share is described as "User level public file sharing via WebDAV or ObexFTP".

The 'traditional' way of file sharing that I learned is to set up NFS shares if all machines are Linux-based and Samba shares if there are Windows machines involved anywhere. A particular folder can operate as both an NFS share & a Samba share if necessary.

If you want to go outside the local network that is behind your router, you most definitely want a secure protocol. Scp & Sftp are secure methods of ftp transfer.

Personally I run Openssh server/client combinations across all shares and setup nfs shares within that secure environment. Works from London to Sydney ok?!! You will need to look at fixed ip addresses if connecting remotely. 

Do a search of these forums (& Google if necessary for some of the key terms mentioned here. There is a heap of useful info available. There are lots of options on this matter so you need to be quite specific about what you want to achieve in order to get specific help about how to do it.

Cheers,
Rhodry

---

