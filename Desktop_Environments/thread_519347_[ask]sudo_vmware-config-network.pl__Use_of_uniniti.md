---
title: "[ask]sudo vmware-config-network.pl : Use of uninitialized value"
date: 2007-08-06
forum: Desktop Environments
---

### Post by urangkayo on 2007-08-06
i have install vmware-player 1.0.2-2, using sudo apt-get install vmware-player, but when configure process, i have error message like this:
> 
Use of uninitialized value in split at /usr/bin/vmware-config-network.pl line 4472.
Use of uninitialized value in bitwise or (|) at /usr/bin/vmware-config-network.pl line 4476.
Use of uninitialized value in bitwise or (|) at /usr/bin/vmware-config-network.pl line 4476.
Use of uninitialized value in bitwise or (|) at /usr/bin/vmware-config-network.pl line 4476.
Use of uninitialized value in bitwise or (|) at /usr/bin/vmware-config-network.pl line 4476.
Use of uninitialized value in split at /usr/bin/vmware-config-network.pl line 4472.
Use of uninitialized value in bitwise or (|) at /usr/bin/vmware-config-network.pl line 4476.
Use of uninitialized value in bitwise or (|) at /usr/bin/vmware-config-network.pl line 4476.
Use of uninitialized value in bitwise or (|) at /usr/bin/vmware-config-network.pl line 4476.
Use of uninitialized value in bitwise or (|) at /usr/bin/vmware-config-network.pl line 4476.
Use of uninitialized value in concatenation (.) or string at /usr/bin/vmware-config-network.pl line 720.


[FONT="Courier New"][SIZE="3"]$uname -a
Linux urangkayo 2.6.20-16-lowlatency #2 SMP PREEMPT Thu Jun 7 20:23:03 UTC 2007 i686 GNU/Linux[/SIZE][/FONT]

i try to run 
$sudo vmware-config-network.pl

but the problem is still the same.

how to fix this problem because i can't Perl :)

thanks

---

