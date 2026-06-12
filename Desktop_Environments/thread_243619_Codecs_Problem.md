---
title: "Codecs Problem"
date: 2006-08-25
forum: Desktop Environments
---

### Post by christxr on 2006-08-25
First of all I'm a noob...I thought I had recovered from the xserver crash the other day but now my DVD playback codecs are broken as well as video in Firefox (not sure what program this is). I'm also having trouble trying to burn to DVD. I tried reinstalling them the same way I installed them in the beginning but to no avail. I used this method:

[http://www.ehomeupgrade.com/entry/2663/how-to_get_full](http://www.ehomeupgrade.com/entry/2663/how-to_get_full)

This worked great the first time but not after the x-server crash. Any suggestions? Do I need to uninstall something else first?

The message I get in Totem is:

Totem could not play DVD
The source seems encrypted, and can't be read. Are you trying to play an encrypted DVD without libdvdcss?

In Firefox I go to play a video stream on foxnews.com and I just get a black box where the video should be.

Any help would be greatly appreciated.

Thanks,
christxr

---

### Post by neilp85 on 2006-08-25
I recommend using Automatix to install the codecs and dvd playback. It can also add the firefox extensions for playing videos. Just open up a terminal and paste the following
```
wget http://www.getautomatix.com/files/automatix-installer
chmod 755 ~/automatix-installer
./automatix-installer
```
That will install automatix, then you can run it from Applications->System Tools->Automatix. Click OK a couple times, enter in your password and then just check all the packages that you want to install. At the end it will ask if you want to restore your old sources.list and you can just say ok.

---

### Post by neilp85 on 2006-08-25
Also, you can find a lot more information about Automatix [here]("http://www.getautomatix.com/")

---

### Post by jimbob on 2006-08-25
Video playbacks from Foxnews.com are broken since they upgraded to Flashplayer 9.

See if you can play videos from Cnn.com which is still working (today anyway).
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by neilp85 on 2006-08-25
According to [this]("http://blogs.adobe.com/penguin.swf/2006/08/across_the_distros_1.html") post Flash 9 could be coming to Linux pretty soon.

---

### Post by christxr on 2006-08-26
Thanks. Automatix did the trick.

---

