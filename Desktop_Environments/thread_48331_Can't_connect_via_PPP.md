---
title: "Can't connect via PPP"
date: 2005-07-12
forum: Desktop Environments
---

### Post by D3k on 2005-07-12
Hello! I have some problems with KPPP. When I connetcting everything goes OK but after that KPPP gives the error (code 1). On other distros everything is OK. WTF?

I have ZyXEL Omin 56k Duo @ COM 1.

---

### Post by coolclassic on 2005-07-12
I would suggest that you check you device settings. Since you stated you're using an external modem, you may need to adjust the device. As a default, kppp (Internet Dial-Up Tool), defaults to /dev/modem, which will link to an internal modem if configured during the installation phase. 

The device settings are as follows:
com1 = /dev/ttyS0
com2 = /dev/ttyS1

Usually, external modems are either com1 or com2. Internals are com3 (ttyS2) or com4 (ttyS3).

In the settings area, you can also set the speed (safely) to 115K, and all will work well. 

Hope this helps, and let us know if this info helped.

---

### Post by D3k on 2005-08-31
Thank you, I wil try that. I can't live without internet. Especially when linux dstro contains small collection of programs.

> Usually, external modems are either com1 or com2. Internals are com3 (ttyS2) or com4 (ttyS3).

Actually I have 2 modems: an external (ZyXEL) and an internel WinModem (left from windows-using-times) Lucent WinModem.

P.S Which distro has bigger collection of apps - Ubuntu or Kubuntu. Maybe I will make a change.

---

### Post by D3k on 2005-08-31
OK, modem works, but KPPP shows the error (see my attach). Can you tell me what does it mean?

---

### Post by ippiraman on 2005-08-31
[QUOTE=D3k]
Aug 31 18:09:25 localhost pppd[7423]: The remote system is required to authenticate itself
Aug 31 18:09:25 localhost pppd[7423]: but I couldn't find any suitable secret (password) for it to use to do so.
Aug 31 18:09:25 localhost pppd[7423]: (None of the available passwords would let it use an IP address.)
[/QUOTE]

Try commenting out auth in /etc/ppp/options:

$ cat /etc/ppp/options | grep auth

# Require the peer to authenticate itself before allowing network
# authentication for specific peers.
auth

Find the line like the above one and put # before auth.

# Require the peer to authenticate itself before allowing network
# authentication for specific peers.
#auth

You can also try experimenting with modes of authentication PAP, CHAP, PAP/CHAP.

HTH

---

### Post by D3k on 2005-09-01
**ippiraman**
Thank you, thank you, and again, thank you!!! It WORKS, and I'm SO HAPPY now!!! 

May the force be with you!

---

### Post by ippiraman on 2005-09-01
no problem
 :)

---

