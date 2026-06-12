---
title: "ShieldsUP! Scan Report"
date: 2009-01-30
forum: Desktop Environments
---

### Post by sharathpaps on 2009-01-30
I just installed firestarter and I ran a test at ShieldsUP to check it. This is the scan report :

```
GRC Port Authority Report created on UTC: 2009-01-31 at 03:30:37

Results from scan of ports: 0-1055

    1 Ports Open
    0 Ports Closed
 1055 Ports Stealth
---------------------
 1056 Ports Tested

NO PORTS were found to be CLOSED.

The port found to be OPEN was: 53

Other than what is listed above, all ports are STEALTH.

TruStealth: FAILED - NOT all tested ports were STEALTH,
                   - NO unsolicited packets were received,
                   - NO Ping reply (ICMP Echo) was received.

```

When I mouse over the open port it says "53 / domain Domain Name Server" . Is it ok for the port to be open? I'm worried because the test says 'FAILED'.

---

### Post by Mud.Knee.Havoc on 2009-01-30
Port 53 is for DNS.  It seems that you've opened this port in firestarter.

---

### Post by sharathpaps on 2009-01-31
> **Mud.Knee.Havoc said:**
> Port 53 is for DNS.  It seems that you've opened this port in firestarter.

But I've done nothing to firestarter. Just installed it and started it. I have not configured it to open any ports or anything!!!?

---

### Post by abn91c on 2009-01-31
its not firestarter, check your router settings

---

### Post by Shazaam on 2009-01-31
Most broadband modems act as a router/NAT firewall these days. That is what Shields Up! is probing. You have to find out the IP address of your pc and manually enter it into the test page at GRC to get a true readout.

---

