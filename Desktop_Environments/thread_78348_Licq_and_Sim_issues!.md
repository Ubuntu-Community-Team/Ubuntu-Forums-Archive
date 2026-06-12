---
title: "Licq and Sim issues!"
date: 2005-10-18
forum: Desktop Environments
---

### Post by Pumpino on 2005-10-18
In Hoary and Breezy (Kubuntu), Sim appears to crash when receiving messages from people using the latest Windows version of ICQ!

In Breezy (Kubuntu), Licq refuses to go online when I start it!  I select "Online", but nothing happens.

Between the two of these playing up, I'm tempted to investigate Kopete and Gaim, but I really didn't like them when I tried them a couple of months ago.

Can anyone confirm these issues and suggest solutions?  I've removed Licq (including the /home/username/.licq dir) and reinstalled it, but it didn't help.

---

### Post by Pumpino on 2005-10-18
This is what the Licq network shows:

08:03:36: [SRV] Requesting logon (#28090)...
08:03:36: [SRV] Connecting to login server.
08:03:36: [SRV] Resolving login.icq.com port 5190...
08:03:36: [SRV] ICQ server found at 64.12.161.153:5190.
08:03:36: [SRV] Opening socket to server.
08:03:37: [WRN] error during receiving from server socket :-((
                Connection reset by peer
08:03:37: [SRV] Dropping server connection.

Any ideas?  Thanks. :)

---

### Post by avb on 2005-10-18
[QUOTE=Pumpino]This is what the Licq network shows:

08:03:36: [SRV] Requesting logon (#28090)...
08:03:36: [SRV] Connecting to login server.
08:03:36: [SRV] Resolving login.icq.com port 5190...
08:03:36: [SRV] ICQ server found at 64.12.161.153:5190.
08:03:36: [SRV] Opening socket to server.
08:03:37: [WRN] error during receiving from server socket :-((
                Connection reset by peer
08:03:37: [SRV] Dropping server connection.

Any ideas?  Thanks. :)[/QUOTE]

yeh, the same problem.

download licq cvs snapshot from my kubuntu repo. 
visit [http://avb.bas-net.by/ubuntu/](http://avb.bas-net.by/ubuntu/) for more information.

---

### Post by Pumpino on 2005-10-19
I installed licq3 after adding that repository.  However, I get the following error:

$ licq
18:48:03: [ERR] Unable to load plugin (qt-gui): /usr/lib/licq/licq_qt-gui.so: cannot open shared object file: No such file or directory.

---

### Post by Pumpino on 2005-10-19
I just spotted alicq in Synaptic.  Never heard of it before, but I downloaded it and it's quite a nice, yet simply client.  Anyone else use it?  aMSN rocks, so I suppose it's natural that alicq would be good too. ;)

EDIT:  Just found the obvious flaw.  It doesn't allow you to minimise it to just a system tray icon. :(  Will have to stick with Licq if I can get it to run!

---

### Post by Pumpino on 2005-10-19
For your info, the Licq error isn't an issue with the Ubuntu DEB.  I uninstalled the Ubuntu DEB, deleted the /home/username/.licq dir, and then downloaded Licq from Debian Sid.  Same problem!  Seems to be a Kubuntu (or maybe Ubuntu) issue. :(  Again, I wish the Kubuntu developers would try running the popular programs like Licq and Kaffeine, cause it's so obvious that they don't work for anyone! :P

---

### Post by avb on 2005-10-20
[QUOTE=Pumpino]I installed licq3 after adding that repository.  However, I get the following error:

$ licq
18:48:03: [ERR] Unable to load plugin (qt-gui): /usr/lib/licq/licq_qt-gui.so: cannot open shared object file: No such file or directory.[/QUOTE]

run:

sudo ln -s /usr/lib/licq/licq_kde-gui.so /usr/lib/licq/licq_qt-gui.so
sudo ln -s /usr/lib/licq/licq_kde-gui.la /usr/lib/licq/licq_qt-gui.la

than run licq again.

Alex

---

### Post by Pumpino on 2005-10-20
Wahoo!  It works. :)  Thanks.  It's better than the version that comes with Ubuntu, too.

So you built the package yourself?  What's involved in building your own deb?

What does the licq3-msn package do?

---

