---
title: "Packet tracer 6.0.1 issues"
date: 2014-05-28
forum: Gaming &amp; Leisure
---

### Post by courtney2 on 2014-05-28
So I'm trying to get Packet Tracer 6.0.1 working for school. I'm running Ubuntu GNOME 14.04. I just had it running in LMDE, and it currently is working just fine on my laptop which is running Ubuntu GNOME 14.04. Not sure what the deal is for my desktop and why it won't work here. I downloaded the file from Netacad. It doesn't seem like it wants to even try to open it up. What I've tried so far:

dpkg -r PacketTracer (to remove)
Downloaded the file again from Netacad
Added .sh to the end and ran in an sh shell

---

### Post by courtney2 on 2014-11-30
I thought I'd contribute to this thread with my findings. Here is my successful method by installing ia32-libs-gtk:
```
sudo -i
cd /etc/apt/sources.list.d
echo "deb http://old-releases.ubuntu.com/ubuntu/ raring main restricted universe multiverse" > ia32-libs-raring.list
apt-get update
apt-get install ia32-libs-gtk
```
Then remove the ia32-libs-raring.list from the sources list and run "sudo apt-get update" immediately after"

Here is one that I have not tested, but might be worth trying first because the first method includes A LOT of dependancies that may/may not be needed

```
sudo apt-get install libgtk2.0-0:i386 libnss3-1d:i386 libnspr4-0d:i386 lib32nss-mdns libxml2:i386 libxslt1.1:i386
```

---

