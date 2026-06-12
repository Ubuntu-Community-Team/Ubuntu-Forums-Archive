---
title: "Firewall interfering Samba network"
date: 2006-09-16
forum: Desktop Environments
---

### Post by BirdZerk on 2006-09-16
Just a little background, I have Ubuntu installed.  I needed Win2k because of Quickbooks and a few other programs I cannot run in Linux.  So instead of dual booting I used VMware Server, Win2k is running perfectly.  I needed to be able to access and tranfer files to and from Ubuntu while in the Win2k, so I installed and got working Samba.  Everything was working perfectly, until I installed ClamAV and Firestarter with Automatix.  Win2k could no longer access the folder in Ubuntu.  Does anyone know what needs to be changed to allow communication between Ubuntu and Win2k and the firewall still do its job

---

### Post by wieman01 on 2006-09-16
I am using Samba & Firestarter and you'll have to take 2 things into consideration as far as I remember:

1. Open ports 137 - 139, 445 for both ingoing & outgoing traffice (use the Firestarter GUI and simply select "samba" when setting up the rules).
2. For some reason unknown to me I need to use the IP address rather than the computer's name to connect to another PC. Firestarter seems to block some kind of service that prevents PCs from connecting via their network name. No idea why...

Does that help? My Samba has been working perfectly since.

---

### Post by BirdZerk on 2006-09-17
Thank you for the instructions, but I know nothing about networking.  With a lot of trial and mostly error I figured how to get Ubuntu and the vitual Win2k to talk to each other with samba.  So what you asked me to change fell on ignorance.  If you could show more details in the instructions I would definetly appreciate it.



Edit: OK, I figured out that under the policy tab, in inbound traffic I added "SAMBA (SMB) 137-139 445 for everyone" to the allowed services section.  In the out bound traffic I am not sure which setting to use permissive or restrictive.

---

### Post by wieman01 on 2006-09-17
No problem...

1. Set up the same rule for "outbound traffic" as you have done for "inbound traffic" and allow for everyone.

2. Connect to Win2K not using the your virtual system's network name, but replace the name with Win2K's IP address. Connect like this: [COLOR="Blue"]**smb://192.168.xxx.xxx/your_shared_folder**[/COLOR]

192.168.xxx.xxx is the computer's ip address you are trying to connect with.

If all this does not work, disable "firestarter" for a minute and see if you can establish a connection. Also make sure that Win2K has no firewall installed that could possibly block the communication between the 2 systems.

Does that help?

---

### Post by BirdZerk on 2006-09-18
wieman01, I want to thank you for the help.  With what you wrote I was able to open the correct service in the firewall.  What ended up happening was, I needed to be able to save info to a linux folder in my home directory while I am in the virtual  win2k system.  The service I needed to open was DHCP in the "inbound traffic". So again thanks, without the point in the right direction the monitor probably would have ended up on the front lawn.

One more question if you don't mind, can I lock the dhcp service down even further instead of it being open to anyone, if so how?

---

### Post by wieman01 on 2006-09-18
Most welcome.

Yes, you can lock it down. Since only the router uses it to establish a connection with your PC via DHCP, simply enter your router's IP address when adding a rule for "inbound" traffic. There is a field where you can enter an IP address (xxx.xxx.xxx.xxx).

See that?

Generally I configure my firewall as conservatively as possible. So I think restricting it like you have suggested makes sense. Just keep it in mind in case you ever want to connect to _another_ network via DHCP. Then you'll have to change the rule.

---

