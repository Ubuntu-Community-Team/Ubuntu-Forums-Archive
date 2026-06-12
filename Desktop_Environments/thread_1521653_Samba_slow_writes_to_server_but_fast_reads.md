---
title: "Samba slow writes to server but fast reads"
date: 2010-07-01
forum: Desktop Environments
---

### Post by karit on 2010-07-01
I have a fileserver running 10.04 server 64bit and samba. I connect it to my desktop which is 10.04 desktop 64bit.

I have the server mounted on my desktop in fstab as:
//[10.0.0.2/share]("http://10.0.0.2/share")  /media/share cifs  guest,uid=1000  0  0

Up until 30 June 2010 it was all fine. 

Now when I write the server it is very slow e.g. 2Mbps though when I read I get >100Mbps so I think my network is still ok. 

If i use nautilus smb://[10.0.0.2/share]("http://10.0.0.2/share") I can write at >100Mbps and also read at >100Mbps

So any ideas why the write speed via the fstab mount samba has started to go really slowly in the last couple of days? Any help gratfully received.

---

### Post by clrg on 2010-07-01
What do you write on the server? If you write a billion 2KB files, it will be painfully slow. Check your speed with

```
sudo apt-get install pv && dd if=/dev/urandom of=~/random bs=1M count=2048 && pv ~/random >/PATH/TO/YOUR/SHARE
```pv will then show a progress bar and the speed of the transfer. Don't believe Nautilus, sometimes it gets transfer rates wrong.

(Explanation of the command: This installs pv which measures the amount of data going through a pipe, then creates a file in your home directory called "random" with the size of 2GB filled with random data, then copies the file to your share (adapt the path, please) while showing you speed & progress)

Greetings

---

### Post by karit on 2010-07-01
Large files >100MB and I have been watching atop and system monitor for speeds

Using nautlis to copy to fstab mounted share ~2Mbps
Using nautlis to copy to smb:// path ~20Mbps
Using pv random > /media/share/tmp/random ~20Mbps

Using nautilus to read from fstab mounted share ~110Mbps

Copying between 2 SATA drive in the server to the disk that has the file share looking at iotop >70 M/s

A 9.10 desktop just before I think was getting >100Mbps writes to the server. Can't double check that right now as machine is locked and person out

---

### Post by adderek on 2010-07-01
Some things that you might check:

smb-server# time dd if=/dev/zero of=/my/shared/mounted/filesystem/dummy bs=512 count=204800 # 100MiB=100*1024*2*512B=204800

smb-server# time dd if=/my/shared/mounted/filesystem/dummy of=/dev/null bs=512 count=204800 # 100MiB=100*1024*2*512B=204800

smb-client# time dd if=/dev/zero of=/mount/my/shared/mounted/filesystem/dummy bs=512 count=204800 # 100MiB=100*1024*2*512B=204800

smb-client# time dd if=/mount/my/shared/mounted/filesystem/dummy of=/dev/null bs=512 count=204800 # 100MiB=100*1024*2*512B=204800

If there is a significant difference between the two - I would check network transfer - it might be the bottleneck. Then you might go through the smb logs to verify what is going there.

Good luck

---

### Post by clrg on 2010-07-01
20MB/s is perfectly acceptable. I usually get 12MB/s when copying with SMB. (MBytes, not Mbits)

---

### Post by karit on 2010-07-03
> **clrg said:**
> 20MB/s is perfectly acceptable. I usually get 12MB/s when copying with SMB. (MBytes, not Mbits)

Yeah that was my up to earlier this week I was get >100Mbps on writes and now I only getting 2Mbps hence why I am wondering if anything has changed recently.

A 9.10 machine is still getting >120Mbps when it writes to the same file server

---

### Post by karit on 2010-07-04
I think this might be related to [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/571235](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/571235) AS I'm seeing a lot of SMB QUERY_PATH_INFO in wireshark like almost continually. Yet on the 9.10 machine that still has fast writes SMB QUERY_PATH_INFO does not show up in wireshark.

Anyone have any ideas on how to fix this?

---

