---
title: "Error messages"
date: 2006-02-19
forum: Desktop Environments
---

### Post by Ramses de Norre on 2006-02-19
My dmesg is full of this error message: ```
[4336864.777000] APIC error on CPU0: 40(40)

```Only the numbers between brackets are different in the messages.

What does it mean? My cpu is an AMD Athlon 64 and I'm running ubuntu-32bit.
Should I worry about it?

And another question: on boot he sais 'fail' on 'setting sensor limits' any idea what to do about that?

---

### Post by Ramses de Norre on 2006-02-26
Anyone who knows what this could be?

---

### Post by someusernoob on 2006-03-02
I have the same error in dapper 6.04 with a pentium 4 @ 2Ghz

---

### Post by mooswa on 2006-03-05
I "fixed" it by booting with noapic flag. I am not sure if I lost something by disabling APIC but one thing I seem to gain is better CPU frequency scalling. My Turion used to stuck at max 1.8 Ghz, now it correctly goes down  to 800Mhz when there is no load.

---

