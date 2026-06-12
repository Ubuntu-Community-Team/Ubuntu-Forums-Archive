---
title: "sudo slow?"
date: 2005-11-06
forum: Desktop Environments
---

### Post by kreso on 2005-11-06
Evertime I want to start a graphical program such as nautilus or gedit with root priveleges, it takes about 5 minutes for the program to load?

I use "gksudo nautilus" or "sudo nautilus" in console.

---

### Post by earobinson on 2005-11-07
try 
1.sudo su
2.<password here>
3.<program name here>

did it take the a long time to get from 1 - 2, or from 2 - 3? 1 - 2 is to log on as root, 2 -3 is to run the program. It may be that the programs you are using just take a long time to load.

---

### Post by Eleka on 2005-11-07
I have the same problem on my laptop. A time ago, a time before updated to Breezy it began to happen. 

Sometimes, when I sut down the computer happens to, and a few days ago the startup go slower than before....

I've tested now, and magically it works very fine ... I don't undestand it, but it works fine ....

The only thing that had changed is that I start with all the network interfaces down (I'm in a laptop) and ifconfig up the interface that I want ...

Test it :P

---

### Post by kreso on 2005-11-07
I've experimented a bit and it appears it is related to the network connection?? Moreover, Totem wont start if eth0 isn't up???

---

### Post by Eleka on 2005-11-08
I think that too. When I have problems with sudo are when I have eth0 down, and I do it in my laptop when I'm using the wireless card ... :S

It's very strange

---

### Post by kreso on 2005-11-08
maby it's a conspiracy :) They might have insterted a microsoft agent within ubuntu ranks :)

---

### Post by Eleka on 2005-11-09
Lol! It's very very probabily :D

---

### Post by flipkick on 2005-11-10
I had the same problem. "sudo" wasn't even working. When I changed my passoword, everything went fine again.

---

### Post by kreso on 2005-11-10
nope. changed the password and still the same problem...

---

### Post by nab on 2005-12-07
I have the same problem. sudo gedit is taking for ever. 

The last changes I made concerned wlan-WPA and xorg-ati/radeon driver.

Testing the system Iget:

user:~$ sudo su
Password:
user:/home/user# gedit

(gedit:8609): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

What can I do to correct this behavior?
(I searched the forum, but without successs.:) )

Niko

---

### Post by braynyac on 2006-01-19
I know this is a bit late in coming....but I think have figured this issue out on my setup.  I was having the same problem - sudo wouldn't open anything, and other programs (Citrix) were taking FOREVER to load.  While fixing a CUPS issue I was having, I noticed that my loopback interface was not getting autostarted.  This happened after I started using Network Manager to control my wireless.  If I start the loopback interface manually, all my problems are solved!  

My problem is that I have to disable the auto before the loopback stuff in my /etc/network/interfaces file, and now it won't come up automatically.  Anyone have any ideas?

Thanks,

~braynyac

---

### Post by dcstar on 2006-01-19
[QUOTE=kreso]Evertime I want to start a graphical program such as nautilus or gedit with root priveleges, it takes about 5 minutes for the program to load?

I use "gksudo nautilus" or "sudo nautilus" in console.[/QUOTE]
Check your /etc/hosts file and make sure that your system name is listed on the 127.0.0.1 entry, as well as on your "real" IP address entry.

---

### Post by GuruX on 2006-01-27
I experience the same problem with it taking several minutes to perform "sudo gedit".
I have the common problem with needing to activate my wireless card every time i start ubuntu. But before I activate my wireless, sudo gedit runs just fine. So, the conflict is somewhere with the wireless network (or perhaps all network connections). But I have no idea where.

---

### Post by operationsone on 2006-05-09
Sorry to re-open an old thread, but I'm having the same problems. I have to run pppoeconf everytime Ubuntu (5.10) loads to be able to connect. If i close the connection (poff) and type for example "sudo gedit test" than gedit opens automatically, however, if i'm still connected it opnes gedit after like 5 minutes. This shouldn't be so difficult to correct. Anyone have any ideas?

> , as well as on your "real" IP address entry.

Do you mean the ip that i'm using? It's dynamic..so I would have to change the file everytime? Could you elaborate on this please?

---

