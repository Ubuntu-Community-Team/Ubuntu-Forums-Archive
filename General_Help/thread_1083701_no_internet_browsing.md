---
title: "no internet browsing"
date: 2009-03-01
forum: General Help
---

### Post by latiff on 2009-03-01
iam having xp with ubuntu dual boot cable modem connected in lan i coudnt connect internet in ubuntu only local ip is inging default gate way dns is not pinging i have hardware checking in ubuntu it is showing follwing error

Testing your connection to the Internet:

ERROR:root:Could not find def gateway info in /proc
Traceback (most recent call last):
File "/usr/share/hwtest/scripts/internet_test", line 132, in <module>
sys.exit(main(sys.argv[1:]))
File "/usr/share/hwtest/scripts/internet_test", line 118, in main
host = route.get_default_gateway()
File "/usr/share/hwtest/scripts/internet_test", line 81, in get_default_gateway
t1 = self._get_default_gateway_from_bin_route()
File "/usr/share/hwtest/scripts/internet_test", line 69, in _get_default_gateway_from_bin_route
if def_gateway:
UnboundLocalError: local variable 'def_gateway' referenced before assignment

how to solve this problem

---

