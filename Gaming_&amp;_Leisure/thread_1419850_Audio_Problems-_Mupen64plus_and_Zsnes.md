---
title: "Audio Problems- Mupen64plus and Zsnes"
date: 2010-03-02
forum: Gaming &amp; Leisure
---

### Post by rflores2323 on 2010-03-02
I installed mupen64plus and Zsnes from the ubuntu software center (ubuntu 9.10) and the playback is very smooth on both emulators however the sound is not working properly.

I am using alsamixer. 

Zsnes sound starts to play and then cuts off for awhile and then starts again. It very sporadic. I did the command 
```
zsnes -ad sdl
``` 
however it still is happening but it did take alittle longer for the sound to go away.  

Also I am not getting any sound from mupen64plus 1.5 that is installed.  How do I get this to work on ubuntu 9.10???

any help please.

---

### Post by k@e on 2010-03-02
Try to install the package libsdl1.2debian-pulseaudio, proceed if asked to uninstall a similar package.

```
sudo apt-get install libsdl1.2debian-pulseaudio
```

If that does not help, remove pulseaudio altogether. In most cases that will fix all audio troubles with SDL apps.

```
sudo apt-get remove pulseaudio
```

---

### Post by rflores2323 on 2010-03-02
Will this interfere with my alsamixer?  This box is for htpc and I currently have my surround sound working perfectly with alsamixer and dont want to break that.

Should I try to remove pulseaudio first and see if that helps incase it is installed.  Will both zsnes and mupen use alsamixer ??

---

### Post by rflores2323 on 2010-03-03
i tried the below and still no sound in mupen

```
sudo apt-get remove pulseaudio
```

---

### Post by k@e on 2010-03-03
Have you restarted after removing? Pulseaudio will still be running until the next restart or manual terminating.

---

### Post by rflores2323 on 2010-03-03
yes I have rebooted and still no audio. :(

---

