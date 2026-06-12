---
title: "Palm Centro reboots in Lucid"
date: 2010-05-08
forum: Desktop Environments
---

### Post by wazoo on 2010-05-08
This happened with 09.something and again with 10.04. When I plug in my Palm Centro smartphone, it starts endless rebooting. I solved it last time by removing modem-manager from /usr/bin.

But that program didn't reappear through my upgrade. 

Well, when I first upgraded, then plugged in my Palm through a USB cable, the phone rebooted. Then, I was able to sync to JPilot. Attempting the same thing later, the phone rebooted continuously.

Today, I seem to be able to sync again. But I'm wondering if anyone else is having similar issues.

---

### Post by houselfish on 2010-05-18
ditto but I am still using karmic koala 9.10
I just started looking at jpilot as an option for my centro.
before
sudo modprobe visor
there was no response
after
sudo modprobe visor 
the centro is continuously rebooting

I am looking into it...

Anthony

---

### Post by houselfish on 2010-05-18
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/470160](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/470160)

Lesson: do not use
sudo modprobe visor
since it is already blacklisted in /etc/modprobe.d/libpisock9.conf

make sure you
sudo rmmod visor
if you had done the modprobe

at least it has stopped rebooting
not lets try a sync....

Anthony

---

### Post by houselfish on 2010-05-18
working :guitar:

j-pilot 
*settings* usb: and 115200
*memos* use memos database (>5.2)
*addresses *use Contacts database (>5.2)

so far so good

Anthony

---

### Post by wazoo on 2010-05-22
Hmm. I issued rmmod visor, and got the message that I didn't have it in /proc/modules. But then I plugged in the Centro, and it seems to be working. Dunno if that's a solution or not. But thanks for the reply.

Note: I see that the successful sync happened while the phone connection was turned OFF. But even after turning it on, it seems OK.

---

### Post by SoFl W on 2010-05-22
This is un-related to your problem but when I tried to sync my centro (it has been a while) I lost a lot of phone numbers.  All the "first" phone numbers for each entry were there but any other number was lost.  I stopped using the ubuntu j-pilot sync.  One of the few applications I still use in Windows is the palm sync software.

---

