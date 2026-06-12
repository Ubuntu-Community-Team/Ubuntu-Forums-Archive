---
title: "How to display IP address on screen in openbox?"
date: 2013-10-30
forum: Desktop Environments
---

### Post by PeterTaps on 2013-10-30
Folks,

My machine has minimal Ubuntu server + openbox. I am very fond of this environment. Gets me do what I want without requiring a full-blown desktop.

Now I am looking at a way to display IP address on the screen. While browsing the Internet, I came across an applet called giplet that could do it. However, it appears I need to install gnome-panel to make it work.

I am wondering if there is a better way to display IP address in the background. The idea is to keep the desktop requirements minimal. 

I guess if there is no better choice, I will install gnome-panel + giplet.

Thank you in advance for your help.

Regards,
Peter

---

### Post by papibe on 2013-10-30
Hi PeterTaps.

How about using conky? See [here]("http://askubuntu.com/questions/321018/setting-up-conky-on-ubuntu"), [here]("https://help.ubuntu.com/community/SettingUpConky") and [here]("http://ubuntuforums.org/showthread.php?t=1771033&highlight=conky").

Regards.

---

### Post by PeterTaps on 2013-10-31
Thank you for introducing me to conky. I have installed conky-all. Can you please tell me where is this legendary VinDSL script that everyone is talking about?

Regards,
Peter

---

### Post by papibe on 2013-10-31
VinDSL is actually an active member of the forum: [VinDSL]("http://ubuntuforums.org/member.php?u=1131082").

Check his posts in the last thread I linked. He both paste code and include file attachments. I'm pretty sure he can give you some pointers if you post specific questions on that thread.

Regards.

---

### Post by deadflowr on 2013-10-31
Here are two different methods to show the IP in conky
The first

```
${execi 1800 wget -q -O - checkip.dyndns.org | sed -e 's/[^[:digit:]\|.]//g'}
```

the 1800 is in seconds, so that means it updates every half-hour.

And the second way involves installing curl
and
```
${execi 1800 curl ifconfig.me}
```

I find either method works fine for me.

Note these are just two ways, there are other ways as well.

---

