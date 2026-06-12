---
title: "Location of kernel source code"
date: 2006-09-13
forum: Desktop Environments
---

### Post by aswells on 2006-09-13
I need some help. When installing the Cisco VPN client, it asks me where the directory containing linux source code is. Could someone tell me where I might find this? I am currently using Ubuntu Dapper Drake 6.06.

---

### Post by aswells on 2006-09-13
bumb. Anyone know? Is this something I already have or something I need to get?

---

### Post by lamego on 2006-09-13
You are more likely to just need the kernel headers, install with:
```
sudo apt-get install linux-headers-$(uname -r)
```

If you do need the linux source code:
```
sudo apt-get install linux-source
```

Please note that after installing the source you will need to uncompress it:
```
cd /usr/src/
sudo tar xvf linux-source-2.6.15.tar.bz2
sudo ln -s linux-source-2.6.15 linux
```

---

### Post by aswells on 2006-09-13
Yep, I read it again and all I need is the headers. I got 2 packages with the code you gave me, ill play around with it until I get it working. Thanks for the help!

EDIT: Ok, I lied. The 2 packages I got are linux-headers-2.6.15-26 and linux-headers-2.6.15.26-386

How do I know which set of headers my system is using, or does it make a difference? What are the differences between the two?

---

### Post by nrwilk on 2006-09-13
I promise you that you'll have a better time with it if you do NOT use Cisco's client.

Instead, use vpnc.  Not only do you not need to install extra kernel stuff, but it is a MUCH better, more solid client under linux.

For a little mini-tutorial check out this post:
[http://ubuntuforums.org/showpost.php?p=1450704&postcount=5](http://ubuntuforums.org/showpost.php?p=1450704&postcount=5)

nrwilk

---

### Post by aswells on 2006-09-14
After installing vpnc, I started it up and ran the program using the cli interface. I am more than happy with vpnc, as it connected much faster than ciscos vpn client ever did on windows. Thanks for the tip!

---

### Post by nrwilk on 2006-09-14
> **aswells said:**
> After installing vpnc, I started it up and ran the program using the cli interface. I am more than happy with vpnc, as it connected much faster than ciscos vpn client ever did on windows. Thanks for the tip!

I'm glad you found it to be better than Cisco's.  I think most people do.  It's lighter, faster, and more stable.

In case you didn't read that link I posted, I'd also like to point out that there is a graphical front-end for vpnc called kvpnc.  But, I found it to be extremely unstable.  To the point of being unusable.  Also, it actually makes the whole process more complicated and longer.  It's so simple to use the CLI vpnc that I don't even see any need for the front-end.

I'm glad I could help! :D 

nrwilk

---

