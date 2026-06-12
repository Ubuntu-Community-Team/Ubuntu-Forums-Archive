---
title: "some bugs on dell mini 1012"
date: 2010-09-26
forum: Dell Ubuntu Support (CLOSED)
---

### Post by tikusjamban on 2010-09-26
hyee i hv installed ubuntu 10.04 LTS my 1012...i hv some minor bugs i think here...

1.my wc is not working..dont know why...pigget or even empthy did not support my wc..(wc=webcam)

2.my bluetooth is not really working..its only working when i plugin my usb thum bluetooth...

3.my microphone is not working either dint know why...

im a newbie in ubuntu..hoping that u all can help me in this...
long live ubuntu..

---

### Post by tikusjamban on 2010-09-30
hello is any one can help me here???

---

### Post by P4man on 2010-09-30
IS the webcam not working, or is video conferencing not working in those apps? To test your webcam support, try installing cheese or ekiga and see if you get a picture or not. More details on testing here:
[https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)

As for bluetooth; are you sure its actually turned ON (most laptops have a hardware switch or Fn+function key combo to turn it on). If thats not it, open a terminal and type in the following 2 commands:
```

lspci
lsusb
```

copy/paste the output here.

As for microphone, same question as 1. Is it the microphone or the audio chat? Check your settings in sound preferences and see if the input level actually works if you talk (or scream). Check the hardware tab for the correct device and profile.

---

### Post by btencd on 2010-11-12
[QUOTE=P4man;9907177]IS the webcam not working, or is video conferencing not working in those apps? To test your webcam support, try installing cheese or ekiga and see if you get a picture or not. More details on testing here:
[https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)

As for bluetooth; are you sure its actually turned ON (most laptops have a hardware switch or Fn+function key combo to turn it on). If thats not it, open a terminal and type in the following 2 commands:
```

lspci
lsusb
```

copy/paste the output here.

Hi could you suggest me then I have the same problem (i posted it in following link details):
[http://ubuntuforums.org/showthread.php?t=1619786](http://ubuntuforums.org/showthread.php?t=1619786)

thanks

---

