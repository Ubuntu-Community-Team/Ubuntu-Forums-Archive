---
title: "Bluetooth from phone to pc still not fixed?"
date: 2009-05-13
forum: General Help
---

### Post by attercop on 2009-05-13
I'm sure that the last time i had this working was in Gutsy. It was quite a while ago.

Bluetooth browsing my phone from pc works fine. Sending something pc to phone works fine. But sending something phone to pc fails instantly.

Am i missing something or is bluez still duff? I'm using Jaunty now but this has been the same in Hardy and Intrepid.

---

### Post by zaphod777 on 2009-05-13
I can't seam to get it to work either.

---

### Post by attercop on 2009-05-14
Is there anyone who has had this working since Gutsy, without maybe using the Gutsy version bluetooth in a more recent Ubuntu?

---

### Post by withnail420 on 2009-05-14
It works for me on 8.04, but I'm using kubuntu. I remember having some issues on 7.10 with gnome. I ended up using the gnome bluetooth app for receiving files and kbluetooth for sending them. Or it might have been the other way round....
Anyway, kbluetooth works fine for me now, so I would suggest installing that and trying it out. It will install in gnome fine, probably needs to install a few libraries too though.

do

sudo apt-get install kbluetooth

and play around with it. Good luck

---

### Post by sgosnell on 2009-05-14
It works fine for me on Jaunty.  I just tried it again, and I can send from the phone to my PC easily.  Exactly what are the symptoms you're having?

---

### Post by attercop on 2009-05-15
Basically everything works except sending from phone to pc. My phone can see my pc, but if i try and send something it just says sending failed almost instantly. They're paired and set up. It makes no sense.

---

### Post by sgosnell on 2009-05-16
Have you installed Bluetooth File Sharing?

---

### Post by attercop on 2009-05-17
> **sgosnell said:**
> Have you installed Bluetooth File Sharing?

Ah. No i did not have that installed. And i have to say it took me quite a while to find it. In the end i installed something on a guess called "gnome-obex-server 0.11.0" and when installed that presented itself as Bluetooth File Sharing.

I'm very surprised that this isn't part of the overall bluetooth package in Ubuntu. But glad to get it sorted. Many thanks.

---

### Post by sgosnell on 2009-05-17
I would have linked it, but I couldn't remember the exact name, and I was short on time.

---

### Post by Billy_McBong on 2009-05-22
It seems like I have this problem. I can send files to my phone and browse it but not receive them. Nothing in this tread has fixed it either. 
Bluetooth File Sharing doesn't seem to do anything and kbluetooth isn't in my repositories for some reason.

I know the files can be read by my computer since I can open them with programs but if I try to copy/paste them through nautilus it says "Media type not supported"

---

### Post by slimx3m on 2009-06-01
attercop,

where i could find that package?  becuase is not on ubuntu packages repository at all :(

---

### Post by slimx3m on 2009-06-01
never mind... i just resolve my problem by installing "gnome-bluetooth" and it works like a charm.

---

