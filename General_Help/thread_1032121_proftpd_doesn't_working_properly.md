---
title: "proftpd doesn't working properly"
date: 2009-01-06
forum: General Help
---

### Post by unclesam.xu on 2009-01-06
I installed proftpd and gadmin-proftpd. didn't change anything in gadmin-proftpd except setup a user.

I can connect to the ftp server from other computers in my home .

I 've already setup forwarding port 21 to the server on my router.

I can't connect to my ftp server from outside the firewall. I really need someone connect to my computer and download some files.

when I use ftp and then open connection , it will simply shows time out after a while.

what can I do ? I have changed to ubuntu from xp for about 1.5 years. I used to setup ftp server in xp behind the same router firewall without any problem. 

anyone have ideas?

---

### Post by mdurham on 2009-01-06
unclesam.xu, have you installed gadmin-proftpd? It makes it much easier setting up proftp.

---

### Post by unclesam.xu on 2009-01-07
I did state in my post that I had installed gadmin-proftpd. It looks like I need some help with how to deal with router ( adsl modem)

---

### Post by pdtpatrick on 2009-01-07
haha that was a funny question .. anyway why are you using FTP to connect to your ftp server outside your home? soon your logs are going to be filled with all the random people hitting your server. Try using port 22 SSH to your server. Port forward it to your specific server and make sure the server is on Static and not DHCP.

Then using another computer or an iPhone if you have one and then try ssh-ing into the machine .. or you could use Filezilla or whatever other gui you prefer. 

You also have to create ftp users and assign them to the group or u can just add your current users to the ftp group which i wouldnt suggest.

---

