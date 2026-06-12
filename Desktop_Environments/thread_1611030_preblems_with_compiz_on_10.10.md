---
title: "preblems with compiz on 10.10"
date: 2010-11-01
forum: Desktop Environments
---

### Post by rahilm on 2010-11-01
I did a clean install of ubuntu 10.10 on my inspiron 15r with ati graphics. Previously, it was running ubuntu 10.04 perfectly. But now, i cannot enable desktop effects. I did a google search and came across some bug reports, but none of the solutions seem to work.

i also downloaded compiz-check:
```

Gathering information about your system...

 Distribution:          Ubuntu 10.10
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc Manhattan [Mobility Radeon HD 5000 Series]
 Driver in use:         radeon
 Rendering method:      None

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: No rendering method in use (AIGLX, Xgl or Nvidia) 

rahil@rahil-laptop:~$ 
rahil@rahil-laptop:~$ lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc Manhattan [Mobility Radeon HD 5000 Series]

```

---

### Post by cromat on 2010-11-01
Which version of the ATI driver are you using?, the open-source one, the proprietary one "tested by ubuntu developers", or install the ATI one from their site?

---

### Post by cpmman on 2010-11-01
I had a compiz problem and followed this advice which corrected it:-

***_[http://ubuntuforums.org/showpost.php?p=9964610&postcount=2]("http://ubuntuforums.org/showpost.php?p=9964610&postcount=2")_***

---

### Post by rahilm on 2010-11-01
> **cromat said:**
> Which version of the ATI driver are you using?, the open-source one, the proprietary one "tested by ubuntu developers", or install the ATI one from their site?

The one which gets installed when u install from System->Administration->Additional Drivers..
(proprietery)

should i try the ones from the site?

---

### Post by rahilm on 2010-11-01
> **cpmman said:**
> I had a compiz problem and followed this advice which corrected it:-

***_[http://ubuntuforums.org/showpost.php?p=9964610&postcount=2](http://ubuntuforums.org/showpost.php?p=9964610&postcount=2)_***

doesn't work.. :(

---

### Post by rahilm on 2010-11-02
Falling back to lucid..

---

### Post by rahilm on 2010-11-02
are they gonna fix this problem.. or will i have to jump directly to narwhal??

---

### Post by rahilm on 2010-11-02
any way i can get the meerkat sound menu in lucid??

---

### Post by rahilm on 2010-11-02
Solved it!!

---

### Post by ballisox on 2010-11-06
Please include the steps you followed to solve it.

---

