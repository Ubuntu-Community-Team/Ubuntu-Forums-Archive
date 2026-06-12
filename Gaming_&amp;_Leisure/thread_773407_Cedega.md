---
title: "Cedega"
date: 2008-04-28
forum: Gaming &amp; Leisure
---

### Post by inukaze on 2008-04-28
Hi everybody , well im in this forum for the next reason 

1 - i have install cedega
2 - i have install engine 6.04
3 - i have install Ragnarok Online
4 - i have configure the Ragnarok Online (correctly)
5 - But i cant play.

In my older version Ubuntu 7.04 Feisty Fawn, i just install all and configured it, and in the cedega i play the game in a pirated server , called gaia , without inconvences. I had install Ubuntu 8.04 is very powerfull and very stable and much more, but when i try to connect to the server 

the first was : "Disconected from server" , immediately i press enter or click "Ok" , the game not try to connect to server , i solved that open an terminal and wrote :

sudo iptables -A INPUT -p tcp --dport 2200 -j ACCEPT
sudo iptables -A INPUT -p tcp --dport 2828 -j ACCEPT
sudo iptables -A INPUT -p tcp --dport 2929 -j ACCEPT
sudo iptables -A INPUT -p tcp --dport 2900 -j ACCEPT
sudo iptables -t nat -A OUTPUT -d 127.0.0.1 -j DNAT --to 24.29.82.68
sudo iptables -t nat -A OUTPUT -d 127.0.0.1 -j DNAT --to 75.126.24.22
sudo iptables -t nat -A OUTPUT -d 127.0.0.1 -j DNAT --to 75.204.113.189
sudo iptables -t nat -A OUTPUT -d 127.0.0.1 -j DNAT --to 70.112.211.59

but when i try to connect again, i wait a few minute or two minutes . the game show me the message "No connected to the server" , the page of server im using is [http://www.gaia-games.com](http://www.gaia-games.com) , but i cant play for this mistake .

someone tell me , if possible , is a system firewall? or something similar i wanna desactivated , i dont need it.

i wait somesone can help me in this plx, i really wanna play againa Ragnarok Online. its very bad what because of a update system i cant play again . some one have possible solution?

sorry for my bad english, using google translator

---

### Post by ChameleonDave on 2008-04-28
Cedega is really crap software.  You can't expect it to work very often.  Try asking on the Cedega forums rather than here.

---

### Post by Dark Aspect on 2008-04-28
> **ChameleonDave said:**
> Cedega is really crap software.  You can't expect it to work very often.  Try asking on the Cedega forums rather than here.

Well thats a little excessive,but I really wouldn't expect many titles to work that aren't supported.If the game is not supported then try wine:

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=701]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=701")

Looks some what promising.

---

### Post by Perfect Storm on 2008-04-29
> **ChameleonDave said:**
> Cedega is really crap software.  You can't expect it to work very often.  Try asking on the Cedega forums rather than here.

That's not the answer we won't on this forum. If someone wants help with Cedega on this board. They are allowed. If you don't want to help, don't post in that thread.

Thanks.

---

### Post by inukaze on 2008-04-29
Well , you dont understand my point, i think,
I just wanna to know, how to desactivated ALL FIREWALLS of Ubuntu 8.04 . I think this is the solution if that no work, the solution is Reinstall the Game Using Cedega Again, Updating in WiN32 , and Copy-Paste where i has installed the Game Under my distro.

Cedega Yes Support the game, i cant enter in the Cedega Forums, im not register in the TransGaming , why i cant, i dont know how to pay to create and account under TransGaming , you know how do that , im in venezuela, caracas , someone can tell if posible pay it without credit card? i just wanna evade the Ddos Attacks.

well how i can desactiva all firewalls of Ubuntu 8.04?
you understand me?

and one more thing, the Wine Is very SLOW for me , the cedega can execute the game perfect :D ;)

My PC:
AMD 950 Mhz Athlon
RAM : 768 MB
Video : Nvidia GeForce 2 100/200 MX [64 MB]
Distro : Ubuntu 8.04

---

### Post by Dark Aspect on 2008-04-29
> **inukaze said:**
> Well , you dont understand my point, i think,
I just wanna to know, how to desactivated ALL FIREWALLS of Ubuntu 8.04 . I think this is the solution if that no work, the solution is Reinstall the Game Using Cedega Again, Updating in WiN32 , and Copy-Paste where i has installed the Game Under my distro.

Cedega Yes Support the game, i cant enter in the Cedega Forums, im not register in the TransGaming , why i cant, i dont know how to pay to create and account under TransGaming , you know how do that , im in venezuela, caracas , someone can tell if posible pay it without credit card? i just wanna evade the Ddos Attacks.

well how i can desactiva all firewalls of Ubuntu 8.04?
you understand me?

and one more thing, the Wine Is very SLOW for me , the cedega can execute the game perfect :D ;)

My PC:
AMD 950 Mhz Athlon
RAM : 768 MB
Video : Nvidia GeForce 2 100/200 MX [64 MB]
Distro : Ubuntu 8.04

> sudo ufw disable

You have to restart your computer,and I don't recommend disabling your firewall.

---

### Post by inukaze on 2008-04-30
i have do that before

in a Terminal 
$> sudo ufw disable

and restart the system, but that not works still, the ports, not are free.
how to i make the ports "ALL" ports , i wanna FREE thats ports.

:'( Why this distro , well if i cant resolve, i need to format my Ubuntu, and Install WinXP , just for Play the game. ;)

Is the one thing i can do, if i cant resolve the problems with the PORTS , and the connection of the game with the server.

you can try it , test the Cedega, and Raganarok Sakray?

---

### Post by cogadh on 2008-04-30
You do realize that with all your ports open, you are completely exposed and advertising yourself to the entire internet? I wouldn't even call it hacking if someone were to get into your system, you are actually inviting them in.

Rather than open all ports, Ragnarok just needs to open up 4500 and 6900. I would suggest you focus on that, rather than making your system the most insecure system on the internet.

---

### Post by Mike'sHardLinux on 2008-04-30
Having ports open is NOT the same as advertising to the internet. In fact, if you have no services listening to any ports, a hacker could ping or do whatever and it wouldn't be any different than having a firewall blocking all ports.

---

### Post by inukaze on 2008-04-30
Oh Ubuntu Brothers this is very hard to solve
I cant , i have desactived the firewalls in that ports, but none works T_T 

Well i think the problem with me LAN , someone can tell me , how to configure the LAN, im client in the "Switch" im a second pc in the lan, someone can give me some of help with LAN and Firewall. to not expose all ports?

---

