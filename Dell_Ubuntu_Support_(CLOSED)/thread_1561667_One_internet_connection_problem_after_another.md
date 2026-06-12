---
title: "One internet connection problem after another"
date: 2010-08-26
forum: Dell Ubuntu Support (CLOSED)
---

### Post by itsmeboston on 2010-08-26
Hello,
First off let me state that i am completely new to all of this as of tonight, however i have spent the last 6 hours trying to learn as much as possible and have finally turned to the forum for help. My basic problem is that i have a dell inspiron 1440 laptop which is using a bcm4312 network adapter. As you may know this means that i have an issue to fix. Unfortunately i cant download via the )system/admin/hardware and drivers)method and get any updates because my eth0 connection also doesnt work. It simply tries to connect and then eventually it tells me that i am not connected to the internet. I then turned to windows to try and download the driver from broadcom website. From the Broadcom website i was able to download the tar but since i have no internet and no updates i found out that i have dont the right package installed to build the the module. I got an error that looked like this. 

make: *** /lib/modules/"release"/build: No such file or directory.

My question is were to now. Once again. I am new to all of this. I didnt even know what a terminal was until tonight but i have spent many hours reading and i am learning quickly. Any advice or help would be appreciated.

---

### Post by Baji P. on 2010-08-26
ItsMeBoston,

I understand your frustration, I've been through it many times for many years, but the AHA ! is worth it, when you get things working.

Here is my suggestion, I can't promise it will fix your issue, but it is worth a try.

Burn a Ubuntu [10.04.1 32-bit alternate CD]("http://ubuntu.mirrors.tds.net/pub/releases/10.04.1/ubuntu-10.04.1-alternate-i386.iso"), make sure that the laptop is physically connected to the network via the ethernet, boot from the CD.

After selecting the language, hit F6 and choose Expert install, and any other boot parameter necessary. Then slowly step through the installation.

When asked which network adapter to use, choose the wired one. Make sure you select every package repository that is offered for package source.

Good luck !

-baji.

---

