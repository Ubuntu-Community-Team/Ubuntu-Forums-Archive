---
title: "NAS 1TB drive ethernet setup"
date: 2008-12-25
forum: General Help
---

### Post by Rixii on 2008-12-25
I wasn't sure if this would belong under the Server Platform section or Hardware section or what, so I figured it could be moved from here if necessary..

I have a basic knowledge of servers and networks, I can set up a LAN network between computers. However, I've never actually done a server or NAS setup, so I'm not sure if I have the right idea or if I'm going about this the wrong way.

I bought a NAS device; 1TB, ethernet connection to connect to a router or switch. (Would it be better to buy a switch?) A page comes with it showing how to set it up on Windows. Apparently you can go to run and type '\\N1200' to log into the drive and bring up the setup utility right there.

Of course, I'm not using Windows, and I'm not sure how I would connect from Ubuntu 7.10. I've seen various utilities, such as Samba, that might apply, but I still don't know if that's what I need. My intention is to use this simply as a backup device/storage. Possibly a media server too but I figure one step at a time..

Can anyone help me, or direct me to a page I can get help from?

---

### Post by LoneWolfJack on 2008-12-25
Can't you just enter the IP address of your NAS in your browser?

---

### Post by Rixii on 2008-12-25
How would I find the IP address?

---

### Post by LoneWolfJack on 2008-12-25
The most obvious place would be the control panel of your router. Just enter your router's IP address in your browser.

You can find out about network interfaces and IP addresses by typing

```
ifconfig -a
```

Note that your NAS won't be on that list, but your internet gateway IP will be (which is your router).

if you attach your NAS directly to your machine, it will be on that list disguised as eth0, eth1 or something like that, which is the ethernet port it is connected to.

---

### Post by Rixii on 2008-12-29
Alright, sorry about disappearing, it being the holidays and all, but now I have a chance to work on this again. I have my IP address now; how do I use it to access my NAS?

---

### Post by Rixii on 2008-12-29
Respectful bump

---

### Post by bgerlich on 2008-12-29
First of - what is the ip of NAS - you can check on your router in client list (or some similar name) - it will be one of the connected computers.

Second check if there is a connection with your nas: ping nas_ip_address

Third you have to configure your nas. Usually you can do this by means of connecting with NAS using the internet browser - just type the nas ip address in address bar.

If this doesn't work give us some more details - like the name, producer of your NAS.

---

### Post by Rixii on 2008-12-29
Ahh, I found it. I rarely did anything to set up my router manually except to put a password on. I have the IP and I can ping it, I'll check back if I have any more problems, thanks.

---

### Post by Rixii on 2008-12-29
Alright, I do have another question.. The default viewer in my browser, when accessing the NAS, seems to only allow me to upload files individually, not directories. Now, I believe there's other programs you can use, correct? I believe Samba is the name..

---

### Post by bgerlich on 2008-12-29
Samba is already installed in Ubuntu (Network in "Places"). On some NAS'es you have to turn it on - check the options using the browser interface.

---

### Post by Rixii on 2008-12-29
> **bgerlich said:**
> Samba is already installed in Ubuntu (Network in "Places"). On some NAS'es you have to turn it on - check the options using the browser interface.

Can you give me an idea of what I might be looking for on the interface? Under network-places, I see my network. But clicking it shows nothing inside.

---

### Post by bgerlich on 2008-12-29
Usualy its called "Windows Shares" or SMB, I could be more helpful if you would provide make and model of your NAS.

---

### Post by Rixii on 2008-12-29
It is a Hammer HN1200=1000 1TB

Everything looks to be enabled by default, all of the protocol types. I don't see SMB. I see CIFS, FTP, NFS, and HTTP. It does say on newegg, in the specifications that it supports SMB.

---

### Post by bgerlich on 2008-12-29
Open places->Connect to server , select "windows share" in service type, type in your user name and password, go to configure directory, open index.htm - follow the MAC or windows instructions from that moment

---

### Post by Rixii on 2008-12-29
This is what I see..

[IMG]http://img.photobucket.com/albums/v366/ShisouIkari/Screenshot.png[/IMG]

Do I type the IP in the server section?

---

### Post by bgerlich on 2008-12-29
Correct.

server: nas_ip

User: admin          (?)

---

### Post by Rixii on 2008-12-29
> **bgerlich said:**
> Correct.

server: nas_ip

User: admin          (?)

awesome! I got it, thank you.

---

