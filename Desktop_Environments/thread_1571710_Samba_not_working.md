---
title: "Samba not working"
date: 2010-09-10
forum: Desktop Environments
---

### Post by messiah89 on 2010-09-10
I have received this message when trying to access folder and printers on the network.

"**Unable to mount location**"
"Failed to retrieve share list from server"

All I have available is "Windows Network" but clicking that displays the same error message. I'm using Ubuntu 10.4 and other Ubuntu computers on the network are still interacting fine.

I tried removing *Samba* and reinstalling but it didn't change anything.
Can anyone help fix this?

---

### Post by lyman18 on 2010-09-10
This has always happened to me and is tough.  The absolute easy way to do this is- find the local IP address of your windows share 192.168.1.something.


Then use the Connect to server feature in Ubuntu in the places menu, select Windows Share in Services Type, and for Server: paste the IP.  No other fields need to be entered, hit CONNECT!  Flawless, works everytime.

2nd way- to view files
Also in a browser you may enter
smb://192.168.1.102     <- the actual IP of course and this will allow you to view and download files from your share.  Works Flawless also

---

### Post by messiah89 on 2010-09-10
I tried what you said and it does work but I don't often use windows, its mostly Ubuntu. My friend had the same thing happen to him a few months ago but he just reinstalled Ubuntu, but I don't want to. 

Your running 10.4 aswell?

---

### Post by lyman18 on 2010-09-10
The most problems I had were Ubuntu->Ubuntu networking.  These exact steps works flawless in Ubuntu to Ubuntu also.  This is also what I use most, I need my computer to map network shares, as this is an important feature of any OS I use.  

Yes, 10.04 Desktop 64Bit alternate disk to use the RAID 0 feature.  And my steps should work with any version you would run.

---

