---
title: "KDE-su reports an error"
date: 2006-10-02
forum: Desktop Environments
---

### Post by lptr on 2006-10-02
Since I played around with KNetworkManager yesterday I having troubles when I try to start for example Adapt package manager. All kde-su commands do fail, now. Start message for adept usually like this: 

Error - KDE-su
su detected an error 

((like because I translated it from german dialog. Original msg was: 'su hat einen Fehler gemeldet'))

No messages in /var/log/messages are provided.

Anyone an idea what is broken?

rob*

---

### Post by kerry_s on 2006-10-02
What happens when you run it from a terminal?

sudo adept

---

### Post by lptr on 2006-10-02
Thanks for the hint this took me to the solution:
```

# sudo adept
```

told me in terminal:
```

sudo: unable to lookup air1 via gethostbyname()
```

Then I remembered, that yesterday I replaced hosts, too. My failure was, not to include this following lines:

```
127.0.0.1       localhost
127.0.1.1       air1

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```


So if sudo telling that gethostbyname cannot find machinename then all is clear ;-)

@kerry_s: Thanks


rob*

---

### Post by lptr on 2006-10-03
Ok found another glitch regarding kdesu:

For some reason (maybe I did it myself - but cannot remember) in ~/xinitrc there was the line:
```
xhost +localhost
```

This is definiitvely wrong with Dapper 6.06


It must be replaced with this line:
```
xhost +local:
```


I found this, because I use to have a start icon for konqueror(root). Started with kdesu it is much easier to manipulate system files. The command line looks like this:
```
# kdesu kfmclient openProfile filemanagement
```

This opens the password window to enter the password and runs kfmclient afterward with root rights.


Before I fixed xinitrc I got something like this, when I tried the upper command in a terminal window:
```
Xlib: connection to ":0.0" refused by server
...
konqueror: cannot connect to X server :0.0
kfmclient: ERROR: Couldn't start konqueror from konqueror.desktop...
```


Hope this helps others, too.

rob*

---

