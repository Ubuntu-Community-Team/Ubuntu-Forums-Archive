---
title: "XDMCP with Xubuntu - help needed"
date: 2011-07-09
forum: Desktop Environments
---

### Post by davre1 on 2011-07-09
I am trying to setup remote desktop access to a headless linux box running Xubuntu (11.04 Natty) from a windows pc. Found some good tutorials on the web and was thinking of using Cygwin or Xming on client. 
 
I need to be able to initate a remote desktop on the server to perform admin tasks when nobody is currently logged in. I think I can do this using XDMCP is that correct?
 
Tutorials I have found indicate that in the gdm custom.conf file under [daemon] I should set RemoteGreeter=/usr/lib/gdm/gdmlogin
 
but in my /usr/lib/gdm directory there is no gdmlogin file so I am stuck! Is this because I am using Xfce desktop? What should RemoteGreeter be set to?
 
Any help appreciated (newbie)
 
Xbuntu 11.04 Natty
Xfce 4.8.0
GDM 2.32.1

---

