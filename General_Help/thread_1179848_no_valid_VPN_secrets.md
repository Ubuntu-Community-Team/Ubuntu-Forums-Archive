---
title: "no valid VPN secrets"
date: 2009-06-06
forum: General Help
---

### Post by DeViLDuD3 on 2009-06-06
I somehow managed to make the 'ADD' button active in the network manager vpn tab, no there another problem, I configuered the profile with my settings, when I connect to it, it says connection failed because there are no valid vpn secrets, I tried this [http://ubuntuforums.org/showthread.php?t=991144](http://ubuntuforums.org/showthread.php?t=991144) still nothing works, connecting again and again vanishes the network manager from the taskbar!
any help regarding it ?

---

### Post by DeViLDuD3 on 2009-06-06
hulo anyone ?

---

### Post by DeViLDuD3 on 2009-06-06
hulo anyone home ?

---

### Post by DeViLDuD3 on 2009-06-06
plz someone ! :(

---

### Post by DeViLDuD3 on 2009-06-07
can anyone plz help me out wid dis one :S ?

---

### Post by solidblu on 2009-09-18
[https://answers.launchpad.net/ubuntu/+source/network-manager/+question/48503](https://answers.launchpad.net/ubuntu/+source/network-manager/+question/48503)

It looks like for some reason it doesn't like having the passwords stored in Network Manager.


I also had to restart Network Manager once I updated the profile
 
(sudo /etc/init.d/NetworkManager restart)

---

### Post by Chronon on 2009-09-18
Huh.  I manage my VPN profiles from the nm-applet and don't have any issues.

---

### Post by phorque on 2009-10-14
> **solidblu said:**
> [https://answers.launchpad.net/ubuntu/+source/network-manager/+question/48503](https://answers.launchpad.net/ubuntu/+source/network-manager/+question/48503)

It looks like for some reason it doesn't like having the passwords stored in Network Manager.


I also had to restart Network Manager once I updated the profile
 
(sudo /etc/init.d/NetworkManager restart)

you sir, are a diamond

---

### Post by T3kG33k on 2009-11-05
> **solidblu said:**
> [https://answers.launchpad.net/ubuntu/+source/network-manager/+question/48503](https://answers.launchpad.net/ubuntu/+source/network-manager/+question/48503)

It looks like for some reason it doesn't like having the passwords stored in Network Manager.


I also had to restart Network Manager once I updated the profile
 
(sudo /etc/init.d/NetworkManager restart)

Yeah...Are you sure that command works?

---

### Post by effbiae on 2009-12-13
also

  ```
sudo service network-manager restart
```

---

### Post by pwnst*r on 2009-12-20
> **solidblu said:**
> [https://answers.launchpad.net/ubuntu/+source/network-manager/+question/48503](https://answers.launchpad.net/ubuntu/+source/network-manager/+question/48503)

It looks like for some reason it doesn't like having the passwords stored in Network Manager.


I also had to restart Network Manager once I updated the profile
 
(sudo /etc/init.d/NetworkManager restart)

I love you.

---

### Post by Found on 2009-12-24
> **solidblu said:**
> [https://answers.launchpad.net/ubuntu/+source/network-manager/+question/48503](https://answers.launchpad.net/ubuntu/+source/network-manager/+question/48503)

It looks like for some reason it doesn't like having the passwords stored in Network Manager.


I also had to restart Network Manager once I updated the profile
 
(sudo /etc/init.d/NetworkManager restart)

Awesome, thanks.

---

### Post by froglet1 on 2010-08-30
try the solution and patch here: [https://bugs.launchpad.net/ubuntu/+source/network-manager-openvpn/+bug/360818](https://bugs.launchpad.net/ubuntu/+source/network-manager-openvpn/+bug/360818)
it fixed it for me using vpnc in 10.04

---

