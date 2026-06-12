---
title: "Ubuntu Can't Boot into Gnome"
date: 2006-07-17
forum: Desktop Environments
---

### Post by walmartshopper67 on 2006-07-17
*I posted this in a different forum, and got no help at all, and only 50 people read it in the 3 or 4 weeks it was posted, so I'm posting it here. Please don't delete/mod it - i'm not doing it just to get a faster response - i'm doing it to GET a response. I'm trying to install Ubuntu dapper 6.06 on a Gateway 310 (link to specs and docs: [http://support.gateway.com/support/srt/docs.asp?sn=1098424970)](http://support.gateway.com/support/srt/docs.asp?sn=1098424970)). The computer has an onboard video card, and an NVidia GeForce FX 5200 (in a PCI slot). It has Windows XP and now Ubuntu dapper - but when Ubuntu starts up it comes up with a red and blue screen with a bunch of garbage and says that the X server could not start, that screens were found but none had usable configs. This happens when the Nvidia card is enabled in the bios and the monitor is plugged into the Nvidia card. When the on-board card is enabled and the monitor in that, it works fine. I need to get it to work with Nvidia card on start up (it's my girfriends computer - i'm on the verge of converting her to Ubuntu but this isn't helping). I've posted the error log and the xorg.conf here on my webserver: (error log: [http://ghettonet.no-ip.org:8080/~redneckpunk/Xorg.0.log](http://ghettonet.no-ip.org:8080/~redneckpunk/Xorg.0.log))

(xorg.conf: [http://ghettonet.no-ip.org:8080/~redneckpunk/xorg.conf](http://ghettonet.no-ip.org:8080/~redneckpunk/xorg.conf) )

Any help would be appreciated - i'm so close to getting her on Linux, and this is frustrating ](*,)

---

### Post by Paerez on 2006-07-17
hi sorry if this is a dumb suggestion, I have never used ubuntu on nvidia cards...

Is there anything you need to install to get nvidia drivers? It seems your comp is having trouble loading libGLCore, which I would guess means you have to install something from nvidia.

Search through the repositories (I suggest aptitude) for nvidia stuff.

---

### Post by reclusivemonkey on 2006-07-17
Firstly, I presume from looking at your xorg.conf you have a TFT/LCD Monitor? Have you checked the 

```

HorizSync	28-57
VertRefresh	43-60

```

are correct?

Secondly, your xorg.conf is set up for your onboard graphics card, so you will need to change this to get it working with your nvidia card. Have you looked at the various HOWTOs on getting NVIDIA cards working??? 

[http://easylinux.info/wiki/Ubuntu_dapper#How_to_install_Graphics_Driver_.28NVIDIA.29](http://easylinux.info/wiki/Ubuntu_dapper#How_to_install_Graphics_Driver_.28NVIDIA.29)

Try that and let us know how you get on.

---

### Post by walmartshopper67 on 2006-07-17
hm..it's a plain CRT monitor, so I will check that. I'll bet that the link you gave me is exactly what I'm looking for - I *think* i just need to configure xorg for the nvidia card by hand because I couldn't get it to do it auto-magically. Thank you for the suggestions, I'll let you know how it turns out!:-D

---

