---
title: "P2P/Torrent application and security."
date: 2006-06-24
forum: Desktop Environments
---

### Post by Village Idiot on 2006-06-24
I would like to install a P2P/Torrent app but I'm concerned about security. Would I need a firewall? Are there any changes I can make to lock down Ubuntu? I don't like using torrents because I tried it in Winblows and it was very slow, I had better luck with P2P namely, Sharaza. My Winblows system is very secure but I'm green when it comes down to securing a Linux machine. I would very much apreciate any help on this matter....Thank You!

---

### Post by Tuxman on 2006-06-24
You can try this firewall, [http://ubuntuguide.org/wiki/Dapper#How_to_install_Firewall_.28Firestarter.29](http://ubuntuguide.org/wiki/Dapper#How_to_install_Firewall_.28Firestarter.29)

Tried Azureus?
[http://ubuntuguide.org/wiki/Dapper#How_to_install_P2P_BitTorrent_Client_.28Azureus.29](http://ubuntuguide.org/wiki/Dapper#How_to_install_P2P_BitTorrent_Client_.28Azureus.29)

---

### Post by FredB on 2006-06-24
[QUOTE=Tuxman]You can try this firewall, [http://ubuntuguide.org/wiki/Dapper#How_to_install_Firewall_.28Firestarter.29](http://ubuntuguide.org/wiki/Dapper#How_to_install_Firewall_.28Firestarter.29)

Tried Azureus?
[http://ubuntuguide.org/wiki/Dapper#How_to_install_P2P_BitTorrent_Client_.28Azureus.29](http://ubuntuguide.org/wiki/Dapper#How_to_install_P2P_BitTorrent_Client_.28Azureus.29)[/QUOTE]

Firestarter is a User Interface for the kernel-embedded firewall named iptables.

And azureus is a great tool. Just add SafePeer plugins, and you'll have a great tool to do some P2P. Legal P2P, of course ;)

---

### Post by Village Idiot on 2006-06-24
Hey guys!....Thanks for the advice and quick reply! I tried to install Azureus with Sun Java but I boched it!:confused: [http://ubuntuforums.org/images/smilies/confused.gif](http://ubuntuforums.org/images/smilies/confused.gif) I did find a few places with instructions and I'll try it again. Are there any P2P clients that don't require java? I'm also going to install Firestarter!

---

### Post by FredB on 2006-06-25
[QUOTE=Village Idiot]Hey guys!....Thanks for the advice and quick reply! I tried to install Azureus with Sun Java but I boched it! :confused:  I did find a few places with instructions and I'll try it again. Are there any P2P clients that don't require java? I'm also going to install Firestarter![/QUOTE]

Can you be more precise what happened with Java and Azureus ?

Azureus is the most complete. You can try also bit tornado - you can add it with Synaptic (don't forget to activate universe and multiverse repositories).

Hope it help ;)

---

### Post by Winblowz on 2006-06-25
[QUOTE=Village Idiot]Hey guys!....Thanks for the advice and quick reply! I tried to install Azureus with Sun Java but I boched it!:confused: [http://ubuntuforums.org/images/smilies/confused.gif](http://ubuntuforums.org/images/smilies/confused.gif) I did find a few places with instructions and I'll try it again. Are there any P2P clients that don't require java? I'm also going to install Firestarter![/QUOTE]
When you installed Sun Java did you use "apt-get install sun-java5-jre"? If so, did it present the Sun license to you? If it DID NOT present the license, then you must do "dpkg-reconfigure debconf" and make it so license's are shown in the terminal. 

As for your second question, if you use KDE, then KTorrent is an awesome bittorent client. Although, its qt, so if you're using Gnome it wouldn't blend well. I'd have to say though, that (in my opinion) other than, KTorrent, Azureus is the best bittorent client around;)

---

