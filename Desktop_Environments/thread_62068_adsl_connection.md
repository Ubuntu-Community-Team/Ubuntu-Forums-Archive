---
title: "adsl connection"
date: 2005-09-03
forum: Desktop Environments
---

### Post by gerhard001 on 2005-09-03
hi!

I'm using kubuntu for 1 week. now i want to konnect to a adsl modem. What I have done:

1) netcard has the ip 10.0.0.140 netmask 255.255.255.0
2) pptp-linux is installed
3) ping to 10.0.0.138 (adsl-modem) is possible
4) file /etc/ppp/chap-secrets modified:  Username * password * (this entry i have entered)
5) file /etc/ppp/peers/adslHome created and modified:

user Username
noauth
noipdefault
defaultroute
persist
pty "/usr/sbin/pptp 10.0.0.138 --nolaunchppd"

6) now i have tried to connect to de net with /usr/sbin/pppd call adslHome
i have got no error message.

but when i try to ping [www.google.com](www.google.com) or to connect to enter google with konqueror i get the message: host not found!

WHAT AM I DOING WRONG??? PLEASE PLEASE HELP ME!!!!
thank you!!!!!!
gerhard

P.S.: sorry about my english!!! (I'm from Austria  :roll: )

---

### Post by Harleen on 2005-09-03
[QUOTE=gerhard001]hi!
2) pptp-linux is installed
[/QUOTE]

Are you shure this is the right package? I'm using the package pppoe, which also looks much nicer in its description. And while installing, it also sets up all needed changes to /etc/ppp/* files.

---

