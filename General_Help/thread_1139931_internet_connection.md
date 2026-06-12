---
title: "internet connection"
date: 2009-04-27
forum: General Help
---

### Post by deputydawg1 on 2009-04-27
help i am a ubuntu virgin i need advice on how to connect to the net i have a netgear wirless router if that helps.

---

### Post by jimbob on 2009-04-27
How do you want to connect to the router - wired or wireless?

---

### Post by 3rdalbum on 2009-04-27
If you're trying to connect wirelessly, can you first please click the little icon in the top panel that shows two computers, and see if there are any wireless networks listed? If there are, then try clicking on the one with the highest signal strength.

If there aren't, then you may need to install drivers; and the driver you need depends on what wireless card you have.

Can you please go to Applications > Accessories > Terminal and paste in the following commands:

```
lspci
```

```
lsusb
```

Copy and paste the results into this thread and we'll be able to take things from there. If this thread gets buried off the front page feel free to PM me for more help, but I won't be on for almost another 24 hours.

---

### Post by archolman on 2009-04-27
[SIZE=3]:lolflag:Welcome to the wonderful world of Ubuntu!:popcorn: 
 
 On the bottom of your router is a label with bar codes on it. Look closely, & you should see the default log-in details. If not, follow this how-to.
 (for a  DG834G v3 UK but should work)

 Open your browser, & go to; [http://192.168.0.1](http://192.168.0.1)
This will bring your router's page up.
 Log-in using "admin" & "password". 
At the top of the left-hand column should be a set-up wizard. 
Run that. You will need the details from your ISP for this.
 Where it asks for DNS or Domain Name Servers, use these;
208.67.222.222
208.67.220.220

(They are for an organisation called OpenDNS, I have been using them for a long time, & they are free for personal use, very safe, very good)

On the computer.
[/SIZE][SIZE=3]At the right of the top bar, you will see the Network logo, 
 2 monitors on top of each other. Click and select manual config. Unlock it, & in the connections tab, select "eth0" then Properties. Select "Static IP..." The rest of the numbers should look like this;
IP address: 192.168.0.2  [/SIZE][SIZE=3](Your computer on your network)[/SIZE]
[SIZE=3]Subnet mask: 225.225.225.0
Gateway address: 192.168.0.1  (This is the router)

I don't think I've left anything out, good luck, & have fun with your Ubuntu:P

(Oops! I forgot to mention that you should install drivers off the CD that came with the router, & assuming you have all the cables plugged in. I don't use wireless, too slow)
[/SIZE][SIZE=3]
[/SIZE]

---

### Post by jimbob on 2009-04-27
Here is a link that may help you;

            [http://www.pcmech.com/article/how-to-quick-wireless-setup-with-ubuntu-804/](http://www.pcmech.com/article/how-to-quick-wireless-setup-with-ubuntu-804/)

---

