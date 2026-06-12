---
title: "Synaptic manager + Update manager not working"
date: 2009-04-11
forum: General Help
---

### Post by demoflare on 2009-04-11
uhh, where do i start.

(EDIT: im using ubuntu 8.10 intrepid)

First off as always, i noticed the update manager telling me about the latest updates. I proceeded to "attempt" to download them for install. But it tells me something is wrong...

Heres the error log.

```
W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.27-11-generic_2.6.27-11.31_i386.deb
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/t/tzdata/tzdata_2009d-0ubuntu0.8.10_all.deb
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/k/krb5/libkrb53_1.6.dfsg.4~beta1-3ubuntu0.1_i386.deb
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/c/clamav/libclamav5_0.94.dfsg.2-1ubuntu0.2_i386.deb
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/c/clamav/clamav-base_0.94.dfsg.2-1ubuntu0.2_all.deb
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/c/clamav/clamav-freshclam_0.94.dfsg.2-1ubuntu0.2_i386.deb
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/c/clamav/clamav_0.94.dfsg.2-1ubuntu0.2_i386.deb
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/c/cups/libcups2_1.3.9-2ubuntu9_i386.deb
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/c/cups/libcupsimage2_1.3.9-2ubuntu9_i386.deb
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/c/cups/cups-common_1.3.9-2ubuntu9_all.deb
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/c/cups/cups_1.3.9-2ubuntu9_i386.deb
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/c/cups/cups-bsd_1.3.9-2ubuntu9_i386.deb
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/c/cups/cups-client_1.3.9-2ubuntu9_i386.deb
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/d/doc-base/doc-base_0.8.16ubuntu1_all.deb
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/p/postgresql-8.3/libpq5_8.3.7-0ubuntu8.10.1_i386.deb
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.27-11_2.6.27-11.31_all.deb
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.27-11-generic_2.6.27-11.31_i386.deb
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-libc-dev_2.6.27-11.31_i386.deb
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/n/nvidia-graphics-drivers-180/nvidia-180-modaliases_180.11-0ubuntu1~intrepid1_i386.deb
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/n/nvidia-common/nvidia-common_0.2.4.1_i386.deb
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)



```

This has never happened before, and as you can see... my internet connection is fine. So then i browse some applications on the synaptic package manager. Only to find a very similar error.

```
W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/x/xaw3d/xaw3dg_1.5+E-15_i386.deb
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/universe/3/3dchess/3dchess_0.8.1-15_i386.deb
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)



```

This has never happened before now, i have looked at other threads on similar bugs. In which i changed the repository server, which still gave me the same errors. I have also tried, sudo apt-get clean, sudo apt-get update, sudo apt-get upgrade...

none seem to be working.

Whats is wrong? is this server side related?

I need to know quickly, (i cannot bear the thought of using M$ vista ram eater)

If anyone can find whats causing this, offer sugestions, anything really to get this working. Thanks in advance, ricky.

---

### Post by demoflare on 2009-04-11
Please, any help appreciated greatly. i cannot continue to work without the software i need 

o.O

---

### Post by demoflare on 2009-04-11
ok, i read theres a possibility of re-installing ubuntu to fix this.
im going to boot from the live-cd, resize the partition and then format the ubuntu part. will post after reinstall if it works, that way anyone else with the same problem could find this handy :o

---

### Post by DJonsson2008 on 2009-04-11
you don't have to reinstall for this, i think 
why don't you try some basic maintenance first

either open a root terminal or use sudo 

sudo apt-get update
sudo apt-get autoclean
sudo apt-get clean
sudo apt-get autoremove
sudo apt-get install gtkorphan
gtkorphan

now the above should go a long ways to sorting
out synaptic 
next run 

sudo synaptic 

from a command line and see if you make any progress.

---

### Post by woodenbrick on 2009-04-11
it looks something similar to this:
[http://forums.debian.net/viewtopic.php?t=310&sid=5d45c57b4d2c5c853afa01a0a4187893]("http://forums.debian.net/viewtopic.php?t=310&sid=5d45c57b4d2c5c853afa01a0a4187893")

---

### Post by demoflare on 2009-04-11
hmm, i don't really know what caused it... whether i went out, and my younger brother fiddled with settings, who knows.

but i literally tried everything :x even the 'sudo apt-get ___' thanks for your help anyway.

and yeah re-installing seems to have worked... 287 updates available lol. whatever the problem is, its not server end :s

---

