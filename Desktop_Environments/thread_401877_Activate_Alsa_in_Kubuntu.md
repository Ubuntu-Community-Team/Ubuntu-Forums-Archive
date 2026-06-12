---
title: "Activate Alsa in Kubuntu"
date: 2007-04-05
forum: Desktop Environments
---

### Post by jackn on 2007-04-05
Need to get an "Intel HD audio" sound card working on my laptop. 
[URL="http://www.rothlaender.net/a8js.html"]
The solution[/URL] to this issue is available, and it consists of adding a line to your /etc/modprobe.d/alsa-base. This seems to do the job for many users.

When I try to apply this modification on my Kubuntu-run laptop, however, I still don't get sound. 

I think this is related to the fact that KDE uses its own sound control, and that I need to run Alsa. I've tried doing that off of the 'sound' section of the 'system settings', but no luck.

Am I right about this and, if so, how can I get Alsa to run sound in Kubuntu?

Thanks,
Jackn

---

### Post by Storm Rider on 2007-04-05
In a terminal:
**sudo alsaconf**

---

### Post by jackn on 2007-04-05
Thank you for the prompt response, Storm Rider. 

I don't have 'alsaconf' ('command not found'). This seems to be a common occurrence on the net, but I haven't found a solution.
I've downloaded [alsaconf ]("/etc/modules.d/alsa")from the alsa.org site. Upon running it (it's a shell script), I got an error message...

I've also read that it's a part of alsa-utils. Yet, I cannot find alsaconf anywhere near an alsa-utils directory. When I try to apt-get install alsa-utils, I'm told it's already the newest version.

While looking at stuff following your answer, I've found the alsactl file. It allows you to run
```

alsactl restore
```

which, miraculously, resotored sound to my laptop.

However, it also spat out these error messages:```

:~$ alsactl restore
alsactl: set_control:894: warning: name mismatch (IEC958 Playback Con Mask/Channel Mode) for control #29
alsactl: set_control:896: warning: index mismatch (0/0) for control #29
alsactl: set_control:994: bad control.29.value type
```

And I doubt I get proper sound. I also can't control the volume with the KDE desktop mixer or with the media buttons of my laptop...

In short, great improvement, but I feel there must be a better way of going about it, and that I'm far from getting the full power of the Intel HD audio sound card.

Thank you, and would love more input on the above.
Jackn

---

