---
title: "Only Firefox can connect.."
date: 2006-07-21
forum: Desktop Environments
---

### Post by CVDpr on 2006-07-21
I cant get conneted to the internet., so i cant get updates ect...

Then i disable the IPV6 in Firefox and now i can use it, then i disable the IPV6 in ubuntu 6.06 but its still the same no connection to Add/Remmove , Upates , Gaim ect... only Firefox can connect.

Why Firefox are the only thing that see my connection?
Help please, any aideas?

---

### Post by Thund3rstruck on 2006-07-21
Are you using a proxy server?

---

### Post by CVDpr on 2006-07-21
> **Thund3rstruck said:**
> Are you using a proxy server?

nop. Direct connection and DHCP.

---

### Post by T700 on 2006-07-21
Any firewalls or firewall interfaces (Firestarter, Guard Dog, etc.) running?  Have you worked on the IP Tables?

Paul

---

### Post by CVDpr on 2006-07-21
> **T700 said:**
> Any firewalls or firewall interfaces (Firestarter, Guard Dog, etc.) running?  Have you worked on the IP Tables?

Paul

Hey im new in linux/ubuntu i have no clue waht are you saying!!

How can i check this stuff?

---

### Post by fdrake on 2006-07-21
did you try to reset the modem and then reboot the pc?

---

### Post by neouser99 on 2006-07-21
try doing something like either of these two commands ```
$ nslookup google.com
$ dig google.com
``` 
If those fail, then it might be a dns problem. if they are successful, trying pinging google.com with ```
$ ping google.com
```
if these come back with success stuff let us know some more.

-neo

---

### Post by CVDpr on 2006-07-21
cvd@cvd-desktop:~$ nslookup google.com
Server:         192.168.1.1
Address:        192.168.1.1#53

Non-authoritative answer:
Name:   google.com
Address: 72.14.207.99
Name:   google.com
Address: 64.233.167.99
Name:   google.com
Address: 64.233.187.99
------------------------------------------
cvd@cvd-desktop:~$ dig google.com

; <<>> DiG 9.3.2 <<>> google.com
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 58117
;; flags: qr rd; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;google.com.                    IN      A

;; ANSWER SECTION:
google.com.             10000   IN      A       72.14.207.99

;; Query time: 2 msec
;; SERVER: 192.168.1.1#53(192.168.1.1)
;; WHEN: Fri Jul 21 20:52:17 2006
;; MSG SIZE  rcvd: 44
------------------------------------------------------------

---

### Post by cliche on 2006-07-21
hi, im having pretty much indentical issues.

fresh install. no connection. could ping google.com but that was all. disabled ipv6 both in firefox and modprobe.d firefox can now connect but nothing else

some data

```
jon@bartlet:~$ nslookup google.com
Server:         192.168.1.1
Address:        192.168.1.1#53

Non-authoritative answer:
Name:   google.com
Address: 72.14.207.99

jon@bartlet:~$ dig google.com

; <<>> DiG 9.3.2 <<>> google.com
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 16928
;; flags: qr rd; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;google.com.                    IN      A

;; ANSWER SECTION:
google.com.             10000   IN      A       72.14.207.99

;; Query time: 2 msec
;; SERVER: 192.168.1.1#53(192.168.1.1)
;; WHEN: Sat Jul 22 01:56:12 2006
;; MSG SIZE  rcvd: 44

jon@bartlet:~$ ping google.com
PING google.com (72.14.207.99) 56(84) bytes of data.
64 bytes from google.com (72.14.207.99): icmp_seq=1 ttl=232 time=102 ms
64 bytes from google.com (72.14.207.99): icmp_seq=2 ttl=232 time=104 ms
64 bytes from google.com (72.14.207.99): icmp_seq=3 ttl=232 time=102 ms
64 bytes from google.com (72.14.207.99): icmp_seq=4 ttl=232 time=104 ms
64 bytes from google.com (72.14.207.99): icmp_seq=5 ttl=232 time=102 ms
64 bytes from google.com (72.14.207.99): icmp_seq=6 ttl=232 time=102 ms
64 bytes from google.com (72.14.207.99): icmp_seq=7 ttl=232 time=102 ms
64 bytes from google.com (72.14.207.99): icmp_seq=8 ttl=232 time=102 ms
64 bytes from google.com (72.14.207.99): icmp_seq=9 ttl=232 time=102 ms
64 bytes from google.com (72.14.207.99): icmp_seq=10 ttl=232 time=102 ms
64 bytes from google.com (72.14.207.99): icmp_seq=11 ttl=232 time=104 ms
64 bytes from google.com (72.14.207.99): icmp_seq=12 ttl=232 time=104 ms
64 bytes from google.com (72.14.207.99): icmp_seq=13 ttl=232 time=103 ms
64 bytes from google.com (72.14.207.99): icmp_seq=14 ttl=232 time=103 ms

--- google.com ping statistics ---
14 packets transmitted, 14 received, 0% packet loss, time 13011ms
rtt min/avg/max/mdev = 102.053/103.199/104.755/1.039 ms
jon@bartlet:~$


```

