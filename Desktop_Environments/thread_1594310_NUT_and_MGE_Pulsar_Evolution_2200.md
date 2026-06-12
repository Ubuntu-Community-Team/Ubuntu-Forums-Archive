---
title: "NUT and MGE Pulsar Evolution 2200"
date: 2010-10-12
forum: Desktop Environments
---

### Post by egrimisu on 2010-10-12
Hey guy's,
I', trying to sync my ups with nut, i have configured nut.conf, upsd.users and upsmon.conf like the folowing:

nut.conf

MODE=standalone
[mge]                        {line 31 in my case}
driver=mge-shut
port=/dev/ttyS0

upsd.users

[monuser]
password = pass
allowfrom = localhost
upsmon master


upsmon.conf

MONITOR mge@localhost 1 monuser pass master

Everything great, now i try to start the nut eith "/etc/init.d/nut start" and i got:
/etc/nut/nut.conf: 31: [mge]: not found
 * Starting Network UPS Tools                                            [ OK ]

the 31 line contain the name of the ups mge in my case. what have i done wrong?

---

### Post by Suncat2000 on 2011-02-23
From the fact you omitted your ups.conf file, I'm assuming you didn't define the "mge" ups there. It looks like you stuffed that information into nut.conf instead.

---

### Post by egrimisu on 2011-02-23
> **Suncat2000 said:**
> From the fact you omitted your ups.conf file, I'm assuming you didn't define the "mge" ups there. It looks like you stuffed that information into nut.conf instead.

Hi, and thanks for the reply, i hava managed to configure it properly in the end :)
the only thing that i didn't succed is to shutdown another ipcop box from a ubuntu box using nut.

---

