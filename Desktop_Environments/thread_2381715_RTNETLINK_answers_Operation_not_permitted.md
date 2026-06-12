---
title: "RTNETLINK answers: Operation not permitted"
date: 2018-01-04
forum: Desktop Environments
---

### Post by tezarin on 2018-01-04
Hi all,

I am on the VPN and can access my work VMs via  SSH. But I cannot access to them on the browser. For example I have Nagios running on 10.75.7.3. I can access the VM via the terminal but cannot access it via the browser. In the past when I had that problem, I fixed it by adding the route to 10.75.x.x network but I can't remember the correct command anymore. This is the error I get: RTNETLINK answers: Operation not permitted

```


ip -a r
default via 192.168.1.1 dev wlp1s0  proto static  metric 600 
10.75.0.0/16 dev vpn0  proto static  scope link  metric 50 
60.170.118.194 via 192.168.1.1 dev wlp1s0  proto static  metric 600 
169.222.0.0/16 dev wlp1s0  scope link  metric 1000 
172.188.323.0/24 dev vpn0  proto kernel  scope link  src 172.16.212.37  metric 50 
192.168.1.0/24 dev wlp1s0  proto kernel  scope link  src 192.168.1.243  metric 600 
192.168.21.0/24 dev vpn0  proto static  scope link  metric 50 
192.168.50.0/24 dev vpn0  proto static  scope link  metric 50 



```

Can you please let me know how I can add that route please? I used to run a command similar to this:

```

 ip route add 10.75.7.0/24 via 192.168.1.1
RTNETLINK answers: Operation not permitted

```


Thank you in advace

---

