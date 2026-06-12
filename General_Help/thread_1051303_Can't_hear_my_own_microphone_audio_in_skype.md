---
title: "Can't hear my own microphone audio in skype:"
date: 2009-01-26
forum: General Help
---

### Post by klepto on 2009-01-26
I'm using Ubuntu 8.10 and using PulseAudio. I use Skype to do a radio show with a Plantronics Audio 650. In windows I could hear my own voice coming from the microphone aka full duplex. I can't seem to do this in skype. Here's the deal, i am not using usb but a dual line in to headphones jack and microphone jack. 

Thanks,  gotta do a show tonight ;)

---

### Post by Jose Catre-Vandis on 2009-01-26
Need more info about your sound settings to really help, am assuming you are not getting any sound from the mic?

Go into the volume control preferences and try out a few settings, particularly "MIC2" and "MIC Boost". I always need these two. You may need to add some switches and options.

Also try moving down to alsa only from pulse audio (there is a thread here somewhere on that)

---

### Post by klepto on 2009-01-26
I"m using ATI IPX, yes I have mic boost and mic on. That is what normally does it on Windows. 
The microphone works fine but it doesn't send the mic audio out for some reason.

Edit: After testing out PulseAudio/Alsa/OSS Still no go..

---

### Post by Jose Catre-Vandis on 2009-01-26
Try running alsamixer from within a terminal, sometimes you need to open up something there to get things working, even though the GUI says it is ??

Also assuming you have tried all available settings in Skype > Sound Devices

---

