---
title: "How do i connect to a server using sftp in thunar?"
date: 2012-06-02
forum: Desktop Environments
---

### Post by slashwannabe94 on 2012-06-02
Hello, 

I have recently switched over to XFCE4 rather than GNOME2 and i had noticed i was unable to connect to my server and mount the filesystem like i could in nautilus using the "Connect to a server" application. Is there a feature that would allow me to do this using thunar and if not how could i install one? 

I can connect to my server via SSH in terminal and it is online. 

Thank you, 

SlashWannabe94

---

### Post by Lars Noodén on 2012-06-03
It's in the menu Go->Open Location, also reachable with Ctrl-L.  Enter the URL for the server there.  If the user on the client is different then the user on the server, you will need to specify it in the URL:

sftp://user@remotehost.example.org/

---

### Post by Jose Catre-Vandis on 2012-06-03
Also, Gigolo is the tool to use for connecting to network shares

---

