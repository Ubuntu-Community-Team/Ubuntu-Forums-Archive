---
title: "Rip to MP3 with K3B"
date: 2005-05-14
forum: Desktop Environments
---

### Post by Chareos on 2005-05-14
Hi all,

I'm trying to rip a music cd to mp3 tracks. I'm used to go with k3b (for preference).
Now, problem comes when I can't find lame in repositories (even in universe!)

Is there a way to get it anyway ?
If that's the case, consider that in my place a personal copy is completely legal (and heavily taxed.....)

Using Hoary on amd64.


THANKS for any help.

---

### Post by DutchLau on 2005-05-14
What about this?

```
wget -c http://frankandjacq.com/ubuntuguide/gstreamer0.8-lame_0.8.8-0.1_i386.deb

sudo dpkg -i gstreamer0.8-lame_0.8.8-0.1_i386.deb

gst-register-0.8
``` 

Maybe this will work for you?

Let us know if this works,

DutchLau

---

### Post by Chareos on 2005-05-14
Tried.
That needs liblame0 (which is needed by k3b too) and I don't know where to get it.

So, no solution as of now, but thanks anyway.

---

### Post by Maestro23 on 2005-05-14
[QUOTE=Chareos]Tried.
That needs liblame0 (which is needed by k3b too) and I don't know where to get it.

So, no solution as of now, but thanks anyway.[/QUOTE]


If you have your /etc/apt/sources.list file set up per the Ubuntu Guide, the lates version of liblame0 is available.  Just checked via synaptic.  Did you set up the extra repositories via the guide?  If not, click the link in my sig.  Hope is helps ya.

---

### Post by Chareos on 2005-05-14
Thank you for your reply !


deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) unstable main
did the trick ad I was able to install lame (hope that "unstable" will not kill my ubuntu eheh)

deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) stable main
deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) testing main
these two seems to be dead, as ubuntu-extra seems to be.


Now, I think I'll remove
deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) unstable main
for safety, but it's goot to know where to look for "exotic" packages (orunexpclicably excluded ones...)


Thank you again.
A well-satisfied ubuntu user :)

---

### Post by Maestro23 on 2005-05-14
[QUOTE=Chareos]Thank you for your reply !


deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) unstable main
did the trick ad I was able to install lame (hope that "unstable" will not kill my ubuntu eheh)

deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) stable main
deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) testing main
these two seems to be dead, as ubuntu-extra seems to be.


Now, I think I'll remove
deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) unstable main
for safety, but it's goot to know where to look for "exotic" packages (orunexpclicably excluded ones...)


Thank you again.
A well-satisfied ubuntu user :)[/QUOTE]


Glad it helped ya man... :wink:

---

