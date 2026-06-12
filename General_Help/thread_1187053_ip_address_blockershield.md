---
title: "ip address blocker/shield?"
date: 2009-06-14
forum: General Help
---

### Post by biff_bobbo on 2009-06-14
Hello
I am looking for an IP address shield program to keep my ip address private. Can anyone recommend one to me, or help me find one? 

I am running the latest ubuntu operating system.

---

### Post by lamego on 2009-06-14
There is no such thing as an IP address blocker/shield, the only way to prevent your own IP address from being known when accessing network services it to use a network proxy for such services.
There are some tools which provide anonymous proxy integration, for example [www.torproject.org]("http://www.torproject.org/").

---

### Post by twright on 2009-06-14
Generally most programs advertising this for Windows are completely useless and unless you live in china/are doing something worth hiding then it is probably not worth bothering - your IP address is public information and if you are a heavy user of bittorrent then the speed loss of something like tor makes the option less viable.

---

### Post by lovinglinux on 2009-06-14
I'm not sure if this is what you are looking for, but If you want an ip blocker like Peerguardian for Windows, then you could install [moblock](http://moblock-deb.sourceforge.net/) or [iplist](http://iplist.sourceforge.net/). They both work great (better than Peerguardian in my opinion).

Unfortunately, it is a common misconception that ip blockers help to hide your IP or to make it private. Well, they don't. What they do (and do well) is to block connections to a list of known ip addresses. Most torrent applications like Deluge, Transmission and uTorrent also have a ip blocklist feature, which essentially protect you the same way, but only at the torrent client level. Moblock and iplist are more secure because they protect your entire network connections, not only torrent related.

If you are seeking for anonymity, then you might want to use TOR as already mentioned, but it has it's own limitations/flaws and are not recommended for high bandwidth traffic.

---

### Post by biff_bobbo on 2009-06-14
help to install TOR...
I'm lost and I don't udnerstand how to do this. 

