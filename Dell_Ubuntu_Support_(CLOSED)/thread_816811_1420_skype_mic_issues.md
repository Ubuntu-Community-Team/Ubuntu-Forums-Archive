---
title: "1420 skype mic issues"
date: 2008-06-03
forum: Dell Ubuntu Support (CLOSED)
---

### Post by sanjuuichisandoichi on 2008-06-03
Alright so here's the deal,

I'm on a 1420n running Gutsy, I have the Webcam working with skype just fine, and the mic works perfectly with the sound recorder and with the little test thing through system-preferences-sound.  However when trying to make an echo call in skype, I can't hear myself at all!

Under Skype's audio options the only choices for 'audio in' are

Default Device <-- i hear nothing
HDA Intel(hw;Intel,0)  <-- I also hear nothing  or
HDA Intel(plughw;Intel,0)  <--- gives me a "problem with audio capture" error while trying to connect the call

I'm not sure which device I should be trying to make work or which of these even is my microphone.  Anyone out there successfully using skype with their built in mic?

---

### Post by svega85 on 2008-06-06
i also have the same problem with the same laptop

---

### Post by cleons on 2009-03-28
I had the same problem and in google I found:

[http://davron.wordpress.com/2008/12/24/inspiron-142015201720-integrated-microphone-in-ubuntu/](http://davron.wordpress.com/2008/12/24/inspiron-142015201720-integrated-microphone-in-ubuntu/)

Open a terminal and:

**sudo alsamixer**

In the item "Digital Input Source" I put the value "Digital". Apparently the Default value is "Analog", so change it to "Digital".

Then I make the test call in skype and works.

Bye.

---

### Post by Denny Johnson on 2009-03-28
> **cleons said:**
> 

In the item "Digital Input Source" I put the value "Digital". Apparently the Default value is "Analog", so change it to "Digital".
.
That's been my experience [1420n, hardy] , and if I want to use a headset, I have to set it back to ANALOG

---

