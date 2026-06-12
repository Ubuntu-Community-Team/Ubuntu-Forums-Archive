---
title: "Bluetooth Headset btsco"
date: 2005-12-13
forum: Desktop Environments
---

### Post by redman5087 on 2005-12-13
Hi,
I installed the bluetooth-alsa driver succesfull.
I "modprobe snd-bt-sco" successfully.
Then I did "hciconfig hci0 voice 0x0060"
I made a bluetooth pin file:
                 echo '#!/bin/sh' > /etc/bluetooth/pin
                echo 'echo "PIN:0000"' >> /etc/bluetooth/pin
                chmod +x /etc/bluetooth/pin

Restarted hcid

When I do:
    btsco -v 00:0D:44:03:6B:8A
I get
     btsco v0.4c
     Device is 2:0
     Voice setting: 0x0060
     Can't connect RFCOMM channel: Resource temporarily unavailable


I did everything by  another thread on this forum:
    [http://ubuntuforums.org/showthread.php?t=52296&highlight=bluetooth-alsa](http://ubuntuforums.org/showthread.php?t=52296&highlight=bluetooth-alsa)

Can someone help, please

Kind regards,
redman

---

### Post by gcain on 2005-12-26
Is the headset already discoverable when you enter the last command?

I get an error not unlike yours if I forget to make it discoverable, and the headset isn't already paired.

Let me know if this helps... :)

---

### Post by wieman01 on 2006-06-02
No sure but your saying you had installed Alsa successfully caught my attention. The README file of btsco says that it only works with the Alsa version that is integrated in the kernel, not the standalone one. So this may (or may not) explain your problem.

Try to avoid installing Alsa. Usually the sound should work "out of the box", so there is really no need to do that.

---

