---
title: "Hey... I Thought Rhythmbox Could Play AAC Streams"
date: 2006-10-07
forum: Desktop Environments
---

### Post by Mark76 on 2006-10-07
I installed the gstreamer and the appropriate plugins and I still can't listen to my favourite radio station on rb ](*,) 

Is aacplus incompatible with rb?

---

### Post by epennings on 2006-10-07
Have you tried installing gstreamer0.8-faad?

```
sudo apt-get install gstreamer0.8-faad
```

---

### Post by Mark76 on 2006-10-07
Yep

---

### Post by lemonsCC on 2006-10-07
From the wiki on restrictedformats
> Install the gstreamer0.10-plugins-bad-multiverse package. (Note: some people may need to also install gstreamer0.10-plugins-bad to make it work.)


[Source]("https://help.ubuntu.com/community/RestrictedFormats#head-3b21b161513c49f26dac2aaca9afd8f64e21aaaa")

---

### Post by epennings on 2006-10-07
AAC Plus streams work for me in RythmBox. You could try installing faad and libfaad2-0 and see if that works.

---

### Post by Mark76 on 2006-10-07
Already got them.

Could you check out Indie Pop Rocks at SomaFm ([www.somafm.com)](www.somafm.com)).   I'm beginning to think their streaming is shagged.

---

### Post by pgatrick on 2006-10-07
Needs gstreamer-0.10 :p

---

### Post by epennings on 2006-10-07
I tried [http://somafm.com/groovesalad48.pls]("http://somafm.com/groovesalad48.pls") and it plays fine. 

edit : Indie Pop Rocks works too :
[http://somafm.com/indiepop48.pls]("http://somafm.com/indiepop48.pls")

sorry, I'm out of ideas :(

---

### Post by Mark76 on 2006-10-07
I downloaded the ugly plugins for gstreamer and it's working fine now.

Thanks for the help guys :)

---