[http://www.torproject.org/download-unix.html.en](http://www.torproject.org/download-unix.html.en)
from here I click the top one on the list, which says ubuntu (noreply...)

that puts me here:
[https://wiki.torproject.org/noreply/TheOnionRouter/TorOnDebian](https://wiki.torproject.org/noreply/TheOnionRouter/TorOnDebian)

and I have no idea what to do now

(i'm a lamen, please help)

---

### Post by Soul-Sing on 2009-06-14
: [http://www.torproject.org/index.html.en](http://www.torproject.org/index.html.en)
: [http://www.torproject.org/documentation.html.en](http://www.torproject.org/documentation.html.en)

Better not running it in a relay. I recommend privoxy and vidalia as addit. software, vidalia as a gui.

---

### Post by biff_bobbo on 2009-06-14
> **leoquant said:**
> : [http://www.torproject.org/index.html.en](http://www.torproject.org/index.html.en)
: [http://www.torproject.org/documentation.html.en](http://www.torproject.org/documentation.html.en)

Those links don't help me? Please... I need help for installation as I don't understand those sites.

I don't understand what you said:
> Better not running it in a relay. I recommend privoxy and vidalia as addit. software, vidalia as a gui.

Can you explain? (I'm a laymen... please simplify your terms, I haven't been using ubuntu for very long)

---

### Post by Soul-Sing on 2009-06-14
jaunty: synaptic: tor and privoxy. I believe vidalia is in it also.
install them.

Open Privoxy's "config" file (look in /etc/privoxy/ or /usr/local/etc/) and add the line
forward-socks4a / 127.0.0.1:9050 .
to the top of the config file. Don't forget to add the dot at the end. 

: [https://wiki.torproject.org/noreply/TheOnionRouter/TorifyHOWTO/WebBrowsers](https://wiki.torproject.org/noreply/TheOnionRouter/TorifyHOWTO/WebBrowsers)
To adjust your browser.

Open vidalia.

---

### Post by biff_bobbo on 2009-06-14
> **leoquant said:**
> jaunty: synaptic: tor and privoxy. I believe vidalia is in it also.
install them.

Open Privoxy's "config" file (look in /etc/privoxy/ or /usr/local/etc/) and add the line
forward-socks4a / 127.0.0.1:9050 .
to the top of the config file. Don't forget to add the dot at the end. 

: [https://wiki.torproject.org/noreply/TheOnionRouter/TorifyHOWTO/WebBrowsers](https://wiki.torproject.org/noreply/TheOnionRouter/TorifyHOWTO/WebBrowsers)
To adjust your browser.

Open vidalia.


Please...
I don't understand how to install these programs. I am used to windows with installation files where you double click and hit a few 'next' buttons and you're done. I don't know what I'm doing with all this stuff. I appreciate your help but will you please explain the installation in babysteps?

---

### Post by Soul-Sing on 2009-06-14
If you are really new to linux/ubuntu, i do not recommend this software to be fair and honest. Really this has to be done with some reading and some patience.......

---

### Post by biff_bobbo on 2009-06-14
> **leoquant said:**
> If you are really new to linux/ubuntu, i do not recommend this software to be fair and honest. Really this has to be done with some reading and some patience.......

Is there no simpler way to achieve this goal?
An IP shield browser add-on or something?

I just want to block my IP address for logging onto my friend's forum to play a joke on her, because she knows my IP from gaming.

---

### Post by lovinglinux on 2009-06-14
> **biff_bobbo said:**
> Is there no simpler way to achieve this goal?
An IP shield browser add-on or something?

I just want to block my IP address for logging onto my friend's forum to play a joke on her, because she knows my IP from gaming.

Use a web proxy like [http://hidemyass.com](http://hidemyass.com)

---

### Post by Fatman22 on 2009-07-04
Hi, I am currently using TOR and was wondering if there is any reason to use Moblock or iplist also?

BTW I have installed GUFW installed also.

---

### Post by Soul-Sing on 2009-07-05
> **Fatman22 said:**
> Hi, I am currently using TOR and was wondering if there is any reason to use Moblock or iplist also?

BTW I have installed GUFW installed also.

I believe it is possible to integrate ip-list into GUFW. You should take a look at the GUFW project on launchpad: questions and answers.

---

### Post by lovinglinux on 2009-07-05
> **Fatman22 said:**
> Hi, I am currently using TOR and was wondering if there is any reason to use Moblock or iplist also?

BTW I have installed GUFW installed also.

You can but...

I don't know exactly how TOR works. I tried it once, but there was a lot of connections coming and going all the time, so I didn't like it. I suppose I was acting as a node or something, but I'm not quite sure. Anyways, assuming that you computer is not a node, using TOR with a blocklist would be useless, because you will never contact the destination directly. Your connections will pass through a series of TOR nodes before reaching the destination, so the only ip addresses that the blocklist will be able to block are in fact from other computers on the TOR network.

Keep in mind that some of the blocklists that are optionally available on moblock and iplist includes several TOR ip ranges. So if you use them, you will end up blocking the TOR nodes you are using to reach the destination ip.

I don't know what are you trying to achieve. TOR is an anonymity tool while moblock and iplist are security tools, that prevent known bad ip addresses from connecting to you. If you think you should block TOR computers from reaching your machine, then you shouldn't use TOR. 

You should also consider that has it's on privacy/security issues. Take a look at:

[http://en.wikipedia.org/wiki/Tor_%28anonymity_network%29#Weaknesses](http://en.wikipedia.org/wiki/Tor_%28anonymity_network%29#Weaknesses)
[https://www.torproject.org/download.html.en#Warning](https://www.torproject.org/download.html.en#Warning)
[https://wiki.torproject.org/noreply/TheOnionRouter/TorFAQ](https://wiki.torproject.org/noreply/TheOnionRouter/TorFAQ)

---

