---
title: "Internet Connection lost on dual boot"
date: 2006-08-16
forum: Desktop Environments
---

### Post by pt123 on 2006-08-16
When I restart and use ubuntu after using Windows XP I don't have internet connection. 

I have cable broadband and I get assigned two different IPs in Ubuntu and XP. 
So I have a feeling this might be causing the problem. 

To restore the internet connection when I lose it in ubuntu I have to deactivate my eth1 connection and then 
sudo restart networking 

Then I have to reboot. 

As you can see this annoying. Is there a script I can run to do this when I boot up. Or fix the DHCP so it tries to get a new IP on start up everytime?

When I don't have internet connection when I try:
ifdown eth1

I get this:
Sending on Socket/fallback
DHCPRELEASE on eth1 to 211.29.132.xx port 67
send_packet: Operation not permitted

---

### Post by michux on 2006-08-16
> **pt123 said:**
> When I restart and use ubuntu after using Windows XP I don't have internet connection. 

I have cable broadband and I get assigned two different IPs in Ubuntu and XP. 
So I have a feeling this might be causing the problem. 

To restore the internet connection when I lose it in ubuntu I have to deactivate my eth1 connection and then 
sudo restart networking 

Then I have to reboot. 

As you can see this annoying. Is there a script I can run to do this when I boot up. Or fix the DHCP so it tries to get a new IP on start up everytime?

When I don't have internet connection when I try:
ifdown eth1

I get this:
Sending on Socket/fallback
DHCPRELEASE on eth1 to 211.29.132.xx port 67
send_packet: Operation not permitted

I had a similar problem with some no-name cable provider. I had to either restart twice or physically unplug the ethernet cable and plug it back to get a normal IP address from DHCP. Perhaps it's the same in your case. Sometimes 3 or 4 "dhclient eth1" did the job.
My problem was not Linux-specific. If I used Linuxa dn then rebooted to Windows the same thing used to occur.

---

### Post by pt123 on 2006-08-17
I was hoping some linux guru would know how to release the DHCP on boot up. 

Back to good ol' Windows.

---

### Post by murataht on 2006-08-17
> **pt123 said:**
> 
When I don't have internet connection when I try:
ifdown eth1

I get this:
Sending on Socket/fallback
DHCPRELEASE on eth1 to 211.29.132.xx port 67
send_packet: Operation not permitted

try to add sudo 
```
sudo ifdown eth1
```
this should work.
then try
```
sudo ifup eth1
```
this should bring back your internet connection.

edit:
here is a similar problem in another post:
[http://www.ubuntuforums.org/showthread.php?p=1389437#post1389437](http://www.ubuntuforums.org/showthread.php?p=1389437#post1389437)

---

### Post by pt123 on 2006-08-19
^ Yeah that was suggested by TLE in this thread:

[http://ubuntuforums.org/showthread.php?t=208548](http://ubuntuforums.org/showthread.php?t=208548)

> Ok so what I did and what seems to work for me is to add the following to lines to /etc/rc.local before the exit 0 line:

sudo ifdown eth0
sudo ifup eth0



Seems to be working most of the times :
Tested 4 times - failed 1

Thanks for your help

---

### Post by pt123 on 2006-08-21
Not too promising now : 8 times - 3 fails.

---

