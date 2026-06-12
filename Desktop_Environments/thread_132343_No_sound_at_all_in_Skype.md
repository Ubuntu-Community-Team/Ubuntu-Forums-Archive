---
title: "No sound at all in Skype"
date: 2006-02-18
forum: Desktop Environments
---

### Post by arrizaba on 2006-02-18
Hi,

I installed Skype using the wiki at:

[https://wiki.ubuntu.com/SkypeHowto](https://wiki.ubuntu.com/SkypeHowto)

I use polypaudio for the sound. 

I start Skype and it works. However, I cannot hear a thing, not even by calling the Test Echo buddy.

Has anybody had the same problem? Any help would be appreciated...

---

### Post by chris_andrew on 2006-02-18
Can you hear sound in any other apps?  Have you checked the volume controls?  Can you try ALSA?

Cheers,

Chris.

---

### Post by arrizaba on 2006-02-18
Hi, I fixed the problem by installing the skype_hijack_dsp script.

More info on:

[http://www.mozmarks.com/james/node/5?PHPSESSID=81dfb4778bcf493247de120cf9b0e725](http://www.mozmarks.com/james/node/5?PHPSESSID=81dfb4778bcf493247de120cf9b0e725)

the problem was that skype could not see my mic in /dev/dsp1, and this script makes it availables for skype.

---

