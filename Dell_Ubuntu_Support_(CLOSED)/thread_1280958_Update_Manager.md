---
title: "Update Manager"
date: 2009-10-02
forum: Dell Ubuntu Support (CLOSED)
---

### Post by jwaclawsky on 2009-10-02
I have been using Update Manager with my mini 9 net-book running 9.04. It has always worked fine. However whne updating my system this time I have warning message: 

"You are about to install software that can't be authenticated! Doing this can allow a malicious individual to damage or take control of your system" 

Does anyone know if there are any issues associated with update manager or any of the updates or know why I am getting this message. The list of updates (29 packages) that update manage wants to install are: 

apport (version 1.0-0ubuntu5.2) will be upgraded to version 1.0-0ubuntu5.4
apport-gtk (version 1.0-0ubuntu5.2) will be upgraded to version 1.0-0ubuntu5.4
libsmbclient (version 2:3.3.2-1ubuntu3.1) will be upgraded to version 2:3.3.2-1ubuntu3.2
libwbclient0 (version 2:3.3.2-1ubuntu3.1) will be upgraded to version 2:3.3.2-1ubuntu3.2
linux-headers-2.6.28-15 (version 2.6.28-15.49) will be upgraded to version 2.6.28-15.52
linux-headers-2.6.28-15-generic (version 2.6.28-15.49) will be upgraded to version 2.6.28-15.52
linux-image-2.6.28-15-generic (version 2.6.28-15.49) will be upgraded to version 2.6.28-15.52
linux-libc-dev (version 2.6.28-15.49) will be upgraded to version 2.6.28-15.52
openoffice.org-base-core (version 1:3.0.1-9ubuntu3) will be upgraded to version 1:3.0.1-9ubuntu3.1
openoffice.org-calc (version 1:3.0.1-9ubuntu3) will be upgraded to version 1:3.0.1-9ubuntu3.1
openoffice.org-common (version 1:3.0.1-9ubuntu3) will be upgraded to version 1:3.0.1-9ubun
openoffice.org-core (version 1:3.0.1-9ubuntu3) will be upgraded to version 1:3.0.1-9ubuntu3.1
openoffice.org-draw (version 1:3.0.1-9ubuntu3) will be upgraded to version 1:3.0.1-9ubuntu3.1
openoffice.org-emailmerge (version 1:3.0.1-9ubuntu3) will be upgraded to version 1:3.0.1-9ubuntu3.1
openoffice.org-gnome (version 1:3.0.1-9ubuntu3) will be upgraded to version 1:3.0.1-9ubuntu3.1
openoffice.org-gtk (version 1:3.0.1-9ubuntu3) will be upgraded to version 1:3.0.1-9ubuntu3.1
openoffice.org-impress (version 1:3.0.1-9ubuntu3) will be upgraded to version 1:3.0.1-9ubuntu3.1
openoffice.org-java-common (version 1:3.0.1-9ubuntu3) will be upgraded to version 1:3.0.1-9ubuntu3.1
openoffice.org-math (version 1:3.0.1-9ubuntu3) will be upgraded to version 1:3.0.1-9ubuntu3.1
openoffice.org-style-human (version 1:3.0.1-9ubuntu3) will be upgraded to version 1:3.0.1-9ubuntu3.1
openoffice.org-writer (version 1:3.0.1-9ubuntu3) will be upgraded to version 1:3.0.1-9ubuntu3.1
python-apport (version 1.0-0ubuntu5.2) will be upgraded to version 1.0-0ubuntu5.4
python-problem-report (version 1.0-0ubuntu5.2) will be upgraded to version 1.0-0ubuntu5.4
python-uno (version 1:3.0.1-9ubuntu3) will be upgraded to version 1:3.0.1-9ubuntu3.1
samba-common (version 2:3.3.2-1ubuntu3.1) will be upgraded to version 2:3.3.2-1ubuntu3.2
smbclient (version 2:3.3.2-1ubuntu3.1) will be upgraded to version 2:3.3.2-1ubuntu3.2
ttf-opensymbol (version 1:3.0.1-9ubuntu3) will be upgraded to version 1:3.0.1-9ubuntu3.1
uno-libs3 (version 1.4.1+OOo3.0.1-9ubuntu3) will be upgraded to version 1.4.1+OOo3.0.1-9ubuntu3.1
ure (version 1.4.1+OOo3.0.1-9ubuntu3) will be upgraded to version 1.4.1+OOo3.0.1-9ubuntu3.1

Any assistance would be appreciated. Thanks!

---

### Post by mikewhatever on 2009-10-02
These are the updates I had yesterday. The error you get has something to do with the repository authentication key. Try a different server.

---

### Post by jwaclawsky on 2009-10-03
Thanks. A different server worked fine but it was a lot slower (I used the "Main server" instead of the previous server "server for the US" ). Does this happen a lot?

---

### Post by drs305 on 2009-10-03
> **jwaclawsky said:**
> Thanks. A different server worked fine but it was a lot slower (I used the "Main server" instead of the previous server "server for the US" ). Does this happen a lot?

The slowdown is most likely due to the introduction of 9.10 Karmic Beta on October 1st. The servers were really stressed during much of the first few days, and choosing the "Main Server" probably selected the heaviest in demand. Things should settle down over the next few days.

One technique during times like this is to open Synaptic or Software Sources and in the Repository settings choose "Other" and then "Choose Best Server", which will run a quick test and determine which worldwide server will provide you the best download speeds. Note this is a only a snapshot, so the 'best' server today probably won't be the 'best' server tomorrow. 

I find it normally best for me to stick with one reliable server and switch the the 'best server' method for short times when it seems to be slower than normal.

---

