---
title: "Wireless internet connection *NEWBIE*"
date: 2005-11-27
forum: Desktop Environments
---

### Post by jaboc83 on 2005-11-27
Hi, I've had Ubuntu running for roughly a day now, and I love it, but I'm not sure how to get my internet running. I have an hp pavilion zv5000 notebook, running a dual boot of ubuntu and Windows XP I connect wirelessly to the internet in our home through our Linksys router. If you need more info let me know. Any help is greatly appreciated.

- Jake (Linux Newb)

---

### Post by ubuntuuser on 2005-11-27
You are probably looking for ndiswrapper. 
[Look here.]("http://ubuntuforums.org/showthread.php?t=91732&highlight=ndiswrapper+howto") This is a very complete step-by-step tutorial.

EDIT:
This works of course not only with Belkin adapters, but with all NDIS-compliant interfaces (yours very likely is). Just replace rt2500usb.inf with the correct filename ;-)

---

### Post by jaboc83 on 2005-11-27
Thanks, I'll give that a shot!

---

### Post by jaboc83 on 2005-11-27
Either I did this wrong or that didn't work. Here's the output from the terminal.

[COLOR="Red"]~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~[/COLOR]
ndiswrapper -l    [COLOR="Red"]//input[/COLOR]
Installed ndis drivers:      [COLOR="Red"]//output[/COLOR]
bcmwl5.sys	invalid driver!

I saved the session as a script so ask me if you need more detail, but this seemed fairly important. The bcmwl5.sys file is the windows driver being used according to my device manager.

I should probably note that I have a broadcom 802.11 b/g WLAN in my notebook. It's not a USB wireless adapter.

[COLOR="Red"]~~ THOUGHTS??~~~[/COLOR]

---

### Post by Zotova on 2005-11-27
> ndiswrapper -l //input
Installed ndis drivers: //output
bcmwl5.sys invalid driver!

There should be a .inf file. The command you enter into the terminal should be:

```
ndiswrapper -i drivername.inf
```

Not a .sys file.

Hope that helps.

Edit - replace 'drivername.inf' with the name of your driver btw

---

### Post by jaboc83 on 2005-11-27
Thanks a bunch, I'm replying to via ubuntu on my wireless connection.:p 
All is good now. 

I appreciate the timely responses,

---

