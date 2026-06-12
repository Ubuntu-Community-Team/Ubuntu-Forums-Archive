---
title: "share ubuntu hard disk?"
date: 2005-06-13
forum: Desktop Environments
---

### Post by icecube76 on 2005-06-13
hello
i have a dreambox ,and i would like to share the ubuntu hard disk with it.
in the dreambox menu i have the option cifs .
in windows i used to make new dir with any name and share it with the dreambox ,but  with ubuntu i dont know ho to do that 


 :? 

[http://www.geocities.com/alharoon/cifsm.JPG](http://www.geocities.com/alharoon/cifsm.JPG)

could some one please tell me how to configure the dreambox with ubuntu..

regards

---

### Post by icecube76 on 2005-06-16
:(

---

### Post by nocturn on 2005-06-16
I don't know what a dreambox is, but CIFS is the windows file share protocol.
Linux can share files this way bu using samba (it should be in synaptic).

---

### Post by icecube76 on 2005-06-17
dreambox is a sat reciver with Linux os

[http://www.dm7000.de/](http://www.dm7000.de/)

---

### Post by gigirock on 2007-02-20
Hi,

In the panel you sent us you are sharing a disk on computer IP 192.168.0.1
Seems share name is dreambox ( windoze says \\192.168.0.1\dreambox)
this disk will be mounted starting from /hdd

so please make this on dreambox:
telnet dreambox user root passw dreambox
mkdir /hdd/pcrecord

in the panel you sent us set localdir /hdd/pcrecord
and then press yellow as mount

on the pcside you must have a samba share named dreambox 
you have to create an user called a with password a
thats all.

happy recording :-) ..... but it is better if you buy an hd for your DM7000 ;-)

---

