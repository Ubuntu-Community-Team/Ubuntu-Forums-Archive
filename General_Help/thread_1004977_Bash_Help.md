---
title: "Bash Help"
date: 2008-12-07
forum: General Help
---

### Post by joec369 on 2008-12-07
OK, I need help with a part of my script I am trying to make. What I have to do is to write a script to ping a host, and then if the host it up connect to it using telnet.

This is what I have so far:

#! /bin/bash
echo "Input an IP address to Ping"
read IP
echo "How many times do you want to Ping?"
read Count
echo "Pinging $IP $Count times"
ping $IP -c $Count || { echo "Nobody Home Go Away" >&2; exit; }
rup $IP || { echo "Host is Up" >&2; exit; }

It works. It pings and lets the user know if the host is up or down. Now I am having trouble moving forward. If the host is up, I need to start the telnet part. So how do I say, if host is up, start telnet? I basically need the bridge between the up host being pinged and starting the telnet.

Thanks for any help in advance.

Joe

---

### Post by phinullfermata on 2008-12-07
I don't have rup on my computer, but find out what it returns, you can use an if statement from there, like:

```
if [ rup $ip ] then;
... telnet command....
fi
```

if the rup command returns 1 when the ip address is up or:

```
if [ ! rup $ip ] then;
... telnet command....
fi
```

if it returns 0 when the ip is up

I believe the if statement executes as long as the return value of whatever is in between the square brackets is non-zero.

Hope that helps.  Good luck :)

---

