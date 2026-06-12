---
title: "Network proxy not connecting"
date: 2009-10-15
forum: Desktop Environments
---

### Post by ambdeep on 2009-10-15
I need use a network proxy to connect to the internet......it works when i use it for firefox.....but it doesnt work when i try to use the update manager or the package installer........ive tried to chane the setting via systm->preferences->network proxy......but it doesnt seem to make any difference......plz help......thanks in advance!!!!

---

### Post by ambdeep on 2009-10-18
*bump*
Can somebody please help me......i cant update my system.....

---

### Post by linux-hack on 2009-10-19
first of all you can search the forum there are already answears to your question :

here is one of them :
```
sudo echo 'Acquire::http::Proxy "http://yourproxy.com:port";' > /etc/apt/apt.conf.d/proxy
```
if its not working put the ip adress and not the name of the proxy
you can also use'it like this :
```
http://]login:password@yourproxy.com:port
```

these are topics i found with the serach button...

[http://ubuntuforums.org/showthread.php?t=1041754&highlight=update+proxy](http://ubuntuforums.org/showthread.php?t=1041754&highlight=update+proxy)

[http://ubuntuforums.org/showthread.php?t=1274775&highlight=proxy+synaptic](http://ubuntuforums.org/showthread.php?t=1274775&highlight=proxy+synaptic)

[http://ubuntuforums.org/showthread.php?t=1207139&highlight=update+proxy](http://ubuntuforums.org/showthread.php?t=1207139&highlight=update+proxy)

---

