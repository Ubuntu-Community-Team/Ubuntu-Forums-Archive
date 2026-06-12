---
title: "Real Player"
date: 2006-07-19
forum: Desktop Environments
---

### Post by seshomaru samma on 2006-07-19
Hi 
I installed Realplayer from the realplayer website but get this error when i run it :
```
GTK Accessibility Module initialized
/usr/bin/realplayer: line 75: 12526 Segmentation fault      $REALPLAYBIN "$@"
```

I tried to install from a deb file ,through a link that someone posted on this forum but got the same results.

The reason I want it in the first place is that my wife wants to be able to listen to Japanese radio  (like [THIS]("http://www.nhk.or.jp/rj/index_e.html")  or [THIS]("http://www.multilingualbooks.com/online-radio-japanese.html")) .
If someone can help me sort out the realplayer problem or offer an alternative way to listen to radio without realplayer , I (and my wife) would be very greatful.
Thanks...

---

### Post by Jagot on 2006-07-19
RealPlayer is now available in Canonical's Commercial Repo:

[http://ubuntu.wordpress.com/2006/07/08/introducing-the-dapper-commercial-repository/](http://ubuntu.wordpress.com/2006/07/08/introducing-the-dapper-commercial-repository/)

Follow the instructions to add the repo to your sources.list and install from there.

---

### Post by Delkster on 2006-07-19
You can just look up RealPlayer in Applications -> Add/Remove. Select the 'Show commercial applications' checkbox and search for realplayer. Be sure to install RealPlayer 10 instead of the older one that is worse supported.

However, you don't necessarily need RealPlayer to listen to some of those stations. At least behind the first link there's a Windows Media stream available that is playable on applications that use Xine or GStreamer as their player backend, such as Totem and Rhythmbox. That requires the ffmpeg plugin for the player, though. Open Add/Remove Applications, make sure you have "Show unsupported software" selected, search for "gstreamer extra plugins" and "xine extra plugins" and install those two packages.

---

### Post by seshomaru samma on 2006-07-19
I installed with add/remove (checked commercial software) and got this error while installing :
```
E: /var/cache/apt/archives/realplay_10.0.6.776-1plf1_i386.deb: trying to overwrite `/usr/lib/mozilla/plugins/nphelix.so', which is also in package realplayer
```

now when i run it i get :
```
GTK Accessibility Module initialized
/usr/bin/realplayer: line 75:  5222 Segmentation fault      $REALPLAYBIN "
```$@"

:confused: :confused: :confused:

---

### Post by Delkster on 2006-07-23
> **seshomaru samma said:**
> 
```
E: /var/cache/apt/archives/realplay_10.0.6.776-1plf1_i386.deb: trying to overwrite `/usr/lib/mozilla/plugins/nphelix.so', which is also in package realplayer
```


Did you remove the old realplayer package first? The new RealPlayer package from the Ubuntu Commercial repository is called realplay while the older version is realplayer. They probably conflict if you try to have both of them installed at the same time. (They should probably state that in their dependencies, though, and if they don't, that may be a bug.)

---

