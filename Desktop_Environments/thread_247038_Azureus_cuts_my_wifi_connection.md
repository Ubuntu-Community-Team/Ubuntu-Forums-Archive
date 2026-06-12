---
title: "Azureus cuts my wifi connection"
date: 2006-08-30
forum: Desktop Environments
---

### Post by Sokar on 2006-08-30
Hi, i 've an Asus Z96 Laptop, with an intel 3945abg wifi card. All works perfectly with the nm-applet... connects to my WPA net, see all other nets...

The problem is when i start a p2p, like azureus... it works for 3-4 minutes, and then the wifi disconnects, and after several retryes, reconnects again...

I've probed and downloaded many things with the same computer, same wifi router, even same azureus version, in winxp and no problems... so i only can figure that is a problem of the driver for ubuntu or something like that...

If someone could give me a solution... it would be one more reason not to use windows ;)

Bye!

---

### Post by ciscosurfer on 2006-08-30
Do you have port-forwarding or port-triggering enabled on your router...you should have it enabled.  Then you won't have issues.

---

### Post by Sokar on 2006-08-30
No, i've opened the ports for my lan ip, and the router has upnp enabled, so it has azureus....

If with that config works in windows, why not in linux?

---

### Post by brundles on 2006-08-30
Have you compared the Azureus connection settings between Ubuntu and XP? It's possible that Ubuntu is opening more connections than XP or at a faster rate causing the router to throw a tantrum.

Try lowering the maximum number of connections that Azureus will allow and see if it makes a differences. There is (or was, my version of Azureus is several releases behind the power curve) also an option to make it only open new connections slowly rather than hammering the PC/router with 100 new connections all at once. Make sure that's enabled too.

---

### Post by Sokar on 2006-08-30
Oks, i`ll take a look to the azureus default settings in ubuntu, it could differe from the settings in windows...

Thnks!

---

### Post by Sokar on 2006-09-14
Hi, 've checked the configuration of the azureus in linux and the same azureus in windows xp, and both are indentical... if this wasnt enough, the wifi also gets down if i put amule (with the same config of emule in win)... so i dont know to think now...

I've executed the command dmesg y/o after some disconnections and reconnections... i dont understand pretty much of what it says, but some of you may understand it and give me any ideas...

[http://www.megaupload.com/es/?d=X2I1LKF9](http://www.megaupload.com/es/?d=X2I1LKF9)

Bye and thanks..

---

### Post by Sokar on 2006-09-19
Hi,

I solved it by installing an updated ieee80211 stack and the intel drivers...

If you know spanish (if not you only have to follow the bash commands), i've explained how did it work here: [http://www.bandaancha.st/foros.php?temid=1051457](http://www.bandaancha.st/foros.php?temid=1051457)

Bye!

---

