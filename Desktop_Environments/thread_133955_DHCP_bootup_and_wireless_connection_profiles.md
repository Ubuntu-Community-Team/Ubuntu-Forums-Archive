---
title: "DHCP bootup and wireless connection profiles"
date: 2006-02-21
forum: Desktop Environments
---

### Post by Xerak on 2006-02-21
Hello,

I've got one main problem with Ubuntu, it's always trying to connect to my network on bootup, which can bring very long time-outs until it fails. I've got a wireless  laptop and I'm connecting from different places, which means half of the time the last connected network won't be valid next time I start Ubuntu.

Is there an *easy* way to disable network connection on Ubuntu startup. I know I could maybe disable all interfaces before I log out, but this is not what I've got on mind :-)

Also, related question, it seems that the default wireless network manager with Ubuntu doesnt "remember" the connection settings for different wireless networks. So I have to re-enter manually info for different networks. Is there a way to make Ubuntu remember a config based on the network's name?

Any help appreciated, thanks.

---

### Post by alamba on 2006-02-21
Long boot up time: ctrl+c

Wireless network managment: network manager package (I think - there was a post on this sometime ago, maybe a search would give u more detailed response)

A

---

### Post by soonindallas on 2006-02-21
[QUOTE=Xerak]
Is there an *easy* way to disable network connection on Ubuntu startup. I know I could maybe disable all interfaces before I log out, but this is not what I've got on mind :-)[/QUOTE]

I know what you mean.  I don't know of one.  I use ctrl-C to skip this step when I know I'm going to use a different interface from the one I was using when I closed the previous session.



[QUOTE=Xerak]Also, related question, it seems that the default wireless network manager with Ubuntu doesnt "remember" the connection settings for different wireless networks. So I have to re-enter manually info for different networks. Is there a way to make Ubuntu remember a config based on the network's name?[/QUOTE]

I use the gtkwifi applet (see forum on 3rd party apps) for storing info (essid, wep keys, etc) for multiple networks and switching between them.  I like this one, there are others eg wifiradar etc.

---

### Post by Xerak on 2006-02-21
Thanks a lot!

---

### Post by brentoboy on 2006-03-04
Is it possible to tell ubuntu about all the ESSIDs that I normally connect to, along with thier WEP keys, and then, when it boots, have it go through the list and connect to the first one that it finds?

I too move from place to place between wifi sessions, and each network has its own ins and outs, so I have to reconfigure each one over and over - it is kind of anoying.

it looks like gtkwifi still needs me to interact, rather than just tell it all the options beforehand, and have the computer do the best thing wihtout interaction once it is setup correctly.

Anyone have any ideas on this?

---

### Post by charlie3 on 2006-05-04
[QUOTE=Xerak]

Is there an *easy* way to disable network connection on Ubuntu startup. 

Also, related question, it seems that the default wireless network manager with Ubuntu doesnt "remember" the connection settings for different wireless networks. So I have to re-enter manually info for different networks. Is there a way to make Ubuntu remember a config based on the network's name?
[/QUOTE]

I found a document in debian that describes this and has a workaround. I don't know how universal it is.

go to [http://www.vollink.com/gary/deb_wifi.html](http://www.vollink.com/gary/deb_wifi.html)

charlie3

---

