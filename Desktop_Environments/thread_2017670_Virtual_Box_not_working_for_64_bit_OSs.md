---
title: "Virtual Box not working for 64 bit OSs"
date: 2012-07-05
forum: Desktop Environments
---

### Post by johnsd on 2012-07-05
Hi

I am needing to run 64 bit virtual machines and am having no luck.

My details are:

Motherboard = D946GZIS
CPU = Intel E5400@2.7GHz x2
OS = Ubuntu 12.04 64 bit.
Virtual Box version = 4.1.12-Ubuntu r77245

The message says that VT-x is not enabled. The acceleration TAB under system is greyed out.

I have:
[LIST=1]
[*]Turned on virtualization in the BIOS.
[*]Upgraded to the latest Ubuntu version of Virtual Box.
[*]Upgraded the BIOS to the latest version. [http://downloadcenter.intel.com/Deta...=2482&lang=eng]("http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=14847&ProdId=2482&lang=eng")
[/LIST]
I really need to get this working so I don't have to go back to work in the evenings!

Any ideas appreciated.

Thanks
John

---

### Post by msammels on 2012-07-05
Might I ask, how did you install VBox? From the website, software center, or from apt-get? Also, is your Java up to date?

---

### Post by timhalo on 2012-07-05
> **johnsd said:**
> 
I am needing to run 64 bit virtual machines and am having no luck.


Shot in the dark here....

I had this problem and tracked it down to also having qemu installed. I could run 32 bit os but not 64 bit. So I unload kvm_amd module whenever I need to run a 64bit o/s on VirtualBox.

---

### Post by QIII on 2012-07-05
It appears that some of those processors, despite being dual core, may not have VT-x capability.

Do you have any further information on date of manufacture, lot number, etc?

Looks like the top markings should include "SLGTK"

---

### Post by 3Miro on 2012-07-05
Question is: does your CPU support 64-bit virtualization or not? Intel seems to have different versions of this CPU. Try the command here:

```
egrep '(vmx|svm)' /proc/cpuinfo
``` 

From this page:
[http://www.howtogeek.com/howto/linux/linux-tip-how-to-tell-if-your-processor-supports-vt/](http://www.howtogeek.com/howto/linux/linux-tip-how-to-tell-if-your-processor-supports-vt/)

---

### Post by johnsd on 2012-07-05
> **msammels said:**
> Might I ask, how did you install VBox? From the website, software center, or from apt-get? Also, is your Java up to date?
  Just the standard version from the repository - I did note that it updated recently.

---

### Post by johnsd on 2012-07-05
> **QIII said:**
> It appears that some of those processors, despite being dual core, may not have VT-x capability.

Do you have any further information on date of manufacture, lot number, etc?

Looks like the top markings should include "SLGTK"

I recently put in a dual core CPU - the box says S-Spec : SLGTK

---

### Post by johnsd on 2012-07-05
> **3Miro said:**
> Question is: does your CPU support 64-bit virtualization or not? Intel seems to have different versions of this CPU. Try the command here:

```
egrep '(vmx|svm)' /proc/cpuinfo
```From this page:
[http://www.howtogeek.com/howto/linux/linux-tip-how-to-tell-if-your-processor-supports-vt/](http://www.howtogeek.com/howto/linux/linux-tip-how-to-tell-if-your-processor-supports-vt/)


No response - so unfortunately looks like no support for 64 bit virtual machines (bother).

---

### Post by johnsd on 2012-07-05
> **timhalo said:**
> Shot in the dark here....

I had this problem and tracked it down to also having qemu installed. I could run 32 bit os but not 64 bit. So I unload kvm_amd module whenever I need to run a 64bit o/s on VirtualBox.

Not sure of the implications of what you are saying- will do some investigations.

---

### Post by johnsd on 2012-07-06
Doesn't look like that is the problem?

root@johnd-desktop:~# rmmod kvm-intel
ERROR: Module kvm_intel does not exist in /proc/modules
root@johnd-desktop:~# rmmod kvm-amd
ERROR: Module kvm_amd does not exist in /proc/modules

---

### Post by johnsd on 2012-07-06
Have pretty much decided that the problem is the Intel E5400@2.7GHz x2  CPU not being capable of 64 bit virtualization. Resigned to the fact I  will have to purchase a new MB/CPU/RAM combination.

Thanks for your responses.

---

### Post by 3Miro on 2012-07-06
> **johnsd said:**
> I recently put in a dual core CPU - the box says S-Spec : SLGTK

Interesting, according to Intel, your CPU should be able to run VT-x:

[http://ark.intel.com/products/40478/Intel-Pentium-Processor-E5400-(2M-Cache-2_70-GHz-800-MHz-FSB)#ordering](http://ark.intel.com/products/40478/Intel-Pentium-Processor-E5400-(2M-Cache-2_70-GHz-800-MHz-FSB)#ordering)

Is it possible that the Motherboard is acting up.

---

### Post by johnsd on 2012-07-06
> **3Miro said:**
> Interesting, according to Intel, your CPU should be able to run VT-x:

[http://ark.intel.com/products/40478/Intel-Pentium-Processor-E5400-(2M-Cache-2_70-GHz-800-MHz-FSB)#ordering]("http://ark.intel.com/products/40478/Intel-Pentium-Processor-E5400-%282M-Cache-2_70-GHz-800-MHz-FSB%29#ordering")

Is it possible that the Motherboard is acting up.

May be true - but I have flashed the BIOS to the latest version so not much more I can do?

---

### Post by johnsd on 2012-07-09
MB/CPU and RAM replaced with an AMD system and all works. One would have thought that 64 bit virtualization would work on a dual core 64 bit Intel CPU.

---

