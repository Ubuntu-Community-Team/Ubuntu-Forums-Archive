---
title: "wifi not working."
date: 2020-12-31
forum: Debian
---

### Post by gardenair on 2020-12-31
hi,
Though it is ubuntu commnity forum but  I have Debian 10 wifi issue. Ubuntu is derived from Debian so I think I am the place where I can get its help. Well, coming to my point I just use Ubuntu 20 live USB on my laptop, wifi works perfect on it.  Then I have installed Debian 10 on the same Laptop. The LAN point is working but wifi is not working.

Following is the output of the list of the network interface.
```
root@debian:~# lspci | egrep -i --color 'network|ethernet'
00:19.0 Ethernet controller: Intel Corporation 82579LM Gigabit Network Connection (rev 04)
02:00.0 Network controller: Intel Corporation Centrino Advanced-N 6205 [Taylor Peak] (rev 34)

root@debian:~# lspci | egrep -i --color 'network|ethernet|wireless|wi-fi'
00:19.0 Ethernet controller: Intel Corporation 82579LM Gigabit Network Connection (rev 04)
02:00.0 Network controller: Intel Corporation Centrino Advanced-N 6205 [Taylor Peak] (rev 34)
```

I am adding my sources.list file.

```
deb http://deb.debian.org/debian buster main
deb http://security.debian.org/debian-security buster/updates main contrib
deb-src http://security.debian.org/debian-security buster/updates main contrib
```

I should be thankful if some guide me for wifi drivers installation. One thing which I understand is my laptop is using **Intel wireless** card in my laptop. 

Thanks in advance.

---

### Post by howefield on 2020-12-31
Thread moved to the "*Debian*" forum.

---

### Post by jeremy31 on 2020-12-31
You will likely need non-free repos and the Intel firmware package to have wifi on Debian

---

### Post by gardenair on 2021-01-04
Thanks "         jeremy31"for your kind reply.Appreciate it. Just for testing point of view I use the same laptop again and install windows 10 on it .The wifi was working perfect. In the device manager  under Network adapters  it shows " **Intel  Centrino  Advanced-N6205** ".

I google it and it shows relevant site

[https://www.iodocs.com/install-driver-intel-corporation-wireless-6205-debian-stretch/](https://www.iodocs.com/install-driver-intel-corporation-wireless-6205-debian-stretch/)

I add  the following line in /etc/resources.list

```
deb http://deb.debian.org/debian buster main non-free
```
 then apply 
```
# apt-get update; apt-get install firmware-iwlwifi
```
The last command 
```
root@debian:/home/test#  modprobe -r iwlwifi; modprobe iwlwifi
bash: modprobe: command not found
bash: modprobe: command not found

```

I reboot the system and during loading I see the *wifi  led light glowing means wifi is up*. In XFCE under Wi-Fi Networks *I can see all available networks*.I try one of them which is in my room  it does not connect and after few min the wifi disable  but after reboot it again enable .

Technically I think that the last command **modprobe -r iwlwifi; modprobe iwlwifi** not execute which is the issue.
Kindly guide me that how can I fix the issue ? why  Debian  shows command not found ? How may I enable it ?

Thanks

---

