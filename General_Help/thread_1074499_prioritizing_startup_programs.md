---
title: "prioritizing startup programs"
date: 2009-02-19
forum: General Help
---

### Post by pasha07 on 2009-02-19
I have Evolution mail notification at startup. However, it starts before my wireless connects to the Internet so it always give an error message. 

Is there a way to prioritise the order of the startup programs or to make it start after the wireless is connected?

Thanks a bunch

---

### Post by albandy on 2009-02-19
You can make a custom script like this.
Make a file called landetect
then change it's permissions to 755 
chmod 755
edit it and put the contents above 

#! /bin/bash
LAN=OFF
EVOLUTION="type here the evolution notification command"

while [ "$LAN" == "OFF" ]
do
ROUTE=$(route -n | cut -f '1' -d ' '| grep 0.0.0.0)

	if [ "$ROUTE" == "0.0.0.0" ]
	then
	LAN=ON
	fi

sleep 1
done
$EVOLUTION &

---

### Post by pasha07 on 2009-02-20
Thanks a lot.. that was really helpful.. it's working fine now..

---

