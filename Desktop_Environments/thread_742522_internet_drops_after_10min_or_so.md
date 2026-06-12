---
title: "internet drops after 10min or so"
date: 2008-04-01
forum: Desktop Environments
---

### Post by uknowho008 on 2008-04-01
if i stop using the internet for about 10 minutes or so ubuntu drops the connection. i run ifconfig and i still have the same ip address and everything and it works fine in windows. i recently removed a network card and went back to using the onboard one when this started. i have to restart the whole computer to have internet again. any ideas? thanks.

---

### Post by warp99 on 2008-04-02
When the connection drops you don't need to reboot the computer. Just issue the following command:

```
sudo /etc/init.d/networking restart
```

The only time you need to reboot Linux is for a kernel update since you can restart all of the services. Does this happen on the on-board port or just the NIC? It may be that the NIC needs certain parameters set.

---

### Post by canistra on 2008-04-02
this is a issue with some providers, it seems that networkd drops if it isn't used for some time, just open a terminal and write ping google.com

---

### Post by uknowho008 on 2008-04-02
i've run that command before and it didn't work. also is is the onboard ethernet, not the nic. i took out the nic. and its not my service provider, it used to work fine until i took the nic out as well as before i ever put the nic in. "ping google.com" times out as well. thanks for the replies.

---

