---
title: "Cannot format Sansa E-280R"
date: 2009-06-01
forum: General Help
---

### Post by InfectedWithDrew on 2009-06-01
I'm having trouble formatting my old mp3 player whose screen broke and I am trying to repurpose as a bootable USB drive.  I tried the IRC channel but was unsuccessful.

I have so far successfully formatted it in Windows but this doesn't help me since I need it to format in usb-creator on Ubuntu.

I tried using Gparted and got this error:
```
   1.
      GParted 0.4.3
   2.
       
   3.
      Libparted 1.8.8
   4.
      Delete /dev/sdc1 (fat32, 7.47 GiB) from /dev/sdc  00:00:11    ( ERROR )
   5.
              
   6.
      calibrate /dev/sdc1  00:00:00    ( SUCCESS )
   7.
              
   8.
      path: /dev/sdc1
   9.
      start: 600
  10.
      end: 15667199
  11.
      size: 15666600 (7.47 GiB)
  12.
      delete partition  00:00:11    ( ERROR )
  13.
      libparted messages    ( INFO )
  14.
              
  15.
      Input/output error during write on /dev/sdc
  16.
       
  17.
      ========================================
```
And I tried using fdisk but got another error (lost the output).

I'm not sure what's wrong.  Hopefully there is a workaround.  I don't want this drive to not work in Ubuntu, because I really wanted a large enough drive to boot a persistent OS off of.  My 2GB drives weren't big enough for my purposes.

---

### Post by InfectedWithDrew on 2009-06-03
Bumping.

---

### Post by InfectedWithDrew on 2009-06-04
Another bump.  Any help, anyone?

---

### Post by Chronon on 2009-06-05
Sorry, I don't know why you're getting errors.  I did want to mention that you could use such a player with Rockbox's voice interface if you still wanted to use it as an audio player.

---

### Post by InfectedWithDrew on 2009-06-06
> **Chronon said:**
> Sorry, I don't know why you're getting errors.  I did want to mention that you could use such a player with Rockbox's voice interface if you still wanted to use it as an audio player.

I had Rockbox on it but I couldn't have set it to use voice, since the screen was broken.

---

### Post by Chronon on 2009-06-12
Hi.

Sorry about the late reply.  You can set the options via a .cfg file.  If you're interested in pursuing this we can help you out on the Rockbox forums.  :)

---

### Post by InfectedWithDrew on 2009-06-12
> **Chronon said:**
> Hi.

Sorry about the late reply.  You can set the options via a .cfg file.  If you're interested in pursuing this we can help you out on the Rockbox forums.  :)

I wish you had told me this earlier.  I have already formatted the device on Windows.  I don't think it has its original firmware anymore, and since it's a Rhapsody model... I don't think it'll work at all anymore.

---

