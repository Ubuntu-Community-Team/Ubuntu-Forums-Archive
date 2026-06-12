---
title: "Ubuntu not resonding to outside requests"
date: 2009-01-11
forum: General Help
---

### Post by Go3Team on 2009-01-11
I'm running 8.04, with a MythTV installation.  The server is not responding to any request outside of the LAN.  It does not respond to SSH, VNC, or Apache2.  I have restarted Apache, and SSH.  I can access the box via SSH, VNC, and can pull up pages served by Apache on another computer on the LAN.  I am remotely accessing other computers on the LAN at my current location, so the router is properly forwarding to those computers.  I have double checked the router and rebooted it.  I can also access external webpages on the box with the problem, via VNC.  I'm stumped.

Thanks.

---

### Post by andresmh on 2009-01-11
Check Ubuntu's firewall setting. I think by default it blocks everything.

---

### Post by Go3Team on 2009-01-11
Everything I've read says that Ubuntu doesn't install a firewall by default.  I've never used one, but use MoBlock occasionally.

---

### Post by Go3Team on 2009-01-12
It was also working fine a few hours befre it stopped working right.

---

### Post by Yashiro on 2009-01-12
So what changed?

---

### Post by Go3Team on 2009-01-12
Nothing was installed .  It was getting GET requests from my cell (GPS Coordinates) and just quit responding. (to all external requests) Everything worked fine internally.  Looked at the firewall, it's not activated.  I did reboot and it fixed it, but it's happened before, and I can't remember what I did to fix it then without a reboot.

---

### Post by jre on 2009-01-12
> **Go3Team said:**
> Looked at the firewall, it's not activated.
How did you check? I strongly suggest to verify that with "iptables -L -nv". E.g. a normal firewall app might not notice that MoBlock is running. But a running MoBlock might explain your problems.

---

### Post by Go3Team on 2009-01-12
> **jre said:**
> How did you check? 
sudo ufw status: Firewall not loaded

> **jre said:**
> I strongly suggest to verify that with "iptables -L -nv". E.g. a normal firewall app might not notice that MoBlock is running. But a running MoBlock might explain your problems.

burke@mythTV-MasterBackend:~$ sudo iptables -L -nv
Chain INPUT (policy ACCEPT 39067 packets, 8855K bytes)
 pkts bytes target     prot opt in     out     source               destination                                                                                                  
12011 1890K moblock_in  all  --  *      *       0.0.0.0/0            0.0.0.0/0                                                                                                            state NEW MARK match !0x14

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination                                                                                                  
    0     0 moblock_fw  all  --  *      *       0.0.0.0/0            0.0.0.0/0                                                                                                            state NEW MARK match !0x14

Chain OUTPUT (policy ACCEPT 36130 packets, 8671K bytes)
 pkts bytes target     prot opt in     out     source               destination                                                                                                  
 2281  289K moblock_out  all  --  *      *       0.0.0.0/0            0.0.0.0/0                                                                                                            state NEW MARK match !0x14

Chain moblock_fw (1 references)
 pkts bytes target     prot opt in     out     source               destination                                                                                                  
    0     0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0                                                                                                            MARK match 0xa
    0     0 RETURN     all  --  *      *       192.168.1.0/24       192.168.1.0/                                                                                                 24
    0     0 NFQUEUE    all  --  *      *       0.0.0.0/0            0.0.0.0/0                                                                                                            NFQUEUE num 0

Chain moblock_in (1 references)
 pkts bytes target     prot opt in     out     source               destination                                                                                                  
  802 76479 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0                                                                                                            MARK match 0xa
 1227 78434 RETURN     all  --  lo     *       0.0.0.0/0            0.0.0.0/0                                                                                                    
 3046  948K RETURN     all  --  *      *       192.168.1.0/24       0.0.0.0/0                                                                                                    
 6936  788K NFQUEUE    all  --  *      *       0.0.0.0/0            0.0.0.0/0                                                                                                            NFQUEUE num 0

Chain moblock_out (1 references)
 pkts bytes target     prot opt in     out     source               destination                                                                                                  
  187 70544 REJECT     all  --  *      *       0.0.0.0/0            0.0.0.0/0                                                                                                            MARK match 0xa reject-with icmp-port-unreachable
 1227 78434 RETURN     all  --  *      lo      0.0.0.0/0            0.0.0.0/0                                                                                                    
  541 57850 RETURN     all  --  *      *       0.0.0.0/0            192.168.1.0/                                                                                                 24
    0     0 RETURN     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0                                                                                                            tcp dpt:443
    3   180 RETURN     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0                                                                                                            tcp dpt:80
  323 81728 NFQUEUE    all  --  *      *       0.0.0.0/0            0.0.0.0/0                                                                                                            NFQUEUE num 0

---

