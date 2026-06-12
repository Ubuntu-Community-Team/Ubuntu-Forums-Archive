---
title: "Help! Beryl first time user"
date: 2007-07-07
forum: Desktop Effects &amp; Customization
---

### Post by frostbytejam on 2007-07-07
Hi!
I'm a first time user of Beryl and Ubuntu. I have been doing a self study on how to use Unix and Linux. I have been experimenting and now I came across with Beryl. It's really not user friendly.
I have installed Beryl and I'm having a hard time setting it up. Some of the actions I have taken, I have installed it and run" glxinfo | grep direct" in which direct rendering is YES. I also downloaded the emerald themes and added (BERLY-manager)to startup. I checked on the Beryl settings manager but still nothing happens. I tried to look for help using google but i found nothing to help me. I am trying to stay away from windows as much as I can. If you can help it would really mean a lot to me.Pls reply ASAP. Thank you.

---

### Post by frostbytejam on 2007-07-07
I also would like to add that my beryl is already up and running and nothing is happening on my desktop

---

### Post by dwebb86 on 2007-07-07
anyone know about this problem? I have beryl-manager up and running on my desktop too, though nothing happens. during installation it worked for about 10 minutes for some reason, then something happened and now it doesn't do anything after it starts up. I see the mini red diamond, it's there and running, but none of the effects do are working.

---

### Post by ASPCartman on 2007-07-07
Beryl i nour repo is broken how i know). it 2.1..0 but feisty need 2.0 . Officical beryl repo hacked down.
I cant run it ether

PS
If u got ATI and bery 2.0 - than u need to be in XGL session (how-to : beryl-project.com than wiki and then... u got it. But ignore install (packeges etc) section - it out of date and, cos of broken repo )

HOW I KNOW - IF U HAVE FEISTY AND V >2.1.0 U CANT RUN IT! 

PSS
I WAAANT MY BERYLLL!!! :(:(:(:(:(

---

### Post by FNDII on 2007-07-13
SO fiesty 7.04 and berly Version: 0.2.1 = no vcube?

---

### Post by Supremacy on 2007-07-13
Do you have composite extensions enabled?? if not enter the following command in a terminal window and restart xserver:

```
sudo nvidia-glx --composite
```

I believe its that command with nvidia-glx. If not please correct me.

Regards,
Supremacy

---

### Post by nelamvr6 on 2007-07-13
Hmmm....

That's weird...  it works fine in Mint.

[img]http://homepage.ct.metrocast.net/~nelamvr6/Screenshot.jpg[/img]

---

### Post by FNDII on 2007-07-13
I had the same problem, I found a fix that worked for me.

[http://ubuntuforums.org/showthread.php?t=5004Post](http://ubuntuforums.org/showthread.php?t=5004Post) back and let me know if that worked for you

---

