---
title: "Inspiron 530n with Ubuntu internet connection problem"
date: 2008-11-06
forum: Dell Ubuntu Support (CLOSED)
---

### Post by arashpa on 2008-11-06
Hello all,

 

I have just bought an Inspiron 530n with Ubuntu installed on it. My ethernet connectin is broadband with static IP address. I think I have set it up correctly but the internet connection is either very very slow or nonfunctional. When I ping the roundtrip travel numbers look fine so my guess there is something wrong with the ethernet driver or setup. I have disabled ipv6 in case that was causing the problem but it didn't help. nslookup seems healthy as well. Any one has seen a similar problem or has a clue? 

 

Thanks,

Arash

---

### Post by sirebral on 2008-11-06
What Driver are you using?

You can find that by right-clicking on your connection icon in the taskbar and then clicking on Connection Information.

You might need to update a driver.

Are you using NDSIWrapper (I forget that software)?  If you are, it works but it caused me a lot of problems.  You might have luck adding the Dell Back ports.  I used those to fix my WiFi light on my laptop, so I might be able to find the repository for those.

---

### Post by arashpa on 2008-11-07
Sirebral,

Thanks for the reply. The connection information is not active in my setup. I guess I don't have the driver installed properly. 

Arash

---

### Post by arashpa on 2008-11-11
Well, I found the solution and will just post it here in case others were in a similar situation. As I found in one other forum Network Manager doesn't like static IPs!! I don't know why! I uninstalled Network Manger and installed wicd and it works fine!

Arash

---

