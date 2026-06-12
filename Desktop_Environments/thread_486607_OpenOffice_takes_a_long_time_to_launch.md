---
title: "OpenOffice takes a long time to launch"
date: 2007-06-28
forum: Desktop Environments
---

### Post by cstoh on 2007-06-28
Hello everyone, I am a new convert to Ubuntu. So far I am happy with it except that OpenOffice seems to take a long time to launch. The first time I did it I thought it hung. The next time I let it take all the time it needed and after about 20minutes it opened properly and I could create documents. Is this the common experience or am I doing something wrong? My previous distro of Linux had OpenOffice opening just in seconds.
Please help. Thanks  :(

---

### Post by napster86 on 2007-06-28
check the amount of swap partition and if possible could you give the synopsis of ur sys config..

or this could be becoz of using unstable beta version of OoO elabrote ur stand with some data....

---

### Post by asfaq on 2007-06-28
Hope this link helps: [http://www.zolved.com/synapse/view_content/28209/How_to_make_OpenOffice_run_faster_in_Ubuntu](http://www.zolved.com/synapse/view_content/28209/How_to_make_OpenOffice_run_faster_in_Ubuntu)

---

### Post by turezky on 2007-06-28
Thanks, this really works :)

---

### Post by cstoh on 2007-06-28
I tried this but I am unable to uncheck the Java Runtime box. Everytime I do this the OpenOffice seems to hang. I also get an error message saying that the OpenOffice Java object is not responding and ask me if I would want to wait or force quit. 
The check box for Office Quick start also does not seem to remain checked after I restart office. Anyone has similar problems?

> **asfaq said:**
> Hope this link helps: [http://www.zolved.com/synapse/view_content/28209/How_to_make_OpenOffice_run_faster_in_Ubuntu](http://www.zolved.com/synapse/view_content/28209/How_to_make_OpenOffice_run_faster_in_Ubuntu)

---

### Post by cstoh on 2007-07-04
I realised that it is the installation of Jre that was causing the problem. When Firefox displayed a message that my Java runtime is not installed, I had followed the links and ended in the Java home page. I then downloaded and installed manually the jre1.6 runtime. Apparently this is not good because the Synaptic Package manager does not recognise it and so does Openoffice. So everytime I start Openoffice it looks for the link to jre and cannot find it. It thus took a long time to start Openoffice and it also does not allow me to uncheck the "run office in java runtime" box. Now I've reinstalled Ubuntu and when I get the same message from Firefox I make sure I select and install the jre using Synaptic and it works fine.

---

