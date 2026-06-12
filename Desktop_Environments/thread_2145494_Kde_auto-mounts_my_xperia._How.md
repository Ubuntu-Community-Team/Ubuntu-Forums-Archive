---
title: "Kde auto-mounts my xperia. How?"
date: 2013-05-15
forum: Desktop Environments
---

### Post by editheraven on 2013-05-15
Hi. In fact, it's like this : I installed opensuse>kde[dolphin] and my xperia is auto-mounted and the transfer rates are really good, compared with my method used in ubuntu>unity[nautilus] (sudo mtpfs -o allow_other /media/xperia). How can I implement the same thing in ubuntu>unity? It's a deamon, a dolphin feature, some rpm-only compiled driver or what?

---

### Post by editheraven on 2013-05-17
Ok. I added this ppa
```
deb http://ppa.launchpad.net/philschmidt/ppa-kio-mtp-daily/ubuntu precise main
```
then ```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 96462C94EA6C03FA
```
and then I installed kio-mtp (in kde plasma workspace, not unity). And I can mount android devices in ubuntu with great transfer rates. 

update : android is auto mounted in unity too, but only dolphin can open it ( dolphin "mtp:/device_name/" )

I have now another question : how do I unmount it? Or : what mountpoint is used for my android device by kio-mtp?

---

