---
title: "GUI problems"
date: 2011-09-30
forum: Desktop Environments
---

### Post by zaidst on 2011-09-30
Hello Everybody 
 
I have ubuntu 11.10 beta 2 with no gui or any desktop enviornment 
I have only GDM and LightDM , and the default is GDM .
On my login screen .. I have only 2 choices :
1. Recovery Console 
2. User Defined Session 
 
Now , I wan to install Gnome ... When I enter the tty2 session and write the following command sudo apt-get install gnome .. here what the last line in the result is :
 
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
 
I listen to his advice 
 
sudo apt-get update 
 
W: Some index files failed to download. They have been ignored , or old ones used instead.
 
sudo apt-get install gnome --fix-missing
 
E: Aborting install 
 
........................
 
Sorry guys i can't quote all the results bcz it's hundredes of lines and i can't copy them to another pc 
 
Please Help 
 
I'm here to listen to your Recommendations 
 
Thanks in Advanced

---

### Post by sanderd17 on 2011-09-30
Do you have an internet connection? Try
```

ping google.com

```
(or any other site)

and see if it responds

---

### Post by zaidst on 2011-09-30
> **sanderd17 said:**
> Do you have an internet connection? Try
```

ping google.com

```
(or any other site)
 
and see if it responds
 
 
 :o It seems no
 
```
ping [www.google.com]("http://www.google.com/")
```
 
ping: unkown host [www.google.com]("http://www.google.com")
 
```
ping 192.168.1.1
```   //my network ip
 
connect : Network is unreachable
 
 
.........................
 
 
So , it seems i have no access even to the network 
I face Network problem 
 
What to do in that case ??

---

### Post by sanderd17 on 2011-09-30
Is it a wired network? In that case, executing dhcpcd will probably be enough.

For wireless, do the following in tty:

```

iwconfig

```

there you should see your wireless card, probably called wlan0. If it's called otherwise, change the name in the next commands.

```

ip link set wlan0 up

```

Now it depends on your encryption:

for no encryption:
```

iwconfig wlan0 essid "networkname"

```

WEP:
```

iwconfig wlan0 essid "networkname" key "0241baf34c"

```

WPA ASCII key:
```

iwconfig wlan0 essid "linksys" key "s:pass1"

```

WPA:
If your /etc/wpa_supplicant.conf file is correct, 
```

wpa_supplicant -B -Dwext -i wlan0 -c /etc/wpa_supplicant.conf

```

otherwise, you need to do first
```

wpa_passphrase networkname "my_secret_passkey" > /etc/wpa_supplicant.conf

```

And as a final step, you can do
```
dhcpcd wlan0
```

---

### Post by zaidst on 2011-09-30
> **sanderd17 said:**
> Is it a wired network? In that case, executing dhcpcd will probably be enough.
 
For wireless, do the following in tty:
 
```

iwconfig

```
 
there you should see your wireless card, probably called wlan0. If it's called otherwise, change the name in the next commands.
 
```

ip link set wlan0 up

```
 
Now it depends on your encryption:
 
for no encryption:
```

iwconfig wlan0 essid "networkname"

```
 
WEP:
```

iwconfig wlan0 essid "networkname" key "0241baf34c"

```
 
WPA ASCII key:
```

iwconfig wlan0 essid "linksys" key "s:pass1"

```
 
WPA:
If your /etc/wpa_supplicant.conf file is correct, 
```

wpa_supplicant -B -Dwext -i wlan0 -c /etc/wpa_supplicant.conf

```
 
otherwise, you need to do first
```

wpa_passphrase networkname "my_secret_passkey" > /etc/wpa_supplicant.conf

```
 
And as a final step, you can do
```
dhcpcd wlan0
```
 
 
It's a wired Network 
 
how to execute dhcpcd ?

---

### Post by sanderd17 on 2011-09-30
just execute
```

dhcpcd

```
or maybe with the device
```

dhcpcd eth0

```

---

