---
title: "Howto burn audio (mp3) in k3b?"
date: 2006-08-11
forum: Desktop Environments
---

### Post by unold on 2006-08-11
I just installed k3b, to burn some music in mp3-format. But the format is unsupported! How can i make k3b support it? If you have other apps to recommand, please do so. Im open to suggestions, i just want to be able to burn my mp3's at audio cd's. :confused: 
And serpentine does'nt seem to work either.:roll: 

- thanks for your time!

---

### Post by Fass on 2006-08-11
[https://help.ubuntu.com/community/RestrictedFormats#head-1340337f2ca1d0c54900935468515ba7630fcc59](https://help.ubuntu.com/community/RestrictedFormats#head-1340337f2ca1d0c54900935468515ba7630fcc59)

"To add mp3 support to K3b, install libk3b2-mp3."

---

### Post by orasis on 2006-08-11
> **unold said:**
> I just installed k3b, to burn some music in mp3-format. But the format is unsupported! How can i make k3b support it? If you have other apps to recommand, please do so. Im open to suggestions, i just want to be able to burn my mp3's at audio cd's. :confused: 
And serpentine does'nt seem to work either.:roll: 

- thanks for your time!

If you wish to convert your MP3's into audio cd format, I believe you will need to install an encoder/decoder - such as LAME. - then re-start your burning program. 

If you simply wish to burn MP3's to your CD's as data it would seem strange to recieve such an error, try using XFBURN if you have that availible in your set up. 

Or X-CD-ROAST. - Seems to be a pretty nice cd burning app, even though sometimes it takes setup to get it to identify your burners. 

But again if you are trying to burn MP3's as audio cd's - it is most likely not working because you do not have any encoding codecs installed. (And I believe for copyright reasons, Ubuntu does not install anything but free codecs by default - and mp3, is not an "open source" format.)

---

### Post by snooze on 2006-08-24
Thanks Fass.
Worked great.
sudo apt-get install libk3b2-mp3
Cheers.

---

### Post by andlinux21 on 2006-09-02
Snooze thanks for posting that command I was having the same problem but now everything is A-OK!! :)

---

### Post by floyd27 on 2006-09-04
Worked great...:)

---

### Post by Mithrilhall on 2006-09-16
Thanks...that worked perfectly.

---

### Post by endorfin on 2006-10-10
Thanks! It just works!

---

### Post by MarkoSK on 2006-10-25
great...worked...tnx a lot...i love when the things are that simple ;)

---

### Post by Huss on 2008-04-20
Worked for me!

You may have to reboot though.

---

