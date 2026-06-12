---
title: "Problems with bluetooth."
date: 2007-12-05
forum: Desktop Environments
---

### Post by KoRnKiD on 2007-12-05
Hey, I cant get my phone to pair with my computer.

kr0n@shane:~$ hcitool scan
Scanning ...
        00:19:A1:63:51:42       shane

kr0n@shane:~$ sudo hcitool cc 00:19:A1:63:51:42
kr0n@shane:~$ sudo hcitool auth 00:19:A1:63:51:42
Not connected.

i have changed the passkey in /etc/bluetooth/hcid.conf and i put the same passkey in the pin file and its not working.... is the pin file just suppose to be the passkey and nothing else? quotes?

thanks in advance

---

### Post by metalheart on 2007-12-05
It may be different for your phone, but I do pairing like that:

Make sure the bluetooth applet is running (indicated by the bluetooth icon in the notification area). Then I search from my phone for bluetooth devices. If the correct one is found I select it and enter the pin code. After that the password popup appears on my computer, I click it and enter the same pin I used on the phone. Done.

Maybe you change the configuration file back to how it was and run

```
/etc/init.d/bluetooth restart
```

befor trying again.

---

### Post by KoRnKiD on 2007-12-05
hmm, i do not get the icon, although bluetooth is running..

---

### Post by _hawk_ on 2007-12-05
First make sure you have the bluez-utils (aptitude)

I get it working using first

hcitool scan

then to connect, I use

hidd --connect <address>

Don't know if this helps, but at least this way works for me...

---

### Post by KoRnKiD on 2007-12-05
well, i got the icon for "bluetooth file sharing" but not the bluetooth icon... if i try sending a file it shows up on my phone and asks for a passkey... but it wont pair because i think the pass is not working

---

### Post by metalheart on 2007-12-05
The program I'm talking about is bluetooth-applet.

---

