---
title: "How do I...? (Linux print server)"
date: 2009-05-11
forum: General Help
---

### Post by chemicalfan on 2009-05-11
I'm looking to set up a Linux print server, to serve Windows clients. I presume this is possible? The server will be a P4 2GHz, so it'll be a lightweight distro (probably Xubuntu 8.10, as I'm already running it on my laptop). Basically, I want to connect my printer to my old PC, and be able to print from the family laptop (running XP). I've got this working with my main PC (running Vista x64) as server, but I'm gonna be moving out, so was going to use my old PC as the server and leave it at home. I'm sure this must be possible somehow, but the whole Windows-Linux network thing confuses the hell out of me. 

I need a noob-friendly step-by-step procedure on this if possible, including a required package list and config changes needed, both on the Linux machine and the Windows client machine (although I could probably figure out the Windows changes myself)

---

### Post by Peter09 on 2009-05-11
Try it simple first

with the printer connected to your Linux system

System->Admin->Printing

Select the server and set it to publish printers to network.

---

### Post by chemicalfan on 2009-05-11
Thanks for the quick reply!
I don't have the Linux machine up and running yet (although I could test it with my laptop, as it should be a clone of the setup). I don't have any kind of network between my Linux laptop and the family XP laptop, the only common connection between them is that they share a wireless router. I presume things like Workgroup are important, and I'll need to set those up somehow?

---

### Post by Peter09 on 2009-05-11
Sharing a wireless router is fine. Don't think you will need to worry about workgroup.

---

### Post by chemicalfan on 2009-05-11
I'll give it a test with my laptop when I get in from work, I'll let you know how it goes!

---

### Post by chemicalfan on 2009-05-11
Ok, I've got the printer plugged in, and Linux recognises it! However, I'm not sure of the share path I need to input into the XP machine - where do I find this?

---

### Post by Peter09 on 2009-05-11
I think its will be automatically found if you tell windows to look for it.

---

### Post by chemicalfan on 2009-05-11
Yes, I've found the laptop (Linux server)! But, Windows is asking for a logon, and putting in my Linux username and password doesn't cut it. Do I need to create a new user on my Linux server for the printing - if so, do I need to do anything special with authority to allow printing?

---

### Post by Peter09 on 2009-05-11
Make sure that you have the access control setup in the printer config on the server.

---

### Post by chemicalfan on 2009-05-11
Sorry, I don't know where I'm looking *doh* I've opened up the Printing page under Applications->Settings, clicked on Server->Settings. I've got "Publish shared printers connected to this system" checked, but nothing else. Is this what you would expect? Or do I have to make some setting changes via the terminal?

Edit: I've just tried it with "Allow remote administration" checked as well, and it doesn't help

Edit 2: I've found access control, under Properties of the printer itself (right-click menu on printer icon), and it is set to Allow for everyone. Still no joy :(

---

### Post by Peter09 on 2009-05-11
Don't think you should need much else.

---

### Post by chemicalfan on 2009-05-13
I didn't get the access to my Linux machine sorted - although I appreciate this has deviated slightly from my original question on printing. Can you give me some advice as to why my Windows machine cannot access the Linux one, even when supply valid credentials (username & password)? It can see the machine on the network perfectly, but when access is attempted, asks for a username & password, and nothing I enter seems to work (Linux or Windows passwords)

---

### Post by Peter09 on 2009-05-13
This may be to do with samba shares - look around for documentation on setting up smb.conf

---

### Post by chemicalfan on 2009-05-13
This is what I was afraid of - Samba is a daunting thing for a networking noob like myself. I'll take a look around though, thanks for your help on this :)

Edit: Found this [link]("http://tldp.org/HOWTO/SMB-HOWTO-9.html"), think it will help a lot!

---

### Post by MysticGold04 on 2009-05-13
This thread might help you out... without using Samba!

[http://ubuntuforums.org/showthread.php?t=1117117](http://ubuntuforums.org/showthread.php?t=1117117)

---

