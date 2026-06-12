---
title: "Running on a windows network"
date: 2007-06-17
forum: Dell  Ubuntu Support
---

### Post by Stenguns on 2007-06-17
Hi.. I have installed Ubuntu 6.06.1 on a machine at my office.. The office LAN is the basic Windows P2P setup with each machine assigned a static IP, subnet, gateway and DNS..
The Ubuntu machine won't connect to the internet and I'm guessing that I have to set up its TCP/IP protocols.. How do you assign an Ip address, DNS, gateway etc? Am I on the right track?..
The modem router is a basic Netgear product.. 

I really only want the Ubuntu machine for web bowsing and getting webmail etc.. When I get some more time, I want to really get the feel..
Thanks Rob

Whoops.. this is in the wrong place.. Sorry

---

### Post by neptho on 2007-06-17
It helps to know where you are connected.  Are you using wireless?  Ethernet?  Go to 'System', 'Administration', then 'Network'.

This should enable you to make most of the setting changes required for a non-wireless (or WEP Wireless) network.

---

### Post by HermanAB on 2007-06-17
Hmm, you need access to a working Windows machine, then open a DOS box (Start, Run, cmd)and type:
C:\> ipconfig /all | more

All the information you need to configure the Linux machine should be displayed.

Cheers,

Herman

---

### Post by scannerdarkly on 2007-06-18
Regardless of wireless or not just click on "System>Administration>Network.  From there you would click on either your Wireless Connection or Wired Connection and even Modem Connection.  Once you figure out which type you want then just click on it and then click on the Properties button.  Then in there you can configure it for a static IP.  As far as your DNS server IP you would just click on the DNS tab in the Network Settings window.  Then click on the "ADD" button and just type in the IP address of your DNS server.  Now your done.


Side note if your ever trying to check the IP set up on a linux machine you can do that via the Terminal and just issue the ifconfig command.  Thats the ipconfig equivalant to ipconfig /all from Windows.

---

