---
title: "[SOLVED] Fn+F2 WiFi HotKey Dosent Work"
date: 2008-08-10
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Danw12 on 2008-08-10
Hey Guys,
i have a dell inspiron 6000 laptop, with an intel PRO wireless onboard NIC. (if that is what you call it)  It is 802.11b & g at 54mb. Its working fine, and is connected right now, but the wifi light is never on, and the fn+f2 hotkey dosen't turn the wifi on or off, but on windows it does work and the light does too. 

im in no rush to fix this problem, and it works fine without, just wondered if there is any way around this?  :-k

Thanks Dudes!!! :)

---

### Post by Sand Lee on 2008-08-11
I've got the same(LED) problem with my Dell 1525. While testing Intrepid, which has a newer kernel than Hardy, I found that the light turns on. So, this is probably a kernel thing - it'll be fixed in 8.10.

---

### Post by superm1 on 2008-08-11
install linux-backports-modules-hardy to turn the light on.

---

### Post by x001 on 2008-08-11
I fixed the problem on my XPS1530 by using instructions on dell's site: [http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/WiFi_LED_does_not_work](http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/WiFi_LED_does_not_work)

It might point you in the right direction.

---

### Post by Danw12 on 2008-08-11
Thanks To All Of You For Your Contributions,
Due to all of your knowledge combined i have been able to fix this situation

(sorry about the posh language [im watching star trek] :))

tnx, 
Dan

---

### Post by Orphee on 2008-08-24
Hi, This Fix doesn't work for me, I have a Vista Dell 1525, I installed Ubuntu 8.04.1 LTS but the wifi led is always off... the wifi works well...
any idea ?

Thanks in advance :)

---

### Post by KiranOtter on 2008-08-24
I have a Dell Precision M70, and the Fn+F2 key has always worked, (it turns the radio on and off,) but the LED does not work.  I've tried the backports suggestion to no avail.

The module I loaded was linux-backports-modules-hardy, which included linux-backports-modules-hardy-generic, and linux-backports-modules-2.6.24.19-generic (which I tried first based on the wiki post.)

---

### Post by Danw12 on 2008-09-10
I Have Still Got An Ongoing Problem With The LED, But I Do Have Another Problem if you would care to take a [URL="http://ubuntuforums.org/showthread.php?t=905671"]look 

http://ubuntuforums.org/showthread.php?t=905671[/URL] 

PLEASE HELP>>>>^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

:confused:

---

