---
title: "simple script for cheking users in the LAN with nmap"
date: 2008-06-12
forum: Education &amp; Science
---

### Post by frojnd on 2008-06-12
Ok, here is the thing. I use nmap for checking who's in the local area network. I wrote this simple script:

> 
#!/bin/bash

while nmap 192.168.0.*; do sleep 60; done


I've also made it executable and put it in /opt/kde3/bin/scan so I can start it from any location. This simple script checks ports on 192.168.0.* and after it scans it starts again in 60 seconds. When in LAN are 2 users and one router the nmap output is: 

> Nmap finished: 256 IP addresses (3 hosts up) scanned in 4.878 seconds


Now, I'd like to modify this script, so when nmap would give (>=4 hosts up) more or the same as 4 hosts that somehow program named audacious would start.

I would need to pipe the nmap output through the 2 cuts & store it in a variable. Then compare that variable with 4 or more, and take proper action if this condition is true.

Some guy on the #ubuntu gave me a tip how to cut: | cut -f6 -d" " | cut -f2 -d\( But I still wasn't able to pipe or to save this output to a variable. Can someone help me this one out. I know that here is many gurus. 

Thanx in advance.

---

### Post by opscure on 2009-01-26
```
#!/bin/sh
cnt=0
while nmap -sP 192.168.0.*>~/filenmap
do
cnt=`tail -1 ~/filenmap |cut -c 30-31`
	if [ "$cnt" -ge "4" ] 
	then
		/usr/bin/audacious &
	fi
sleep 60
done

```

This should do it.  If you want to just play a sound if there is 4 or more connected IPs then I would use aplay filename.wav or something similar.  This is going to start the audacious application every 60 seconds otherwise.

---

