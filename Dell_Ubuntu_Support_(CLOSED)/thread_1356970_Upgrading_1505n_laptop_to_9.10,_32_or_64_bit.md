---
title: "Upgrading 1505n laptop to 9.10, 32 or 64 bit?"
date: 2009-12-16
forum: Dell Ubuntu Support (CLOSED)
---

### Post by LinuxBob on 2009-12-16
HOw do I know whether to use the 32 or 64 bit?  I currently have Ubuntu 9.04 on the machine.


Also, thinking about installing on a Winbook (windows laptop), again 32 or 64 bit?  How do I figure it out in Windows XP?

---

### Post by Nostalos on 2009-12-16
> cat /proc/cpuinfo The do a google search to determine if its 64bit.   Or simply try booting a 64bit boot CD.

---

### Post by baddog144 on 2009-12-16
Can you tell us what CPU it is? If you're in windows, right click on My Computer and click "Properties"

---

### Post by LinuxBob on 2009-12-19
Thanks


It ia an INtel core duo T7200 - 64 bit.


I have 32 bit Ubuntu 9.04, can I chnage it to 64 bit without a completely new install?

As I  installed the Dell ISO for 9.04 should I assume it already is 64 bit, and any subsequent upgrade to Karmic will be 64 bit also?

---

### Post by Nostalos on 2009-12-19
unfortunatly no. to go from 32bit to 64bit requires a fresh install.   

to see if you are running 32 or 64 execute "uname -a" from a terminal window.   32bit will output somthing like "i686 GNU/Linux"  or some iteration there of.  i.e. i386 i486 i586 etc.   64bit will ouput "x86_64 GNU/Linux"


Also don't assume your dell ISO is already 64bit.  And yes,  any subsequent upgrades to a 64bit system will be 64bit.

---

### Post by baddog144 on 2009-12-19
Well all Core 2 Duos are 64-bit as far as I know, so you can run 64-bit Linux (or Windows). However, you will need to do a clean install if you're currently running 32-bit.

---

### Post by michael37 on 2009-12-20
I have a similar laptop, and I am running Ubuntu 9.10 64-bit.  It runs real well.   As mentioned previously, you need a fresh install if you have 32-bit Ubuntu installed.

---

