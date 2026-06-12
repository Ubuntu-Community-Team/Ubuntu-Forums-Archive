---
title: "kde4 seems to be taking up 50% of my CPU power after upgrade"
date: 2009-05-23
forum: General Help
---

### Post by philjwill on 2009-05-23
I upgraded to 9.04 last night, to hopefully get rid of some graphical issues I'd been having with KDE, this turned out to be the right thing to do, as it solved them all. However, since I've upgraded, kde4 has been using 50% of my CPU power and driving up the temps quite a bit, anyone have any insight into my situation?

---

### Post by applefox on 2009-05-23
Hello. Would you mind giving me the specs of your CPU and just overall computer. It may be that it is not high enough spec to run the new KDE. Thanks.

---

### Post by philjwill on 2009-05-23
AMD athlon 4200X2 @ 2.2GHz
2 gigs of corsair PC6400
250gig maxtor drive
XFX 7950GT

This box may be over 2 years old at this point, but I doubt there should be a problem, specs wise.

---

### Post by khelben1979 on 2009-05-23
> **philjwill said:**
> AMD athlon 4200X2 @ 2.2GHz
2 gigs of corsair PC6400
250gig maxtor drive
XFX 7950GT

This box may be over 2 years old at this point, but I doubt there should be a problem, specs wise.

I don't think so either. My guess is that your graphics drivers have been replaced to slow open source drivers by some update.

Another thing it could be is that you need to turn down the graphical effects in the new [KDE 4]("http://en.wikipedia.org/wiki/Kde_4") enviroment.

---

### Post by philjwill on 2009-05-23
This is the thing, I'm running the nvidia 180 drivers, that's why I thought it was so weird. as for desktop effects, even when I turn them off completely, the result is the same.
I've tried switching between opengl and xrender with no change too. It's quite bizarre.

---

### Post by khelben1979 on 2009-05-23
Downgrade? 

I'm using KDE 3.5.10 myself and it doesn't take very much cpu power over here. This old laptop (see my signature) can drive it without serious performance issues (at least in the sense how I'm using it).

---

### Post by philjwill on 2009-05-23
:(

I was hoping someone could come up with a reply like "This is a common bug, easily fixed by doing X"

I suppose it's time to check some other options out.

---

### Post by noelvh on 2009-05-23
I was a Kubuntu user for over 2 years, and with the new KDE4 I made the move to Ubuntu. Hell I love it but it takes up to much system for me to use it well. I am not going to get new hard ware for it. What I did in KDE I can do in Gnome. Hell I even have some qt apps installed and they run great with out the KDE4 over head.

Noel

---

### Post by Mirge on 2009-05-23
Which specific version of KDE are you using? Are you on Kubuntu? Or are you using Ubuntu with KDE installed on it? Etc..

---

### Post by philjwill on 2009-05-23
Apparently it's a known bug, I just killed kded4 and it no longer causes any problems.
kded is only used to check for updates and hostname changes anyway, or so I've read, so I doubt I'll miss it.

---

### Post by noelvh on 2009-05-23
I was looking for the same thing before I made the switch. I did find some good help, but I was spending more time fixing that computting. I felt as if I was using windows with out the viruses. I love KDE and did not want to make the switch, but I setled in very quickly under Gnome. I also loved dolphin and could not live with out it so I installed it under Ubuntu. I hope you find the answer:-)

Noel

---

### Post by txcrackers on 2009-05-23
I've had kded go nuts a couple of times. Either killed it or logged out and back in again. There never was an indication as to what exactly triggered it, but it hasn't acted up in a while.

---

