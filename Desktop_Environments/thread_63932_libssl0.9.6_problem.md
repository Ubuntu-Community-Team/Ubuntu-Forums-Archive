---
title: "libssl0.9.6 problem"
date: 2005-09-09
forum: Desktop Environments
---

### Post by itechph on 2005-09-09
Hi guys,

    i'm installing yahoo messenger debian for my Ubuntu and i h ave a problem with libssl0.9.6 package.  This is the problem:

root@Gateway2:/home/gateway/Desktop # dpkg -i ymessenger_1.0.4_1_i386.deb
Selecting previously deselected package ymessenger.
(Reading database ... 58150 files and directories currently installed.)
Unpacking ymessenger (from ymessenger_1.0.4_1_i386.deb) ...
dpkg: dependency problems prevent configuration of ymessenger:
 ymessenger depends on libssl0.9.6; however:
  Package libssl0.9.6 is not installed.
dpkg: error processing ymessenger (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ymessenger


and when i tried to install libssl0.9.6... i got this problem:

root@Gateway2:/home/gateway/Desktop # apt-get -f install libssl0.9.6
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package libssl0.9.6
root@Gateway2:/home/gateway/Desktop # 

can someone help me with this....thank you very much

---

### Post by itechph on 2005-09-09
[QUOTE=itechph]Hi guys,

    i'm installing yahoo messenger debian for my Ubuntu and i h ave a problem with libssl0.9.6 package.  This is the problem:

root@Gateway2:/home/gateway/Desktop # dpkg -i ymessenger_1.0.4_1_i386.deb
Selecting previously deselected package ymessenger.
(Reading database ... 58150 files and directories currently installed.)
Unpacking ymessenger (from ymessenger_1.0.4_1_i386.deb) ...
dpkg: dependency problems prevent configuration of ymessenger:
 ymessenger depends on libssl0.9.6; however:
  Package libssl0.9.6 is not installed.
dpkg: error processing ymessenger (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ymessenger


and when i tried to install libssl0.9.6... i got this problem:

root@Gateway2:/home/gateway/Desktop # apt-get -f install libssl0.9.6
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package libssl0.9.6
root@Gateway2:/home/gateway/Desktop # 

can someone help me with this....thank you very much[/QUOTE]



right now...libssl0.9.6 i think the version currently installed to my computer.

---

### Post by Atreides2k on 2008-03-24
i have the exact same problem :| any ideeas?

---

### Post by lajevardi on 2008-05-08
[http://old-releases.ubuntu.com/ubuntu/pool/universe/o/openssl096/](http://old-releases.ubuntu.com/ubuntu/pool/universe/o/openssl096/) (Can't find the new one)
but I extremely! suggest you to use [Pidgin]("http://pidgin.im") and [Gyache]("http://www.phrozensmoke.com/projects/pyvoicechat/index_gyache.php") for voice and webcam support.

---

