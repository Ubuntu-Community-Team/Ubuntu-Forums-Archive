---
title: "Startup... need to add an extra step"
date: 2006-02-06
forum: Desktop Environments
---

### Post by dshreve71 on 2006-02-06
I would first like to apologize if this is the wrong forum to post this type of question. 

I beed working on a setting up pxe, tftpd, and samba. Those work fine, until PXE runs into an old network card that has intel's landesk service manager II v .99h on it. Then it hangs.

This may be corrected, with the command echo "1" > /procs/sys/net/ipv4/ip_no_ptmu_disc.

I want to add this into the startup of 'Breezy', how would I do this ?


Thanks,

dshreve71

---

### Post by encompass on 2006-02-06
ok... try this... this is a first for me... moded from a script I made ages ago...

> sudo nano /etc/init.d/intel_up #Name it waht you like

type the fallowing in it...
> 
#!/bin/sh
#Put the explanation of the cam here... so you don't forget!
echo "1" > /procs/sys/net/ipv4/ip_no_ptmu_disc

now... make sure it is the right kind of file (executible for everyone)

> sudo chmod 755 /etc/init.d/intel_up

Last... we create a link to the script to launch it at startup...

> sudo ln -s /etc/init.d/intel_ip /etc/rcS.d/S99intelup

reboot and tell me what happpens... I will do my best to help you from there.

---

### Post by dcstar on 2006-02-06
[QUOTE=dshreve71]
......
This may be corrected, with the command echo "1" > /procs/sys/net/ipv4/ip_no_ptmu_disc.

I want to add this into the startup of 'Breezy', how would I do this ?
......[/QUOTE]
Edit /etc/sysctl.conf, add in:

net.ipv4.ip_no_pmtu_disc = 1

Simple, innit?

---

### Post by dshreve71 on 2006-02-06
[QUOTE=dcstar]Edit /etc/sysctl.conf, add in:

net.ipv4.ip_no_pmtu_disc = 1

Simple, innit?[/QUOTE]

Thank you both for the responses. The response above lead me to the correct answer. Once, I opened the file, a saw a sample, so I ended up using this

net/ipv4/ip_no_pmtu_disc=1

Thanks again,

dshreve71

---

