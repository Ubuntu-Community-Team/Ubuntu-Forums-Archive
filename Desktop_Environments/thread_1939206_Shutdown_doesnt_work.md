---
title: "Shutdown doesnt work"
date: 2012-03-11
forum: Desktop Environments
---

### Post by ratanpd on 2012-03-11
I am using ubuntu 11.10 on my desktop (64 bit) for a long time. Few days back there was some issue with power supply and i have to shutdown my desktop using power button in hurry. Now when i am going to shutdown the desktop, the shutdown process starts and ubuntu logo and five dots comes and then it hangs. Can you tell me what went wrong in the situation of mine? any help will be appreciated.

log off works and restsrt works too.

sudo shutdown now –P doesnt work.

ratanp

---

### Post by whiskers751 on 2012-03-11
Try```
sudo halt
```

---

### Post by winh8r on 2012-03-11
try 


```
sudo shutdown -P now
```

time parameter should be the last one given

---

### Post by drdos2006 on 2012-03-11
I had the same problem on my ASUS motherboard with an onboard Realtek NIC. 

Had to disconnect the ethernet cable after shutdown for the Realtek to reset. Then I could use : sudo shutdown -h now ...  and this worked for me.

regards

---

### Post by ratanpd on 2012-03-11
I had tried both the 
sudo shutdown -P now  and 
sudo halt

but it didn't worked.

i followed this thread and it worked. (though I am not sure whether it was correct procedure/method)
[https://bugs.launchpad.net/ubuntu/+source/netbase/+bug/903825]("https://bugs.launchpad.net/ubuntu/+source/netbase/+bug/903825")

---

### Post by ratanpd on 2012-03-13
it worked for two days and now i am back to same issue.
it doesn't shutdown :(

Please help.

---

