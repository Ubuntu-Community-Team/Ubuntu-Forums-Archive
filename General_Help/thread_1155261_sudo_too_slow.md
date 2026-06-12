---
title: "sudo too slow"
date: 2009-05-10
forum: General Help
---

### Post by max7 on 2009-05-10
I experience too slow sudo.

When I enter "sudo ls" I have to wait minutes to see dir listing.
Same happens when I type it second time.
It does not asks me password but I still have to wait minutes to see any results.
CTRL + C does not work

When I searched google with "sudo too slow" (with quotes) I got not results at all.

I was fine before.

What is wrong and where should I look?

Please, help.

---

### Post by Brandon Williams on 2009-05-10
Running sudo requires a name server lookup for your machine's hostname. If you do not have an entry in /etc/hosts assigning your hostname to a localhost interface, then sudo will attempt a hostname lookup through your configured DNS server as per /etc/resolv.conf. That lookup might take a while if the hostname of your machine is not publicly resolvable.

Double-check to make sure that there is an entry in your /etc/hosts file for your machine's hostname. It should look something like this:
```
127.0.1.1 hostname
```

If this entry exists, then it is probably something else. Still, you could double check by running tcpdump in a separate terminal:
```
$ sudo tcpdump -nvvv -i wlan0 port 53
```
Replace 'wlan0' with the name of your active interface.

With tcpdump running, run 'sudo ls' and check to see if there is any output from tcpdump. If there is, especially if there is only an outgoing request a no incoming response, then you should double-check /etc/hosts again.

---

### Post by max7 on 2009-05-13
Thank You for very much.

I had 127.0.1.1 hostname
(with correct hostname)

The problem happened when I lost inet connectivity with my main ISP and I switched to ADSL modem.

If it will happen second time I would be able to debug it with your tcpdump query.

---

### Post by max7 on 2009-05-13
BTW I added 

sudo route add -net 127.0.0.0/8 dev lo


Not sure if it makes sense but when it happened it was very odd.

---

### Post by max7 on 2009-05-13
same happened again after I switched internet.


I switch inet using following script

```
#!/bin/bash
sudo route del default
sudo route add default gw 192.168.0.27
sudo /home/user/bin/setnameserver.sh 192.168.0.27
```

setnameserver.sh
```
#!/bin/bash
echo "nameserver "$1 > /etc/resolv.conf
```


I have active terminal with
```
sudo tcpdump -nvvv -i eth0 port 53
```


My hostname resolve and and nothing happen when I try to resolve it.

My internet also works. Names are resolve as usual. I wrote this post using that connection.


I have kubuntu and windows box that also use 192.168.0.27. No other problems. sudo works fine on kubuntu.

I was using that scripts for years without problems with sudo.

---

### Post by max7 on 2009-05-13
recov.conf
> cat /etc/resolv.conf
### BEGIN INFO
#
# Modified_by:  NetworkManager
# Process:      /usr/bin/NetworkManager
# Process_id:   5376
#
### END INFO



nameserver 192.168.0.27



Seems like it is also modified by NetworkManager after I did it with my script sudo /home/user/bin/setnameserver.sh 192.168.0.27.

My script is not adding comments to the file.

---

### Post by max7 on 2009-05-14
I have that problem with sudo again and it was fixed after restart.

I feel it is linked with networking but hostname and routing is fine.

Any idea?

---

### Post by m_gr_01 on 2013-01-19
I hope you have found a solution, by now. 
But, just in case you haven't and to help others:
1) Yes, the problem is indeed the hostname resolution.
2) Yes, likely NetworkManager does it.
3) Depends on your setup, i.e. NetworkManager configuration:
   a) It may be changing your hostname according to the DHCP server request (there is an option for that)
   b) It may be changing your host fullname (e.g. mypc.myhome.vu), according to the router's (DHCP) "beliefs" and because of your network naming and because you have not added the simple hostname to your /etc/hosts.
Try to add in the 127.0.1.1 line your simple hostname (e.g. mypc) irrelevantly of any full hostname in there. 
Example: You named your machine Lucy. NetworkManager adds or changes a line in /etc/hosts like 127.0.1.1 lucy.local or lucy.mydomain.eu . 
You change (or add) it to 127.0.1.1 lucy (and whatever else name separated by space) . 
It did the trick for me.

---

### Post by oldos2er on 2013-01-19
Old thread closed.

---

