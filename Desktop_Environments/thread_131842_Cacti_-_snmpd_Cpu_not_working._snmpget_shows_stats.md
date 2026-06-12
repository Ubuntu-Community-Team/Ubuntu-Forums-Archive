---
title: "Cacti - snmpd Cpu not working. snmpget shows stats"
date: 2006-02-17
forum: Desktop Environments
---

### Post by mxc on 2006-02-17
Hi all,

I have set up snmp on our server for monitoring purposes. I am trying to get cacti to graph cpu utilisation. I have setup a community that can access v2c snmp and the queries must come from the localhost. I can get interfacet stats fine in cacti but not cpu stats.

If I run snmpget -V2c -c xxxx localhost ssCpuRawUser.0 I get info back. So I know snmp is working. What can I do to get cacti to report the results correctly?

---

