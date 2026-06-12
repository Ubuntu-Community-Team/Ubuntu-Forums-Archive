---
title: "Ubuntu Connects to Wireless Network Very Slowly"
date: 2009-07-28
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Tykin on 2009-07-28
My Dell Mini 9 connects to my work's hidden, WPA Enterprise network very slowly. 

While my Windows partition takes a couple seconds to connect, Ubuntu takes well over a couple minutes.

This is also the case in my home network.

I think the problem lies somewhere in the Gnome Network Manager. I tried switching to wicd and I connect much faster to my home network (within a few seconds). Unfortunately, I cannot connect to the hidden WPA2 Enterprise network at my job with wicd.

Is there some setting I can change in Networkmanager which allows faster connections to wireless networks? Alternatively, is there a network manager which would allow me both speed and accessibility to a hidden, secured network?

Thanks for the help!

---

### Post by Tykin on 2009-07-30
bump

---

### Post by FirstByté on 2009-07-30
can you post the output of your 

```

~$ lshw -C network

```

---

