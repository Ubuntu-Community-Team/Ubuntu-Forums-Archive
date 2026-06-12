---
title: "&quot;ror: temporary failure in name resolution&quot;"
date: 2005-07-21
forum: Desktop Environments
---

### Post by shadsky_1 on 2005-07-21
Please help, have just recieved ubuntu installation and live cd. Very keen to use however when I try to run live cd goes through heaps and then gets to a section that checks things and I get a fail in red "ror: temporary failure in name resolution" and thats it goes no further just a black screen. I have limited knowlege but can follow any directions or advice on offer. Thank's in advance

---

### Post by eeried on 2005-08-01
I have the same line on my screen but either with the Live CD or the installed Ubuntu this line doesn't seem to cause any further problem.

I have this line on two very different computers: a new laptop, an oldish desktop.

---

### Post by super on 2005-08-01
hopefully this will answer your question:
[http://ubuntuguide.org/#configuringnetwoktooslow](http://ubuntuguide.org/#configuringnetwoktooslow)

it sounds like you network fails to connect to the ntp.ubuntulinux.org servers. this is not a big problem. it should not freeze you boot process tho.  :???:

---

### Post by coolclassic on 2005-08-01
I have the same problem. The problem is caused by the ntp server trying to connect before you having a internet conection. My adsl connection starts automatically after ntp tries to resolve thus having the above error.

Any ideas on how to have either starting before or after to solve problem.

---

### Post by eeried on 2005-08-01
Thanks for the link, super.

However as I have a dial-up connection I'd like to configure ubuntu so that it doesn't attempt to connect at all. How can i do that on a permanent basis?

Is that the role of BUM (see your link): clever stuff if that's so?

Is there no other way like, you know, traditional editing of config files?

Many thanks in advance!

---

### Post by varunus on 2005-08-01
Instead of using bum, you can use the command

```
sudo update-rc.d -f ntpdate remove
```

to manually stop the script from running.

---

### Post by bdash on 2005-09-13
I have the same problem... And I don't want to disable it, because I want my clock to be acurate. Is there any way to change it, to make it happen at the end of the boot process?

---

