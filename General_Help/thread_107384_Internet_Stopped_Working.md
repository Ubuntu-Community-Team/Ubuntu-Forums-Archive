---
title: "Internet Stopped Working"
date: 2005-12-22
forum: General Help
---

### Post by souled on 2005-12-22
Hello, I update my kernel to the newest one today. Can't remember the version, but it asked to restart my computer so I did. However, my internet no longer works. The rest of my computers have internet connection, so I know it's Ubuntu. When I boot with a Live CD of Knoppix, the internet works. Also, the networking doesn't work in Ubuntu (can't see networked computers). Can anyone help me fix my internet please? I'm guessing it's some service that's failing to start or something like that...

---

### Post by redactech on 2005-12-22
please do the following and post the result here (use the console)

a) uname -a

b) cat /etc/network/interfaces (or gedit /etc/network/interfaces)


c) ifconfig -a


d) ping (insert your gateway or high speed/adsl/cable modem IP here)

e) traceroute google.com

---

### Post by souled on 2005-12-22
Problem solved... I discovered that eth0 was not activated for some reason... Thanks for the reply, though.

---

