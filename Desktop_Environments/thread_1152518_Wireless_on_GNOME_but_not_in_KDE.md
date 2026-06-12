---
title: "Wireless on GNOME but not in KDE"
date: 2009-05-07
forum: Desktop Environments
---

### Post by tridgell on 2009-05-07
Hi I am using ubuntu(linux for that matter) for the first time in my life. I installed KDE but my wireless is not working in KDE.

Any help regarding this will be highly appreciated.

If you need more information to solve this, please ask me what is the additional information you need, also tell me how can i get that information.

Thanks

---

### Post by amingv on 2009-05-07
Did you remember setting your SSID/Passphrase in both KDE and GNOME?
Please take into account that they each use a different network manager, and may not share this data.

---

### Post by tridgell on 2009-05-07
> **amingv said:**
> Did you remember setting your SSID/Passphrase in both KDE and GNOME?
Please take into account that they each use a different network manager, and may not share this data.

Can you tell me how do I set passphrase in KDE.  I remember doing something similar in GNOMe

---

### Post by Muskegman on 2009-05-07
hello guys, I am having the same problem, i am using jaunty and have no problems with it so far. Connecting to the net in gnome works great using mobile broadband but i downloaded KDE today and tried connecting to the net using my 3G connection and it will not connect at all. The KDE desktop really looks and feels great but not being able to connect to the internet is a real bummer.

If anyone has any ideas how to proceed it would really be appreciated.:)

---

### Post by tridgell on 2009-05-08
I made some progress............Using network manager i was able to see the available wireless networks from KDE. It even allows me to enter the Passphrase. However, it takes long time but it never connects to the network............

---

### Post by earthtoclinton on 2009-05-08
> hello guys, I am having the same problem, i am using jaunty and have no problems with it so far. Connecting to the net in gnome works great using mobile broadband but i downloaded KDE today and tried connecting to the net using my 3G connection and it will not connect at all. The KDE desktop really looks and feels great but not being able to connect to the internet is a real bummer.

If anyone has any ideas how to proceed it would really be appreciated.

I got Xubuntu 9.04 Jaunty when it came out, and have been trying out KDE on it too - mobile broadband just DOES NOT WORK in KDE with the network manager plasma widget. It connects fine in both Gnome and XFCE, but KDE just won't connect it...very very frustrating. Maybe KDE 4.2.3 thats just been released will fix it? Gonna download it now and try. I have been searching all over and tring everything the last couple of weeks and have not found a work around for it.

---

### Post by Muskegman on 2009-05-12
I finally got my mobile broadband up and running and was able to connect to the internet in KDE. What i did was i opened up terminal in KDE and typed "nm-applet" and the connection icon appeared and i was able to connect, the only problem is when i exit and close terminal the icon dissapears and so does my connection. So now I am looking for a way to keep the applet added somehow to the panel so it will always be there when i switch from the gnome desktop to the KDE desktop. There must be some easy way i imagine to get it all working so i will keep on reading. Im just happy i could finally get internet in KDE.:)

---

### Post by earthtoclinton on 2009-05-13
Sounds great - I'll give it a try when I get home..I haven't had any luck connecting any other way yet myself. You could add the nm-applet to your autostart programs in kde? Don't see why that wouldn't work - will try it tonight. This aside though, they really need to fix the plasma widget so mobile broadband works. I can't really use KDE until they do.

---

### Post by ClyN3il on 2010-05-11
I'm having the exact opposite problem... Installed Kubuntu, then installed the Gnome desktop components. Wireless works fine on KDE (and in Vista) but when I switch to the Gnome desktop, it will detect the wireless networks, but never successfully connect. Is there some kind of conflict between software they use to manage wireless connections? I've tried installing the Gnome network manager and removing the KDE network manager, but that didn't seem to help.

Kubuntu Lucid dual-booted with Vista on an HP Pavilion laptop

---

### Post by jimbo99 on 2010-05-11
I can't offer much help on solving your problem, but I do know that kde's network manager, where you enter the passcode is a different mechanism than gnome. 

In my experience the problem is more with KDE than gnome.  What I mean is that generally I can get gnome to work with wireless where KDE almost always gives me a hassle (if I can get it to work at all).  Most of the time the KDE networking component sees the wireless and sees the WiFi access point but fails on the pass phrase.

I almost never have an issue with gnome, no matter what.  But I have had some difficulty with the latest gnome accepting the pass phrase.  I have not tried KDE on that comp.  Maybe I'll take another look.

---

### Post by vaiocomputer on 2010-05-12
If you have a problem with 'network-manager' and its applets for kde and gnome, you could use instead a different network manager.  I've heard some recommendations before about people that prefer using other network managers than the default ones in (k)ubuntu.  From the screenshots I've seen of it, it looks decent, but I can't remember what its called.

I'm not sure this is it, but here is one:  [http://en.wikipedia.org/wiki/Wicd_(Linux_Network_Manager](http://en.wikipedia.org/wiki/Wicd_(Linux_Network_Manager))

---

### Post by ErhanBey on 2010-05-25
I installed Wicd, it works in kde. But in gnome connection drops frequently. Then I removed Wicd. 
This is an important problem to not connect internet with using KDE. How can we solve this?

---

