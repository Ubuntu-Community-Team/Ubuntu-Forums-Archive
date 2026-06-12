---
title: "help mounting a usb drive"
date: 2006-01-13
forum: Desktop Environments
---

### Post by twitch101 on 2006-01-13
not a HD

i have a usb external cdrw burner and i need to mount it. it shows up when i use the lsusb command in terminal as being on bus 004 : xxxx    xxx:xxx cd burner name

but how do i get it to where i can mount it and burn cds with it it is an HP cd+writer 8200 series

---

### Post by djgenesis on 2006-01-14
have you tried creasting a folder in /media/cdrw:
```

mkdir /media/cdrw

```
and then
```

sudo mount /dev/sda1 /media/cdrw

```
Not suire if it works on a CD burner but this is how i am mounting my usb flash

genxx

---

