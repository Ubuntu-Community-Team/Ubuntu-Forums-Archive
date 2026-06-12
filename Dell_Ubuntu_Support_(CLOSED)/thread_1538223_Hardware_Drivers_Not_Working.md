---
title: "Hardware Drivers Not Working"
date: 2010-07-24
forum: Dell Ubuntu Support (CLOSED)
---

### Post by jterry64 on 2010-07-24
I just installed Ubuntu on a Dell Latitude E6410 laptop. My laptop has an NVidia discrete graphics card, so I had to connect it to an external monitor in order to install it/use it. Following instructions from this blog post, [http://blog.katharsys.com/?p=931](http://blog.katharsys.com/?p=931) , I went to System -> Administration -> Hardware Drivers to find a compatible NVidia driver so I can use my laptop monitor, but every time I go Hardware Drivers, I get the message:

"Downloading package indexes failed, please check your network status. Most drivers will not be available."

and I can't find anything off google that helps.

---

### Post by tkoco on 2010-07-24
Several possibilities:

a restrictive firewall between you and the Internet
the site was down when you attempted to access the list
your Internet connection was down
the DNS server is down or flaky

Just wait a while and try again. See if you can access google.com with Firefox. On my Internet connectivity, the DNS server is flaky. So since I have no control over that puppy, I switched to Google's Public DNS service:

[http://code.google.com/speed/public-dns/]("http://code.google.com/speed/public-dns/")

Good Luck!


> **jterry64 said:**
> I just installed Ubuntu on a Dell Latitude E6410 laptop. My laptop has an NVidia discrete graphics card, so I had to connect it to an external monitor in order to install it/use it. Following instructions from this blog post, [http://blog.katharsys.com/?p=931](http://blog.katharsys.com/?p=931) , I went to System -> Administration -> Hardware Drivers to find a compatible NVidia driver so I can use my laptop monitor, but every time I go Hardware Drivers, I get the message:

"Downloading package indexes failed, please check your network status. Most drivers will not be available."

and I can't find anything off google that helps.

---

