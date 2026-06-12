---
title: "Server install"
date: 2006-03-22
forum: Desktop Environments
---

### Post by shaan_l on 2006-03-22
Hi

I did the server install, and I wanna know what basic packages do I need to make it run "smooth".

So far I've installed the following:
fluxbox
krusader
firefox
xmms
adept

I need samba on here, and I attempted to install it (as well as swat) but I'm not sure how to check if it works? krusader keeps saying that the protocol is not supported.

---

### Post by alamba on 2006-03-22
If you did the server install did you then install the GUI post the fact? If yes, why? If not, then it's not a server install per se.

A

---

### Post by shaan_l on 2006-03-22
i did the server install so i didnt have all the extra "stuff"
and i wanted to learn a bit about linux too....

---

### Post by alamba on 2006-03-22
ok. So I'm assuming that you installed KDE or GNOME after the server install. For installing samba just look for it in synaptic or do sudo apt-get install samba (or smb - not sure which one). To see if its working:
1. cd /etc/init.d
2. ./samba restart

A

---

### Post by shaan_l on 2006-03-22
nah, installed fluxbox as my window manager.
i did what you said for samba, and its there.

how do i get krusader to support the protocol now?

Also, how do i get some of the features that are in kde like the control panel, where i can browse the network, etc etc

---

### Post by alamba on 2006-03-22
ahhhh...this the moment where I kick myself for being plain dumb. Didn't realise fluxbox was a gui. Could've saved us 2 posts. I've never used krisader so don't know about that. 

However, what are you trying to do? Do you want to host a samba server or are you trying to access a samba share? If it's the latter then smbmount might be the thing u're looking for.

A

---

### Post by shaan_l on 2006-03-22
haahaaa yea fluxbox is a gui :) 

i wanna access share drives on my network. the other pc's are xp machines.

---

### Post by alamba on 2006-03-22
Then i know of 2 ways:
1. Simple GUI method on GNOME gui (this is what I use)
2. smbmount or mount with smbfs as the file system. A simple google search will get you going.

A

---

### Post by shaan_l on 2006-03-22
k cool.

how can i get stuff like the control panel running, and the updates for adept (security updates), the system settings....etc etc?

also, my cdrom doesnt work? i put a cd in and nothing!

---

### Post by alamba on 2006-03-22
Again have'nt used adept. cdrom should work once you have mounted it.

A

---

