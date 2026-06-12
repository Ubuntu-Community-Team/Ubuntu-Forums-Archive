---
title: "Samson C03U USB Microphone Setup Config Ubuntu Linux"
date: 2008-12-15
forum: General Help
---

### Post by parablood on 2008-12-15
I am in need of some help configuring my USB Mic (Samson C03U USB Microphone) on Ubuntu 8.10. I have included some details below and while you can see my XFI hardware card is installed I do not use my XFI card for Ubuntu at this time. I use my on-board sound card for sound to play movies music etc and it works great. However, I can't at this time hear what I record with my USB Mic on Audacity etc. (It seems to really be recording in Audacity. I can see the lines when I speak.) However, I can't play the sound back because Audacity can't see my on-board sound card. When I run a Sound capture test from System > Preferences > Sound - I can speak 1 word and hear 1 word before sound cuts off from my Samson C03U USB Microphone. Ideally I would like to get this microphone setup so I can not only use it for this system but so I can use it on my VM's with Virtual Box. If anyone has any ideas either complex or simple I am all ears.

```

:~$ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf7000000 irq 22
 1 [default        ]: USB-Audio - Samson C03U              
                      Samson Technologies       Samson C03U               at usb-0000:00:1a.0-2, full
```


ALSA Information Script v 0.4.52
[http://pastebin.ca/1285595](http://pastebin.ca/1285595)

Thanks ahead of time,

Parablood

---

