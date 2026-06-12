---
title: "HELP with a sony Vaio"
date: 2009-04-21
forum: General Help
---

### Post by Murflaw on 2009-04-21
Okay, so I have this Sony Vaio VGN-FZ140E sitting in front of me, the web cam won't work and microphone won't pick up sound.

I have had this problem before with my laptop, but was able to fix these problems with the help of this thread:
[http://ubuntuforums.org/showthread.php?t=524907&page=4](http://ubuntuforums.org/showthread.php?t=524907&page=4)

Unfortunately, I had someone else handle this problem initially, and now there is a little green light that constantly blinks; even though I have removed all r5u870 drivers.

I then attempted a reinstall of these drivers, which I found here:
[http://cranked.me/2008/05/how-to-install-sony-vaio-vgn-fz21m.html](http://cranked.me/2008/05/how-to-install-sony-vaio-vgn-fz21m.html)


I have followed all terminal steps accordingly, and according to skype it is now recognized as:
SONY VGP-VCC4 #1 (/dev/video0)

but still shows now picture.  As for the microphone, no sound is being recorded.  

I am trying to avoid a full system reinstall, but if necessary I will do so and attempt to fix this problem.

If anyone has any insight into this problem, please help me! ](*,)

---

### Post by hifimusic on 2010-02-03
have ubuntu 9.10 installed on a Vaio FZ140E and everything works beautifully.

For microphone: you just need to fiddle with the audio settings a bit. the default audio device selected is wrong. change that to the other available option.

For webcam: go to 

[http://linux.softpedia.com/progDownl...oad-30296.html](http://linux.softpedia.com/progDownl...oad-30296.html)

and download 

Ubuntu DEB i386 (firmware)
[ubuntu_deb] [97.50 KB]

or 

Ubuntu DEB amd64 (firmware)
[ubuntu_deb] [97.50 KB]

and install the package

and it should start working.

---

