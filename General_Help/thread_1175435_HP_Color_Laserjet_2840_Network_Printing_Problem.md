---
title: "HP Color Laserjet 2840 Network Printing Problem"
date: 2009-06-01
forum: General Help
---

### Post by scaat on 2009-06-01
Hello Everybody,

       I just switched from Vista to Ubuntu 9.04 Jaunty. So far, everything is great ;)

       I just have one issue currently: I have installed Samba and I can print to windows network drivers which are hooked up to the xp terminals without any problem. 

       We also have a HP Color Laserjet 2840 which is directly connected to the network. I have assigned a static IP to the HP device. Windows clients have no problem connecting to it and use other functions like copy, scan to network etc. 

       I have tried to install the device from system / management / printing / add printer section. Luckily, Ubuntu instanly showed me the device on the network and installed it without any hassle. But when it comes to printing, I was not that lucky. I am trying to print various documents, also test pages. They are showing up in the printing queue but not printing. 

       Weird thing is, I am able to scan documents via XSane image scanning, which indicates there is not any problem in network communication between HP device and Ubuntu. But printing is a no-go. Any ideas?

---

### Post by scaat on 2009-06-02
Hi guys, anyone has any ideas? I am really in desperate position.

---

### Post by kirilloff on 2009-06-02
same problem 
i can see network printer (it adress and port)
but i can't print

---

### Post by kirilloff on 2009-06-02
i forgot to say: it's HP LaserJet p2015

---

### Post by scaat on 2009-06-02
Well, I could not find any solution to the problem but I have developed a workaround.

I have a virtual machine with XP installed on my Server, which is running with Win Server 2003. This virtual machine is working as a "scan server", since HP scanning software is not working on Server 2003 systems. We needed a dedicated machine for scanning jobs so I found this workaround for that purpose. (you can say that this workaround is built in another workaround ;)) 

Well, I have shared the HP device from this scan server, than I connected Ubuntu to the scan server. Now I can print without any problem. Scan server is queuing and printing the print jobs. 

I suppose there is a compatibility problem for Linux with the jet direct software installed on HP device. Despite the fact I could not solved the main problem, this workaround works quite seamless for me.

---

