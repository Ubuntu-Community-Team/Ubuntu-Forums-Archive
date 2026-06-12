---
title: "Ubuntu Server Ed. on Dell pc's?"
date: 2007-08-08
forum: Dell  Ubuntu Support
---

### Post by arvadawest on 2007-08-08
[SIZE="5"]Hi,
I am considering purchasing a Dell pc with Ubuntu but I noticed they provide the desktop version of Ubuntu and not the Server edition.  I would really like to run the server edition for DNS on my network, Apache, the Firewall, etc.  Does Dell provide the server edition?  Thank you.  -AW[/SIZE]

---

### Post by Rocket2DMn on 2007-08-08
For future reference, please type in regular size, large/bold/caps makes it appear rude.
On to your question - I don't believe Dell sells PCs with the server edition, but you could certainly install it yourself after purchasing a computer.
The server edition doesn't have a GUI by default, only CLI, but you can setup X if you want.  You can install LAMP or whatever programs you want for the server to work with Apache and perform your DNS functions.  A firewall is built into Ubuntu in the form of iptables.  If you install a GUI you can use *firestarter* as a nice graphical interface to iptables.
Welcome to Ubuntu!

---

### Post by arvadawest on 2007-08-08
Hi, thanks for your response. Can I install LAMP on the desktop edition?  I want to use Ubuntu as mostly a file, dns, and apache server.  I just wonder if the desktop edition would allow me to do this? (sort of quasi-server) or would i need the Ubuntu server ed.  Thanks I am new to this.

Also, if I purschased a Dell with Ubuntu desktop ed., would it be easy to convert to server ed.?  thanks.   -aw

---

### Post by Rocket2DMn on 2007-08-08
Yeah, anything you can install on one, you can install on the other.  The server edition is just better tweaked to act as a server.

You don't "convert" to server edition, you would just download the server edition from the website - [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) - and install over the existing desktop edition  (wipe it clean and put server edition on, essentially).

---

### Post by arvadawest on 2007-08-08
Thanks for your advice.  Could I use the desktop ed to serve as a file server for my network.  Of course, the network is windows based, but it would be nice to use Ubuntu as my file server v. Windows 2000 Server. 

I am tired of the security patches and reboots and I understand that Ubuntu Linux..well.. can run without reboots for weeks and months.  

So that is my primary question--would u recommend using the server ed. or can I use the desktop ed. as a network file server?  Thanks.

---

### Post by Rocket2DMn on 2007-08-08
Either will work.  If you just want to share files, the desktop version might be easiest, but if you want to be a purist, use the server edition.  Again, they will both work - it probably would not be worth the trouble to setup the server edition just to share files.
And yes, you can share files, you would have to setup a samba share - there are threads to help you on that, we won't cover doing that here.  If you want to pursue that, start here - [https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)
If you do need help with it, start a separate thread for it once you try setting it up.

---

### Post by arvadawest on 2007-08-08
Outstanding.  Thank you very much. I will probably purchase a pc through Dell with ubuntu desktop ed and start there.  I thank you for answering all my question and for your time.

-Arvada West

---

