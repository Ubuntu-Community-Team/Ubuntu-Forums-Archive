---
title: "KDE 4.8.4 optimizations"
date: 2012-07-30
forum: Desktop Environments
---

### Post by Jakin on 2012-07-30
I'd like to know of some kubuntu 12.04 amd64 (though it probably makes little difference whether x86 or x86_64) tweaks or trick to improve the KDE plasma desktop load times.

From the moment i press the power button on my laptop- through grub- through plymouth, it takes 5 seconds to present the KDM login screen. 
Once giving the password though, the splash takes like 30 seconds before it goes away, and i have desktop ready. Why is that?  
My cpu is 2.3ghz and i have 6gb ram with no swap. 
I disabled akonadi server, and turned off nepomuk services. didn't help.
Could it be because i have all the bells and whistles of kwin openGL effects? I dont have any plasmoids really, a panel to view the desktop folder, and i run cairo dock open GL. 
Only thing that is autostarting with the session is f.lux and the dock.

Its not so bad to wait, but hey, if it can be optimized, of course we'd all want it.

---

### Post by carl4926 on 2012-07-30
> Could it be because i have all the bells and whistles of kwin openGL effects? Well it should be easy to test if it is...
Just turn off effects and try booting.

---

### Post by Jakin on 2012-07-30
Right, and quite. lol

It isn't the culprit it seems, wish it was.

[https://dl.dropbox.com/u/58975533/xsessions.txt](https://dl.dropbox.com/u/58975533/xsessions.txt)


[https://dl.dropbox.com/u/58975533/bootlog.txt](https://dl.dropbox.com/u/58975533/bootlog.txt) i think wont heip though.

---

### Post by carl4926 on 2012-07-31
Create a new user login, with no modifications and effects off.
Test it's behaviour.

---

### Post by Jakin on 2012-07-31
Its the strangest thing, I tried it, 10second splash; Went back to my previous user session with no configuration change, 10second splash. I don't get it but... THAT is more like it.

Thanks carl4926 :D

---

