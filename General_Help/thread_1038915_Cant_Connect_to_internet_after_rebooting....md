---
title: "Cant Connect to internet after rebooting..."
date: 2009-01-14
forum: General Help
---

### Post by Isilion on 2009-01-14
Hi i was trying ipmasq to change my ip so i can download serios files from megaupload, rapidshare, etc.
I runned "#ipmasq" and nothing seemed to happen. after a couple hours i rebooted and at first i cant connect to internet.

im not very advanced linux user, so i tryed messing with ifconfig and iptables. 

this is what i did:

#ifconfig eth0 down
#ifconfig eth0 up
#iptables -F
#ipmasq --no-act
(then i resetted the modem)
#ipmasq
#depmod -a /etc/ipmasq.rules

and magically connection worked again, but i didnt have idea of exactlly what i've done lol.neither, i dont know if net time ill rebot it will work again. could anyone help me?and perhaps, teach me how to properly spoof my ip for what im looking for?

---

