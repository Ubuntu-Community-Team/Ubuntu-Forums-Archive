---
title: "&quot;Google Earth + Proxy (login+pwd)&quot; Problem"
date: 2007-09-19
forum: Education &amp; Science
---

### Post by hzambran on 2007-09-19
At the University, I'm behind a proxy (that requires a login and password). I have set the proxy in the "System\Preferences\Network Proxy" and I'm able to connect to Internet using Firefox and to run Synaptic.

After the installation of Google Earth in my Feisty 7.04, Google Earth works fine, but If I close it and run it again, even without to close my session, it is not be able to connect to Google Server.

How can I solve this problem ?

---

### Post by Kyairan on 2007-10-22
I found some weird problems like this, i've worked around it by running Google-earth from the terminal and changing the shortcut from 'Application' to 'Application in Terminal'. I think it's ignoring the http_proxy env variable.

Joel.

---

### Post by pollux_master on 2007-10-31
Hi,

Got the same problem here, and after searching google groups found a solution:

from the terminal, i ran:

# http_proxy=[put_your_proxy_address_here] googleearth&

Worked fine.

---

### Post by darkazurka on 2007-11-15
This helped me! (using Ubuntu Gnu/linux 7.10 "Gutsy Gibbon")

The things below is just an example. Your proxy and port number are probably different. The below code I typed in a terminal.
1st step: ```
# http_proxy=[10.140.22.1:8080] googleearth&
```
2nd step: (this I typed in my home directory where google earth was installed, to launch google earth from the command line) ```
./googleearth
```

When I launch google earth in another way by double clicking an icon, then it says it won't connect to the server. When launching google earth from the command line, it works, and connects through the proxy. Thanks for your help!

---

### Post by ingsil on 2011-10-06
> **darkazurka said:**
> This helped me! (using Ubuntu Gnu/linux 7.10 "Gutsy Gibbon")

The things below is just an example. Your proxy and port number are probably different. The below code I typed in a terminal.
1st step: ```
# http_proxy=[10.140.22.1:8080] googleearth&
```
2nd step: (this I typed in my home directory where google earth was installed, to launch google earth from the command line) ```
./googleearth
```

When I launch google earth in another way by double clicking an icon, then it says it won't connect to the server. When launching google earth from the command line, it works, and connects through the proxy. Thanks for your help!
Please try edditing the environment variable.

#gedit /etc/environment

then add your proxy server like this

http_proxy="http://proxy.xxx.net:8080/"
ftp_proxy="ftp://proxy.xxx.net:8080/"
https_proxy="https://proxy.xxx.net:8080/"
all_proxy="socks://proxy.xxx.net:8080/"

save and restart your machine

---

### Post by overdrank on 2011-10-06
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]

---

