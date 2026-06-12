---
title: "ubuntu server problem"
date: 2009-02-07
forum: General Help
---

### Post by meinvateristnein on 2009-02-07
ubuntu server is runnning painfully slow!!!! i think my eyes might bleed if i look at the download speed again.,... i know this is |NOT my internet because i download at 1.5 mb per sec online but the second i try to download and install anything from the terminal or add/remove or synaptics it goes a painful to watch max. 34kbs now i need to download large fiules i mean 4-5 gb each and i dont want to wait 5 years to do it is there anyhope of making it go faster ...... is it a software / ubuntu problem or is it just that the servers are getting raped??? .... i dont think its that one because nothing that good could possibly have come out.;

---

### Post by madverb on 2009-02-07
Use a different mirror?

---

### Post by meinvateristnein on 2009-02-07
how is that possible .??? i am donwloading form ubuntu servers........ not form the internet .................. i cant get these files from the internet.......... only from ubuntu servers

---

### Post by madverb on 2009-02-07
Pardon?

---

### Post by meinvateristnein on 2009-02-07
i am using ubuntu software to download files / updates / programs / every program i need . i can not get "another mirror" becuase there is only one mirror which is ubuntu server

---

### Post by mb_webguy on 2009-02-07
Actually, there are dozens of mirrors for the Ubuntu servers.  Switching mirrors is easy in Gnome, but I don't know how you'd go about doing it on an Ubuntu server.  Or rather, I know how to change your mirror, but I don't know how to determine which mirror would be the best for you.

If knew roughly where in the world you're located, I could pick one close to you and tell you how to switch to it.

---

### Post by meinvateristnein on 2009-02-07
Canada

---

### Post by mb_webguy on 2009-02-07
Ok, here's what to do.  Open your sources list with the command "sudo nano /etc/apt/sources.list".

Change each instance of "http://archive.ubuntu.com/ubuntu/" to one of the following:

[ftp://ftp.cs.mun.ca/](ftp://ftp.cs.mun.ca/)
[http://gpl.savoirfairelinux.net/](http://gpl.savoirfairelinux.net/)
[http://gulus.usherbrooke.ca/](http://gulus.usherbrooke.ca/)
[http://mirror.arcticnetwork.ca/](http://mirror.arcticnetwork.ca/)
[http://mirror.cpsc.ucalgary.ca/](http://mirror.cpsc.ucalgary.ca/)
[http://mirror.csclub.uwaterloo.ca/](http://mirror.csclub.uwaterloo.ca/)
[http://ubuntu.mirror.rafal.ca/](http://ubuntu.mirror.rafal.ca/)

Save the file, then exit the editor.  Now update your sources with "sudo apt-get update".  If this doesn't increase your speed for installing packages, try one of the other mirrors.

---

### Post by meinvateristnein on 2009-02-07
OMFG thanks so much it worked like a charm...... back up to 1.5 mbs

---

### Post by mb_webguy on 2009-02-08
Glad I could help. :)

---

