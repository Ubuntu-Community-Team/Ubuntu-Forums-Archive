---
title: "gdesklets and hddtemp sensor"
date: 2006-08-24
forum: Desktop Environments
---

### Post by shanepardue on 2006-08-24
when running the hddtemp gdesklet, i get 0 degrees as the temperature. hddtemp as well as libsensor are both installed. i've noticed no program can pick up my temperatures. i'm pretty sure i've had it working on a previous installation of maybe breezy or something so i think my hardware has sensors-capabilities. 

any help is great! thanks!

---

### Post by dutchman25 on 2006-08-24
I have the exact same problem.  I'd love to figure out how to get my notebook to read the temp. of the hard disk.

---

### Post by seanUSXIII on 2006-12-05
Sometimes this happens to me. Just restart the desklet and it should work 8)

---

### Post by dcstar on 2006-12-06
> **shanepardue said:**
> when running the hddtemp gdesklet, i get 0 degrees as the temperature. hddtemp as well as libsensor are both installed. i've noticed no program can pick up my temperatures. i'm pretty sure i've had it working on a previous installation of maybe breezy or something so i think my hardware has sensors-capabilities. 

any help is great! thanks!

Don't you need the **smartmontools** package for this?

---

### Post by airflow on 2007-09-14
Hello,

I have the same problem - the hddtemp-desklets don't work, although hddtemp works.

I can definitely say that hddtemp for itself works:

```
airflow@n069b019:~$ sudo hddtemp /dev/sda
/dev/sda: FUJITSU MHV2060BH PL                    &#65533;: 41°C
```

Also, the hddtemp-daemon is running (so the desklet doesn't need root-access):

```
airflow@n069b019:~$ telnet localhost 7634
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
|/dev/sda|FUJITSU MHV2060BH PL                    &#65533;|42|C|Connection closed by foreign host.
```

The desklet is configured correctly (right port, right harddisk) - still, every hddtemp-desklet (and there are a few of them) only reports 0°.

Any idea? I would really appreciate a solution, as my notebook has temperature-problems sometimes, and I would need a way to monitor the status.

Thanks,
airflow

---

### Post by Suikwan on 2008-07-12
I too am having trouble with gdesklets & hddtemp as well as all desklets that work with lmsensors.  I am able to run successfully xsensors, however I do have to manually point it to the sensor configuration file.  Is there any way to do the same thing with gdesklets?

---

