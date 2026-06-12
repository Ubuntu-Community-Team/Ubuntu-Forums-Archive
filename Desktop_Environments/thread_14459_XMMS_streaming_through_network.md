---
title: "XMMS streaming through network?"
date: 2005-02-07
forum: Desktop Environments
---

### Post by alvinistic on 2005-02-07
Hello Ubuntuers!

I've installed XMMS through synaptic. I like it a lot. The only downside is i found that my installed XMMS can't play the mp3 files in my (Windows) network. It also can't play mp3 files in my Windows XP partition which I access with samba. But, it can play any mp3 files in my current partition.

So, did i miss something? Oh yeah, for information, I use proxy here. 

Thx in advance for the help!

---

### Post by alvinistic on 2005-02-12
Anyone???

Pls help.....

Thx in advance.

---

### Post by dahifi on 2005-02-12
are you having any problems with internet sites? online radio stations?  do you have the same problem with .pls sites or .m3u?  what about playing an mp3 off the web like this site:  [http://soundhog.gybo.org/as%20heard%20on%20radio%20soundhog%20vol%205%20-%2033%20problems.mp3](http://soundhog.gybo.org/as%20heard%20on%20radio%20soundhog%20vol%205%20-%2033%20problems.mp3)

I was able to play it all until today when I was trying to reinstall mplayer and installed the mozilla-mplayer plugin.  now i can play mp3s, but not any pls or m3u files..

---

### Post by drasko on 2005-02-12
>I've installed XMMS through synaptic
not important in this case...

>It also can't play mp3 files in my Windows XP partition which I access with samba. 
? Can't you just see your partition as in /dev directory - mout the partition and read it directly (prosuming that kernel is configured for ntfs support, which usually is).


I suspect on the proxy firewall, cose I doubt that streamong goes through 8080 port (http proxy). Try using the realplayer, I think it can go through the http proxy, so you'll skip the firewall.

Drasko

---

### Post by DidRocks on 2005-06-26
I don't know if you have still this pb, but i think it can be useful for someone else :

Preferences->Audio I/O plugins->MPEG Layer 1/2/3
Player->Configure->Streaming->Proxy

cheers,

Did

---

