---
title: "Mic problem - DELL XPS 210, Ubuntu 9.04"
date: 2009-05-28
forum: Dell Ubuntu Support (CLOSED)
---

### Post by vizualbod on 2009-05-28
Hi all,
since I installed Jaunty the microphone is not working. Speakers and headphones work great. Mic does not work on Gnome Sound recorder nor Skype.

Machine is 32 bit Dell XPS 210 with Ubuntu 9.04 installed from standard ISO image (not the Dell image).

Could you point me to the right direction?

---

### Post by boogerama on 2009-05-28
Hello Frank

I had the same problem.  After having little success modifying settings via alsamixer and volume control I eventualy reloaded with Dell's image.  Eventually I changed from Alsa Mixer to OSS mixer and that resolved my problems.  Now for the caveat.  This is on a Dell Mini 9 so your milage may vary.

Although it didn't completely clear up my issues, installing the Dell image did resolve a host of problems.  As of one week I have a clear running, issue free linux build (knock on wood:) )


Hope this helps.

---

