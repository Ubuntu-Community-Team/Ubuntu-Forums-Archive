---
title: "aMule 2.1.3"
date: 2007-08-14
forum: Desktop Effects &amp; Customization
---

### Post by cape_town on 2007-08-14
Hello everybody,

I am a new user of Ubunty 7.04 - the Feisty Fawn. I have installed in my laptop aMule but I don't know to configure Connect. 
Could you please tell me the data which I should insert in the fields (server, port, etc) in order to connect aMule, and to make it functional?

All the best,

cape_town

---

### Post by Hallvor on 2007-08-14
Hi, just choose a couple of servers from this list:

[http://gruk.org/list.php](http://gruk.org/list.php)

Donkeyserver 2 has IP 62.241.53.16 with port 4242. That should be all you need to connect.

You also may want to open the correct ports, since you will get a low id if you don`t and your downloads will be slower. Open a terminal and type 

> sudo iptables -A INPUT -p tcp --dport 6881 -j ACCEPT to open tcp on port 6881. 

> sudo iptables -A INPUT -p udp --dport 6881 -j ACCEPT to open udp on port 6881. 

To close these ports, try:

> sudo iptables -A INPUT -p tcp --dport 6881 -j DROP

and 

> sudo iptables -A INPUT -p udp --dport 6881 -j DROP

Using different ports for tcp and udp is recommended.

---

### Post by bricksen on 2007-08-14
I keep getting that kad is firewalled how can I stop this from happening?
ED2K works fine

---

### Post by Hallvor on 2007-08-14
It is possible that you don`t have enough sources yet, and that you get a false positive. Try downloading a few popular files and see if the arrow turns green. KAD is probably fine.

---

### Post by bricksen on 2007-08-14
I tried and it suddenly went "kad is off" :confused:

---

### Post by Hallvor on 2007-08-14
Strange. Some people have reported trouble with kad if they are behind routers. The problem *may* be solved by opening an udp port for extended server requests. This is always your udp-port + 3, so that is the port you should open. (Look under connection - preferences to see what your udp-port is and do the math to find the port for extended server requests). Then open it as shown above. Hope it helps. :)

---

### Post by bricksen on 2007-08-14
I tried that to and used your commands from the tread and open for 3881 and 3884
but when i restarted amule it was reset to 35672 or something.

---

### Post by bricksen on 2007-08-14
it's also very slow 2.5 down and i get 275 in xp with the same settings :confused:

---

### Post by Hallvor on 2007-08-15
Perhaps a silly question, but you did click "OK" after you changed the ports? If you still can`t make it work, press Alt+Home to enter your home directory. Then, press Ctrl+h to show hidden files. Enter the .aMule directory and open the amule.conf file with a text editor.

Look for this: 

Port=35672(?) (This is the tcp-port)
UDPPort=35673(?) (This is the UDP-port)

and change it to what you like:
Port=3880
UDPPort=3881

Save and exit. In addition you have to open the udp+3 port in iptables and on your router..

I assume you have opened and forwarded the ports in your router (if you have one).

The speed depends on how many sources the file has, how many connections your router/modem can handle and if you are firewalled. But I can tell you this, if you download at an average of 275kb/s in Windows, you are probably leeching your @ss off. Whatever you download must be uploaded somewhere else, and if you download large amounts of data while uploading much less, the network is actually better off without you. Please, always upload as much as you download... :)

---

### Post by misfitpierce on 2007-08-15
Donkey Server 1 and 2 are best bets as well :)

---

### Post by Hallvor on 2007-08-15
Have to agree there :)

---

### Post by bricksen on 2007-08-20
Sorry been away for awhile
Didn't do it for me and yes I did confirm the port-change but it seems that anything I do resets the next time I start amule.
So my question is how to set the right permissions for this program. I used sudo to install and tweah it??

---

### Post by hidden_leaf_sasuke on 2007-08-20
why dont you use gtk-gnutella? its much faster..:)

---

### Post by Hallvor on 2007-08-20
> **bricksen said:**
> Sorry been away for awhile
Didn't do it for me and yes I did confirm the port-change but it seems that anything I do resets the next time I start amule.
So my question is how to set the right permissions for this program. I used sudo to install and tweah it??

It is a bug, then. Just try editing the amule.conf file in your .aMule directory. From your desktop, press Alt+Home to launch the home directory, and then Ctrl+h to show hidden files. Click the .aMule directory and open amule.conf with a text editor. Change the ports there, save and exit. Start aMule.

hidden_leaf_sasuke: That is just an illusion. The gnutella network seems to be faster because the users tend to share fewer and smaller files. Therefore, the queue turnaround increases. Bittorrent, on the other hand, is fast because the upload capacity is concentrated on a single file. But the average torrent lives a short and violent life. For larger and popular files, especially if downloading several at once, aMule can be just as fast as a public tracker on Bittorrent.

---

### Post by bricksen on 2007-08-21
Thanks alot and it actually workes :KS
I only use kad and that thing with the firewall is beaten.
A bit left to the speed i got in xp though but i run that on another pc so it's not that big a problem and I have to run that anyway cause of a lot of musicprograms that runs poorely under wine. sonar 6 etc....

And to the gtk-gnutella fans: if you only listen to listpop that is probably a good solution but I seldom find anything of interest there :) but thanks anyway

---

### Post by Hallvor on 2007-08-21
You are welcome. Glad it worked.

I`ve had some issues running Kad alone in aMule. In my experience, it does not perform as well as in eMule.

Actually, overall performance in aMule is not that bad. Yes, some eMule mods in Windows are lightning fast, but you still have to reboot every other day! :lolflag:

---

