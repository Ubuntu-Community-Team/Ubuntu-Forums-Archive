---
title: "How do I connect my Creative Zen X-Fi to Ubuntu Intrepid?"
date: 2009-02-19
forum: General Help
---

### Post by Lingonet on 2009-02-19
Hi, hi.

I have a Creative Zen X-Fi I was going to connect to my computer in Ubuntu 8.10. The thing is that absolutely nothing happened. I have tried to install Gnomad2 but then it says says: "No jukebox found on USB bus". To sum it up: When I plug my MP3 in nothing happens. No external device pops up. Nothing.

How can I make Ubuntu connect my MP3 player??

Thank you!

---

### Post by mttman on 2009-02-19
I had a similar problem with my mp3 (from Phillips) it turned out that i had to use the specific cord it came with the get it to connect on any OS (even though it was the mini usb connector). apart from that try to use 
```

sudo mkdir /mnt/mp3 
sudo mount /dev/usb# /mnt/mp3
``` with # being some number starting with 0.

Post any results you get from this, also usb# might not be the right device to use, have to do some checking.

Mttman

---

### Post by Lingonet on 2009-02-19
```
henrik@Femmansbuntu:~$ sudo mkdir /mnt/mp3
mkdir: kan inte skapa katalog "/mnt/mp3": Filen existerar
henrik@Femmansbuntu:~$ sudo mkdir /mnt/mp3 
mkdir: kan inte skapa katalog "/mnt/mp3": Filen existerar
henrik@Femmansbuntu:~$ sudo mount /dev/usb# /mnt/mp3
mount: specialenheten /dev/usb# finns inte
henrik@Femmansbuntu:~$ 
henrik@Femmansbuntu:~$ sudo mount /dev/usb1 /mnt/mp3
mount: specialenheten /dev/usb1 finns inte
henrik@Femmansbuntu:~$ sudo mount /dev/usb2 /mnt/mp3
mount: specialenheten /dev/usb2 finns inte
henrik@Femmansbuntu:~$ sudo mount /dev/usb3 /mnt/mp3
mount: specialenheten /dev/usb3 finns inte
henrik@Femmansbuntu:~$ sudo mount /dev/usb4 /mnt/mp3
mount: specialenheten /dev/usb4 finns inte
henrik@Femmansbuntu:~$ sudo mount /dev/usb5 /mnt/mp3
mount: specialenheten /dev/usb5 finns inte
henrik@Femmansbuntu:~$ sudo mount /dev/usb6 /mnt/mp3
mount: specialenheten /dev/usb6 finns inte
henrik@Femmansbuntu:~$ sudo mount /dev/usb7 /mnt/mp3
mount: specialenheten /dev/usb7 finns inte
henrik@Femmansbuntu:~$ sudo mount /dev/usb0 /mnt/mp3
mount: specialenheten /dev/usb0 finns inte
henrik@Femmansbuntu:~$
```

English translation:

"Kan inte skapa katalog" - Cannot create catalouge.

"Filen existerar" - File exist.

"Finns inte" - Doesn't exist.

---

### Post by mttman on 2009-02-19
in terminal 
```
cd /dev
ls|grep usbdev2
```
try all the results one at a time in 
```
sudo mount /dev/<result> /mnt/mp3
```
replace <result> with one of the lines displayed at a time

please post output

---

### Post by Lingonet on 2009-02-20
```
henrik@Femmansbuntu:~$ cd /dev
henrik@Femmansbuntu:/dev$ ls|grep usbdev2
usbdev2.1_ep00
usbdev2.1_ep81
usbdev2.3_ep00
usbdev2.3_ep81
henrik@Femmansbuntu:/dev$ 
```

---

### Post by Lingonet on 2009-02-20
I was going to try this today and it surprised me that the MP3 was... dead. I can't turn it on, I can't recharche it in the computer nor the wall contact.

What is wrong with it? It is dead!

Thank you!

---

### Post by mttman on 2009-02-20
with a problem like that you should contact the manufacturer

---

### Post by Vultoor on 2009-03-03
> **Lingonet said:**
> I was going to try this today and it surprised me that the MP3 was... dead. I can't turn it on, I can't recharche it in the computer nor the wall contact.

What is wrong with it? It is dead!

Thank you!

Just try to restart it... I had the same problem and it worked! It has to have a little button or something for restart! Hope it helps!

---

### Post by woodenbrick on 2009-03-03
mtp devices like the creative zen can be a bit fiddly trying to get to work with ubuntu.  I have a zen (not xfi) and I use Amarok for sending music and mtp-tools to send videos.

Amarok is the only player i found that sends along the artwork.
mtp-tools works most of the time, however seeking through a movie may be broken depending on he file encoding.

Also note, you wont see your creative zen on the desktop like you would a usb device, unless you use the mtpfs program to mount it.

---

