---
title: "USB only internet??? Possible?"
date: 2006-07-16
forum: Desktop Environments
---

### Post by shawnrgr on 2006-07-16
I have a very old system laying around that doesn't have a nic card. I bought one before but it didn't work with my extremely old hardware. It doesn't however have working usb, and my linksys router has the ability to rout through usb. Would this be possible?

(And I know everyone is going to tell me to just find a nic that works, but i would rather not. so please don't respond if you just plan on laughing at me and telling me to purchase a nic)

---

### Post by shawnrgr on 2006-07-18
nobody? their has to be a way! this is linux we're talkn not winblows! \\:D/

---

### Post by Morpsemia on 2006-07-18
I'm not sure I'm reading your post right. I'm not aware of a linksys router that works via USB, but I know several cable / dsl modems that will. These work by installing themselves as a USB NIC, and usually use their own drivers, I don't know if you could find some with ubuntu that will work. If you have working usb I would say get a USB NIC with known linux support, as they are very cheap nowadays.

---

### Post by shawnrgr on 2006-07-18
yes, thats what i ment. i have a cable modem that supports both eth & usb. I want to use the usb to get my old box on the net. anyone know of any good drivers and how to set them up? or anyone who has successfully done this who could give me some advice?

---

### Post by shawnrgr on 2006-08-07
well you guys were so helpful thanks. 

i eventually figured it out. if anyone is trying to get there usb modem working. try these steps:

1. make sure CDCEther is loaded at start. modprobe CDCEther 
2. shut down pc
3. shut down modem
4. make sure only usb is plugede into the modem.
5. turn modem on and let completely boot up
6. turn pc on
7. if nothing at boot up thats fine. log in
8. at prompt: dhclient eth0

worked for me with my linksys usb modem on an older p1 ;) hopefully this can help a few people out.

---

