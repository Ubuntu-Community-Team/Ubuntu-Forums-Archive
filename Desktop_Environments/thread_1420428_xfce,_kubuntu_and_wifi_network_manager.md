---
title: "xfce, kubuntu and wifi network manager"
date: 2010-03-03
forum: Desktop Environments
---

### Post by fahd on 2010-03-03
Hi folks …

There is a weird network manager related issue in ubuntu. XFCE (daily build) would recognise the wifi-network as soon as you login,  the only thing to be done, is to type in the password for wifi connection (praise to gnome network manager ). Whereas kubuntu always fails to recognise the wifi-network (knetwork manager, kwallet). It seems that gnome has done a good job than ubuntu. I propose for kubuntu development team to adopt gnome network manager or alike to apply it in kubuntu. No doubt that Kubuntu is a cool stuff, but we should learn more from others ( it is not shame). Thanks.


Fahd
100303

---

### Post by inobe on 2010-03-03
network manager has a bit more configuration involved but it works if you know your router settings.

---

### Post by fahd on 2010-03-03
As I have already mentioned. Xfce automatically recognises the se. protocol my wifi router using (wpa/wpa2 with psk). All these things are prerequisites for setting and configing the wifi routers. All what you are asked to do is to type in your password configured in the router. Again the difference lies in the two counterpart apps, kde and gnome nwtwork managers. Thanks again.

Fahd
100303

---

### Post by Thomas Garman on 2010-03-04
Reading through various threads inspired me to give Kubunutu a try to see what KDE was like compared to GNOME, which I have been using since I started using Ubuntu.
 
I tried installing the kde-desktop through apt-get and as it turns out it made my wifi undetectable in both kde and gnome, so I uninstalled it and tried a clean install of kubuntu from the liveCD on its own partition... 
 
KDE cannot detect or connect to wifi without messing around with its network manager in some way that utterly mystifies me whereas GNOME's network manager detects and connects to wifi with absolutely no user input required other than the wep/wpa password.
 
On top of that, under Kubuntu neither my keyboard nor my mouse were recognized, so I had to use a usb mous/keyboard that I had laying around...  so anyway...  
 
I deleted the partition and just went back to gnome.  Life is too short to get jerked around by a network manager.
 
Thanks for nothing KDE.

---

### Post by fahd on 2010-03-07
You are completely right. KDE dev. team should take into consideration that the life is too short (as you have mentioned), and think of that how to allure folks from windows world to love and use kde. Have they ever asked themselves (KDE development team) why people all over the world (the majority) use microsoft windows products. Simply because they are not forced to config every thing to get the product useful. We are all here in this forum and other linux forums to support and advocate linux and make it the best free stuff, not to give the everlasting ideas and proposals. Is KDE the best solution (projekt) for all of us (linux fans and users) ? No doubt GNOME has not made the good job (unfortunately). I feel that neighter KDE is the perfect projekt. Anyway, may be after years somebody would recognise that, the time has arrived to conceive new breed of DEKTOP which is bug-free and fast enough to harness the your computer hardware. Really there is big gap between the hardware and software developments. The software development is sluggish comparing to its counterpart (hardware). It is easy to dream any thing, but it is difficult to realise it. Thanks a lot.

Fahd
100307

---

### Post by aarons6 on 2010-03-07
works for me, right click it, select enable wireless and away you go?

sometimes i do have to put the password in twice.. but it works every time.

---

### Post by inobe on 2010-03-07
> **fahd said:**
> As I have already mentioned. Xfce automatically recognises the se. protocol my wifi router using (wpa/wpa2 with psk). All these things are prerequisites for setting and configing the wifi routers. All what you are asked to do is to type in your password configured in the router. Again the difference lies in the two counterpart apps, kde and gnome nwtwork managers. Thanks again.

Fahd
100303

so what's the big deal ?

use what works for you ;)

---

### Post by bunty on 2010-03-07
I'm mystified as to what I have to do to get a wifi connection on kubuntu.

The network manager hemorrhoid shows the local network fine and I can see the router wifi as unconnected. I click, it opens a dlg to enter the password , which I copy/paste from the routers web interface. 

It then shows that it failed to connect. No explanation. Nothing in /var/log/messages

I seem to recall kwallet bugging me last time I looked at this and I gave it a password , don't know if that's related. Since I get asked for a password I guess not , but I know kwallet can be a PITA as well.

Is there a way to set this manually? I hate "just works" gui tools , especially ones that don't.

:o

---

### Post by bunty on 2010-03-07
ARgh, this is turning into a cluster-fcuk.

Having followed the great advice of installing wicd it has ripped the guts out of the networkmanager hemorrhoid which is now just a black spot on the screen. It has not set up the wifi and eth0 is now gone. 

I now have no networking at all , I cannot even reach the router.  

Is there any way out of this mess with out doing a windows-lame reinstall ?

---

### Post by Thomas Garman on 2010-03-07
Absolutely mysterious, really.  I decided to give KDE another try... and once again after reading various threads for two hours I have yet to see any way that you would be able to get the KNetwork Manager to actually connect to wifi.

So, that's the end of that...  I don't know what else to say other than:  KDE's network manager cannot connect to wifi.

And that is a total deal breaker.  If you are saying you just turned on your computer and got wifi to work through KDE somehow then I say lucky for you because it definitely will not connect on my computer and using the gnome network manager under KDE... well why bother with KDE at all.

very frustrating.

---

### Post by krazyd on 2010-03-08
The KDE team is well aware of the limitations of the current knetworkmanager, and are writing a new plasma-applet to manage network connections - but it's not ready yet. 

Personally, I'm using knetworkmanager and admit its a little buggy, but works well enough for me.

If you want, you can uninstall 'plasma-widget-networkmanagement' and install 'network-manager-gnome'. It's perfectly usable in KDE.

---

### Post by fahd on 2010-03-08
Hi guys ...

Try wicd application. It is very cool stuff for network management. I did it. Have a good luck.

Fahd
100308

---

### Post by fahd on 2010-03-08
Hi guys ...

Try wicd application. It is very cool stuff for network management. I gave it a try. It functions very well. Have a good luck.

Fahd
100308

---

### Post by JakeOfOz on 2010-03-31
yea, wicd works for me too. I had the same problems. Btw, knetwork is very firm on not recognizing hidden networks (once tried to connect to a hidden apple network... it was hell)
and besides, wicd has a better interface too

---

