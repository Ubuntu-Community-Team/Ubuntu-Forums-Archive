---
title: "VMWare server will not run after reboot"
date: 2006-08-14
forum: Desktop Environments
---

### Post by div3rg3nt on 2006-08-14
Dapper X86, IBM T43 (if that matters)
Installed VMWare Server, install seemed to go without a hitch. After install I am able to open the GUI console, create a new VM, etc. However, after a reboot when I launch VMWare server it appears to loading but then does nothing. If I run the config script again, I am able to run run the console again

Any ideas? 

 - Dave

---

### Post by lamego on 2006-08-14
Eventually you did a kernel update  before the reboot ?
On every kernel updated you will need to rebuild the vmware kernel modules...

---

### Post by PriceChild on 2006-08-14
> **lamego said:**
> On every kernel updated you will need to rebuild the vmware kernel modules...
by:
```
sudo vmware-config.pl
```

---

### Post by div3rg3nt on 2006-08-14
> **lamego said:**
> Eventually you did a kernel update  before the reboot ?
On every kernel updated you will need to rebuild the vmware kernel modules...
I have not installed a new kernel since I installed VMware Server.

---

### Post by jpeddicord on 2006-08-15
I am having this problem too. It has been bugging the crap out of me.

---

### Post by NetworkGuy on 2006-08-15
Did you happen to check the VMware forum for Server to see if this may be a known issue to them?

---

### Post by EmmEff on 2006-08-15
It sounds like the vmware service isn't being started at boot.

Try this from a shell prompt:

```
user@host:~$ sudo update-rc.d vmware defaults 90 08
```

In the meantime, do this:
```
user@host:~$ sudo /etc/init.d/vmware start
```

Does that work?

---

### Post by BLTicklemonster on 2006-11-26
I know this is late, but.... IF you can open the terminal, and type in sudo vmare to get it running, then the only fix I've found is this:

[http://www.ubuntuforums.org/showpost.php?p=1514238&postcount=10](http://www.ubuntuforums.org/showpost.php?p=1514238&postcount=10)

---

### Post by BiggoCharley on 2006-12-02
I have been having the same problem. I found this site through the VMware forum under the vmware server section.  I followed these instructions but it didn't solve my problem -maybe I don't know what I'm doing -- I would like to see comments by someone more proficient than i am (that's almost anyone).
 [http://jeremy.co-comp.co.uk/archives/6-VMware-need-to-re-run-vmware-config.pl-every-reboot-on-linux.html]("http://jeremy.co-comp.co.uk/archives/6-VMware-need-to-re-run-vmware-config.pl-every-reboot-on-linux.html")

---

### Post by Shay Stephens on 2006-12-04
I was having trouble too in edgy.  When I ran vmware from the terminal, I got this:

sudo vmware
vmware is installed, but it has not been (correctly) configured
for this system. To (re-)configure it, invoke the following command:
/usr/bin/vmware-config.pl.

So I ran the vmware-config command and it did some "stuff", but did not change the ability to run the program.  So I read the "stuff" and it mentioned needing xinetd installed.  So I installed it via synaptic, then reran: 
```
sudo vmware-config.pl
```

It now works :-)

---

