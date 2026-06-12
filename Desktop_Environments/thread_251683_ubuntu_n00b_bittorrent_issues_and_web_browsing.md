---
title: "ubuntu n00b bittorrent issues and web browsing"
date: 2006-09-05
forum: Desktop Environments
---

### Post by naes341 on 2006-09-05
Hello folks. Ive been running ubuntu for about a month now. First of all, this is the best linux distro I have ever used. Im a convert now. Windows is but a bad memory. I do have two questions however. One is I have noticed that bittorent cannot share files. I can dl, but no upload. Some of the sites I like tend to frown on this. The windows computers on my network at home can share without issue. I have no idea where to start. I have not configured any firewalls at this point. Also I have noticed that firefox is very slow when resolving DNS, is there a setting I am over looking? Im running an inspiron 8600 with the stock intel wireless.

---

### Post by naes341 on 2006-09-07
Ive been looking into this, and still cant figure out what is going on. Anyone have any ideas?

---

### Post by skymt on 2006-09-07
Do you use the official Bittorrent client that comes with Ubuntu? If so, don't. Use Azureus, KTorrent, or Transmission. If you use a router, you should also forward whatever ports you use for Bittorrent. By default, with the official client, that's 6990-6999. Many unofficial clients use just 6990.

For the slow DNS, try [disabling IPv6](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4).

---

### Post by naes341 on 2006-09-07
Yea, Im using azurius. The funny thing is that I dont port forward on my router for my win clients, or mac OSX clients...

---

### Post by distroman on 2006-09-08
That's most lightly because of UPnP support with win and os x.   
Try firestarter, it's a GUI for the iptables.
[http://www.fs-security.com/](http://www.fs-security.com/)

---

### Post by skymt on 2006-09-08
Ignore Firestarter. All you need to is forward your ports.

---

### Post by distroman on 2006-09-08
> Ignore Firestarter. All you need to is forward your ports.
Please explain how and which ports to forward. Would be brilliant, because I am in the dark. 
Help me out please? Need your advice.
Thank you.

---

### Post by tribaal on 2006-09-08
On the firefox side of your post, did you try to disable ipv6 resolution in firefox's config? That did the trick for me:

- open firefox
- type in "about:config" in the url
- type in "ipv6" in the "filter" box
- there is only one key returned, double click it (so that it becomes "true")
- restart firefox
- enjoy :)

Hope this helps :)

- trib'

---

### Post by distroman on 2006-09-08
brilliant :D

---

### Post by skymt on 2006-09-08
Forwarding ports is different for each model of router, so I can't help you with the specifics. You should see the manual for your router for details.

In general, though, you need to connect to your router in a web browser (often 192.168.1.1 or 192.168.0.1), go to the port forwarding page, and set it up to forward ports 6990-6999.

---

### Post by distroman on 2006-09-08
I can only referrer to this. 
[http://www.ubuntuforums.org/showthread.php?t=253482](http://www.ubuntuforums.org/showthread.php?t=253482)

---

### Post by Cynical on 2006-09-08
Thats odd, azureus works the same for me in linux as it does in windows.

Try going to [http://www.portforward.com](http://www.portforward.com) and finding your router model, they have step by step tutorials with pictures showing you how to do it.

---

### Post by naes341 on 2006-09-09
> **tribaal said:**
> On the firefox side of your post, did you try to disable ipv6 resolution in firefox's config? That did the trick for me:

- open firefox
- type in "about:config" in the url
- type in "ipv6" in the "filter" box
- there is only one key returned, double click it (so that it becomes "true")
- restart firefox
- enjoy :)

Hope this helps :)

- trib'
  
BINGO! Thank you very much.If anyone else is having this issue, it worked for me!

---

### Post by naes341 on 2006-09-09
> **distroman said:**
> That's most lightly because of UPnP support with win and os x.   
Try firestarter, it's a GUI for the iptables.
[http://www.fs-security.com/](http://www.fs-security.com/)

I dont have UPuP enabled on my router, it struck me as being a bit insecure....

---