i have some experience with ubuntu but have been out of the loop for a while. from searching the forums most of today for a solution seems a fair amount of people are having similar issues. hope i can help get to the bottom of the problems.

---

### Post by neouser99 on 2006-07-21
how about these two
```
$ ping google.com
$mtr google.com
```
are there any hops that have problems in there? mtr is a constant traceroute program that gives you an idea of how packets get across the internet.

-neo

---

### Post by cliche on 2006-07-21
> **neouser99 said:**
> how about these two
```
$ ping google.com
$mtr google.com
```
are there any hops that have problems in there? mtr is a constant traceroute program that gives you an idea of how packets get across the internet.

-neo

no problems showing with mtr.

tbh i think the problem is closer to home. and certainly related to ipv6.

seems i havn't managed to fully disable ipv6 accoring to these checks suggested in a different thread.

```
jon@bartlet:~$ ip -6 route
fe80::/64 dev eth0  metric 256  expires 2133158sec mtu 1500 advmss 1440 hoplimit 4294967295
ff00::/8 dev eth0  metric 256  expires 2133158sec mtu 1500 advmss 1440 hoplimit 4294967295
unreachable default dev lo  proto none  metric -1  error -101 hoplimit 255
jon@bartlet:~$ ip -4 route
192.168.1.0/24 dev eth0  proto kernel  scope link  src 192.168.1.3
default via 192.168.1.1 dev eth0
jon@bartlet:~$ ip a | grep inet6
    inet6 ::1/128 scope host
    inet6 fe80::2c0:9fff:feeb:d5ef/64 scope link
jon@bartlet:~$

```


EDIT:

found the thread with the changes i made to diable ipv6 if it helps:

[http://www.ubuntuforums.org/showthread.php?t=87798&highlight=disable+ipv6](http://www.ubuntuforums.org/showthread.php?t=87798&highlight=disable+ipv6)

i made the changes in aliases not making a bad_list file.

---

### Post by cliche on 2006-07-21
ok... added the bad_list file with changes aswell but the checks i posted still show same result suggesting ipv6 is still active (if advice from other post is correct)

---

### Post by neouser99 on 2006-07-21
i have to say that i am not really sure what is going on. it doesn't really look like it is something wrong with the ipv6, but i am kinda out of ideas...
how were the times on the mtr? was there any loss?

-neo

---

### Post by cliche on 2006-07-21
neouser99: 1-2% loss between me and my router the rest of the hops show 0% loss.

everybody: i've been searching these forums all day and seen a lot of problems similar that all seem related. anyone else had similar problems post links to your threads here (if you posted about it allready) or describe your problems and hopefully together we can work out whats causing this problem. 

i agree in that i don't think ipv6 is the cause of the problem but one of many related things that have been broken by an as yet undiscovered problem.

---

### Post by neouser99 on 2006-07-21
the loss isn't as big of a deal... your pings to google were at about 100ms... which is kinda high latency, was that number really high anywhere else?

---

### Post by cliche on 2006-07-21
im getting high latency on my mac aswell. but that can connect to the inernet fine. the latency problem i think is a problem with my isp. BT(UK) has fubard alot of their network recently

i know im not an expert or anything but im pretty sure that the problem is not with my internet connection or my network as like i allready said firefox is now working fine now i disabled ipv6 from about:config. but nothing else (eg synaptic, updater) can connect. which suggest a problem with ipv6 or something related to it.

---

### Post by cliche on 2006-07-22
shameless bump

---

### Post by CVDpr on 2006-07-22
Thats the beauty of Linux/Ubuntu!!!

The Question is, Why Firefox can but the rest not(Update,Gaim ect.)?:-k

Maybe with Suse i have better luck!!

---

