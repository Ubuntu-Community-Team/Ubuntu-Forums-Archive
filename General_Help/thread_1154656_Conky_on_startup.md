---
title: "Conky on startup"
date: 2009-05-10
forum: General Help
---

### Post by mike0020 on 2009-05-10
When I added conky to startup it stopped working properly. It now goes in font of windows and has a shadow border to it when it should look like it's just a part of my desktop, how can I fix this so it doesn't happen again?

---

### Post by j.m.wilson@earthlink.net on 2009-05-10
I am having the same problem since upgrading to Jaunty

---

### Post by mike0020 on 2009-05-10
Can anyone help?

---

### Post by LesterPalooza on 2009-05-11
Had the same problem but the script here on this link solved it. Just put a delay when you logon, wait for 10 seconds or so, before you start conky. Check out this link:

[http://ubuntuforums.org/showthread.php?t=386078]("http://ubuntuforums.org/showthread.php?t=386078")

---

### Post by mike0020 on 2009-05-12
> **LesterPalooza said:**
> Had the same problem but the script here on this link solved it. Just put a delay when you logon, wait for 10 seconds or so, before you start conky. Check out this link:

[http://ubuntuforums.org/showthread.php?t=386078]("http://ubuntuforums.org/showthread.php?t=386078")

That doesn't seem to be working for me.

---

### Post by zyxyellowxyz on 2009-05-14
> **mike0020 said:**
> That doesn't seem to be working for me.

.conky_start.sh
```
#!/bin/bash
sleep 20 && conky;
```

add that to your start-up applications

delays the start-up of conky by 20 seconds, good for when compiz in enabled. Speaking of Compiz, that's what is causing the shadow. [Check out this post and it will explain what to do.]("http://ubuntuforums.org/showpost.php?p=6994155&postcount=4")
Hope that helps!

---

### Post by mike0020 on 2009-05-16
I figured out why it wasn't working, I needed to make the file executable. Once I did that conky started up correctly. Thanks everyone.

---

### Post by Tiler on 2009-06-01
I have my startup script created and permissions set on it but it won't launch from startup.  Any suggestions?

I can run the script from terminal but neither .startconky nor ~/.startconky work in the Startup Applications command line and I am a little perplexed.

---

