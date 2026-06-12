---
title: "Breezy Badger and P2P"
date: 2005-10-14
forum: Desktop Environments
---

### Post by pawel_z_wroclawia on 2005-10-14
I have been using Breezy Badger (Kubuntu) for about two weeks. P2P programs have been refusing to work since the beginning, neither Azureus, nor aMule is operational. They start normally, the search function in aMule does work, but they will not download anything. Also, the system slows down significantly. Program settings are defaults with some very minor modifications, iptables settings are OK... I have no idea what can possibly be wrong. Under Hoary Hedgehog both programs caused no problems. 

It is really troublesome, please help!

---

### Post by Tails on 2005-10-14
yeah, i have the same problems as well, all BitTorrent apps just couldnt download anything..

---

### Post by philipacamaniac on 2005-10-14
You should give Ktorrent a try.  sudo apt-get install ktorrent  (with universe repos enabled)

---

### Post by manicka on 2005-10-14
Have you tried anieboy's how-to for azureus?

[http://ubuntuforums.org/showthread.php?t=75272](http://ubuntuforums.org/showthread.php?t=75272)

---

### Post by UKer on 2005-10-14
I've always used gtk-gnutella without any issues. I have port 6346 open on my router so Gnutella works well, as you have to configure which port to use (it works [just about] otherwise, with crap speeds), I dunno if you have to open ports with other networks like BT and amule.

---

### Post by pawel_z_wroclawia on 2005-10-14
I repeat, Azureus is installed and it starts. Just doesn't download anything. Also, the problem concerns aMule as well, so I doubt it is Azureus-related. Any both programs DID work like charm under Hoary... 

I repeat, ifconfig is OK, by this I mean the appropriate ports are open. 

So most of the above replies are of little help, I'm sorry to say. But I'll try Ktorrent... just in case...

---

### Post by pawel_z_wroclawia on 2005-10-14
I've installed KTorrent and... wow, it works! And its simplicity is charming :). Thanks, a million, philipacamaniac!


Still, I would like to be able to run other programs... so still waiting for the ideas. It seems I'm not the only one. Perhaps it is a general Kubuntu Breezy Badger issue?

---

### Post by pawel_z_wroclawia on 2005-10-15
Update. Several hours later. KTorrent does work... a bit. The files start to download, but the peer number and download times are ridiculous and after some time the download dies...

So it really seems the problem concerns all P2P programs. A network issue? Please help!

---

### Post by pawel_z_wroclawia on 2005-10-15
Plus, I am getting "The tracker ... is down, stopping download." message from time to time.

---

### Post by UKer on 2005-10-15
[QUOTE=pawel_z_wroclawia]I repeat, ifconfig is OK, by this I mean the appropriate ports are open. [/QUOTE]

I meant the ports on your router, not your linux setup (if you use one, if you're directly on the Internet with a modem forget this).

It won't stop you downloading, it just means it will be very slow as you can't accept incoming connections, see [http://dessent.net/btfaq/#ports](http://dessent.net/btfaq/#ports) - make sure a TCP (UDP not needed) port between 6881-6999 is open.

---

### Post by pawel_z_wroclawia on 2005-10-15
[QUOTE=UKer]I meant the ports on your router, not your linux setup (if you use one, if you're directly on the Internet with a modem forget this).

It won't stop you downloading, it just means it will be very slow as you can't accept incoming connections, see [http://dessent.net/btfaq/#ports](http://dessent.net/btfaq/#ports) - make sure a TCP (UDP not needed) port between 6881-6999 is open.[/QUOTE]

I also meant the ports on my router. Guess I wasn't clear. Yeah, it was late and I was very tired yesterday. OK, here's how it works.

One computer (with Slackware) is connected directly to the Internet, is always on and serves as a mail server (and a router, yeah). The other one (let's call it workstation) is connected to that server and has Kubuntu Breezy Badger installed. /etc/rc.d/rc.f on the server has not been changed and it worked OK when there was Ubuntu Hoary Hedgehog installed on the workstation.

So I'm at a loss... It does look like a port problem... but iptables are well configured on the server. It must be something on the workstation.

---

### Post by myg on 2005-10-19
im having the same problem

azureus worked fine before the breezy update and now it does not download.  

bittorrent ports are correctly forwarded and ifconfig looks correct.

---

### Post by thnogueira on 2005-10-19
The same here with Azureus. I gave ktorrent a try but it says all my torrent files are corrupted. What a nightmare upgrading to breezy...

---

### Post by myg on 2005-10-19
reinstalling azureus worked for me

[http://http://ubuntuforums.org/archive/index.php/t-75272.html]("http://http://ubuntuforums.org/archive/index.php/t-75272.html")

---

### Post by stoeptegel on 2005-10-20
I havn't got problems with rufus on kubuntu5.10. I you want to try this (better)client, install python-wxgtk2.6 and then rufus and it should work.
deb package here: [http://strikeforce.dyndns.org/files/](http://strikeforce.dyndns.org/files/)

---

### Post by thnogueira on 2005-10-20
```

I havn't got problems with rufus on kubuntu5.10. I you want to try this (better)client, install python-wxgtk2.6 and then rufus and it should work.
deb package here: http://strikeforce.dyndns.org/files/

```

Thank you, stoeptegel. I've finally got brezzy to manage with torrent eith rufus.
With this solution I'll don't need to give a try to myg's solution :) 

```

myg
reinstalling azureus worked for me
http://http://ubuntuforums.org/archi...p/t-75272.html

```

---

### Post by AndersAA on 2005-10-20
[QUOTE=pawel_z_wroclawia]Plus, I am getting "The tracker ... is down, stopping download." message from time to time.[/QUOTE]

well... this means the server on the other side is having problems (tracker is the server you connect to that tells you about other peers and seeds).

I got a feeling this isn't your problem at all, but your testing torrents from a broken tracker or something ;)

---

### Post by squirrel on 2005-11-11
hi, 
i have the same problem as the originial poster (p2p apps don't work) on ubuntu badger, ever since i upgraded from warty warthog. has anybody solved this?

how can i check whether the relevant ports are open?

thanks!

---

### Post by dolny on 2005-11-12
[QUOTE=pawel_z_wroclawia]Update. Several hours later. KTorrent does work... a bit. The files start to download, but the peer number and download times are ridiculous and after some time the download dies...

So it really seems the problem concerns all P2P programs. A network issue? Please help![/QUOTE]

I had exactly the same problems as you. 

1. aMule didn't work so I installed Limewire, but it doesn't handle ed2k links (even though that it was very fast)
a) After some time I decided to try again, I left aMule working for veryyy long and finally it started finding sources and downloading!!! It works now, even though its not fast... but this will change with time I think. I hope.
2. Azureus worked SLOOOOW. So I removed it, along with Java. Did a complete reinstall of Java and Azu, following a tutorial on these forums. It works now :)

Try it my way.
Pozdrawiam, nie poddawaj sie :)

---

### Post by Lmax on 2005-12-08
The problem is probably java. This solved it for me. Azureus is downloading at full ADSL capacity now.

To start:
Add these lines to your /etc/apt/sources.list:
deb [http://antesis.freecontrib.org/mirrors/ubuntu/plf/](http://antesis.freecontrib.org/mirrors/ubuntu/plf/) breezy free non-free
deb-src [http://antesis.freecontrib.org/mirrors/ubuntu/plf/](http://antesis.freecontrib.org/mirrors/ubuntu/plf/) breezy free non-free

Make sure these modules are installed:
sudo apt-get install libcommons-cli-java liblog4j1.2-java libseda-java libswt-gtk-3.1-java

Then install java with this command:
sudo apt-get install sun-j2re1.5

Then do this:
sudo update-alternatives --set java /usr/lib/j2re1.5-sun/bin/java
(without this java doesn't work correctly)

Then (re)install azureus:
wget [http://ftp.us.debian.org/debian/pool/contrib/a/azureus/azureus_2.3.0.6-1_all.deb](http://ftp.us.debian.org/debian/pool/contrib/a/azureus/azureus_2.3.0.6-1_all.deb)
sudo dpkg -i azureus_2.3.0.6-1_all.deb

Good luck

---

### Post by hellmet on 2006-05-17
[QUOTE=Lmax]The problem is probably java. This solved it for me. Azureus is downloading at full ADSL capacity now.

To start:
Add these lines to your /etc/apt/sources.list:
deb [http://antesis.freecontrib.org/mirrors/ubuntu/plf/](http://antesis.freecontrib.org/mirrors/ubuntu/plf/) breezy free non-free
deb-src [http://antesis.freecontrib.org/mirrors/ubuntu/plf/](http://antesis.freecontrib.org/mirrors/ubuntu/plf/) breezy free non-free

Make sure these modules are installed:
sudo apt-get install libcommons-cli-java liblog4j1.2-java libseda-java libswt-gtk-3.1-java

Then install java with this command:
sudo apt-get install sun-j2re1.5

Then do this:
sudo update-alternatives --set java /usr/lib/j2re1.5-sun/bin/java
(without this java doesn't work correctly)

Good luck[/QUOTE]
Thanks a TON mate..
That JAVA thingy made all the difference.
I am really grateful to yaa

---

