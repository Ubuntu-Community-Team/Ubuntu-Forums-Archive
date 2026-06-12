---
title: "Fuppes and xBox 360..."
date: 2007-11-11
forum: Gaming &amp; Leisure
---

### Post by insineratehymn on 2007-11-11
Ok...

I've successfully installed Fuppes, which seems to be the hard part from all of the posts that Google will show me.

I cannot get my 360 to see my uPnP server, though.

The xBox business from my fuppes.cfg file: 
```
<device name="Xbox 360" virtual="Xbox 360" enabled="true">
      <user_agent>Xbox/2.0.\d+.\d+ UPnP/1.0 Xbox/2.0.\d+.\d+</user_agent>
      <user_agent>Xenon</user_agent>
      <xbox360>true</xbox360>
    </device>
```

The xBox business from my vfolders.cfg file:
```
<vfolder_layout device="Xbox 360" enabled="true">

```

Any ran into this problem? All of the posts I read basically made it seem like its a hard fight to get it installed, but once you do it will just work?

Oh, and I do have the port (#5000) forwarded on my router and there should not be a firewall issue.

Thanks everyone.

---

### Post by insineratehymn on 2007-11-26
bump?

---

### Post by lmellor on 2007-12-02
bump, also having the same problems, I have followed all the instructions I can find on here but still my 360 cannot find my upnp server, any suggestions?

---

### Post by Mike'sHardLinux on 2007-12-02
If your server and your xbox are both on your lan, you don't need to forward any ports on your router. Forwarding ports on your router is for the purpose of making services available to the wan/internet.

Do you have a firewall running on the fuppes server? If so, you probably need to open the port on the firewall on the fuppes server.

---

### Post by lmellor on 2007-12-02
I am not running any firewall on ubuntu as far as I know (unless it comes with one), any other suggestions, I'm beginning to think that everybody else is just winding me up and that it's not actually possible.  Would love to be proven wrong however.

---

### Post by lmellor on 2007-12-04
For anybody who is at the same point as I was then the answer lies in this thread...

[http://ubuntuforums.org/showthread.php?t=618781]("http://ubuntuforums.org/showthread.php?t=618781")

Thankfully somebody knew what was wrong and more importantly how to fix it!

---

