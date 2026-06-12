---
title: "Wireless problems on Dell Mini 9"
date: 2010-10-07
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Singingbowels on 2010-10-07
I have a Dell mini 9 and am loading Ubuntu netbook remix 10.04. Everything works just fine exept the wireless - of course. I have the network symbol, right clicking and going onto network connections allows me to go onto the wireless tab. There was no wireless router showing so I entered the name of my ssid using the add network function. after that nothing....
Going ontoHardware drivers I am told that the broadcom STA proprietary driver is not activted, nor is B43 Wireless driver. Following the instructions gets me to a message ' Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/p/patch/patch_2.6-2ubuntu1_1386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/p/patch/patch_2.6-2ubuntu1_1386.deb). could not resolve 'gb.archive.ubuntu.com''
I've followed all the instructions coming up but gotten nowhere. Could anyone help please?
Thanks,

Scott

---

### Post by mörgæs on 2010-10-07
Hi, can you access the net with wire and install bugfixes?

---

### Post by Singingbowels on 2010-10-08
Yes wire access is fine and I can access terminal and sudo etc. Thanks, Scott

---

### Post by anjilslaire on 2010-10-09
Your error shows that you can't reach the repository your machine is configured to use 'gb.archive.ubuntu.com''
Go into your Software Sources and select a different server to get updates from, then launch Update Manager and click Check to update it then download the drivers again.

---

### Post by Singingbowels on 2010-10-12
Have achieved the change of server and the machine has reloaded up to date package info. Hard wire internet works fine but the wireless icon turns up *device not ready* for wireless connections, even after a restart. I have no idea what wireless card is fitted or how to find out, nor do I know which drivers are installed or how to find out. 

I seem to have hit a brick wall, any ideas?

Many thanks for any help,,
Scott

---

### Post by Singingbowels on 2010-10-12
Solved the problem!
Stumbled across a ref to this; 
[ http://www.ubuntumini.com/2010/04/broadcom-wireless-driver-fix-in-lucid.html]("http://www.ubuntumini.com/2010/04/broadcom-wireless-driver-fix-in-lucid.html")

having reinstalled the [COLOR=#000099]bcmwl-kernel-source[/COLOR]  packageeverything seems fine so far.
Thanks for all help and advice!!

Scott     :guitar:

---

### Post by mörgæs on 2010-10-12
Good, please mark the thread 'solved'.

---

