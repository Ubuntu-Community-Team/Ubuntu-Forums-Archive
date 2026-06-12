---
title: "Xserver hangs after boot"
date: 2006-07-10
forum: Desktop Environments
---

### Post by KoRnholio on 2006-07-10
I posted this in the Beginner's forum, but it went down to the second page in about twenty minutes.  I think its been lost there.  I figure it might be more apt here, since I'm not using the latest release.

----------------------------

I installed Breezy fine, on a dual-boot with XP, and it was working fine. I even installed the Easy Ubuntu packages without a problem.

Then I logged into Windows, essentially did nothing, and restarted again, to log into Ubuntu.

At Grub, I select the latest Ubuntu version, and it successfully reaches and passes the loading screen (the ugly black and brown one, which lists all the things its doing as its starting up). However, after then, nothing loads. The blank screen (with the blinking cursor) comes up, the blinking cursor goes away, and nothing happens.

It appears that the system is loading fine but the X server is hanging for some reason. Doesn't give me any error messages.

It passed installation fine and I was in the X server then for a while, without any problems. It was only on this reboot.

Would i have to reconfigure the X server? Or does this problem sound like something else?

---

### Post by raldz on 2006-07-11
it looks like EasyUbuntu installed the wrong graphics driver.. try to login in Recovery Mode and execute this in the terminal:

```
sudo dpkg-reconfigure xserver-xorg
```

just choose the default settings so that X Server could load..

---

### Post by KoRnholio on 2006-07-11
Thanks.  That seemed to be the problem.

It brings up another problem (not sure if there's a working driver for my Nvidia GeForce 6600), so I have to use the standard one for now.  But I only play 3d games on the Windows partition, so it doesn't matter too much :)

---

### Post by raldz on 2006-07-12
You may try to install the nVidia Legacy drivers which works well.. I've done it on my FX5200 and works well, here is the howto:

[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)

If anything goes wrong, just reconfigure it again to default settings..

---

