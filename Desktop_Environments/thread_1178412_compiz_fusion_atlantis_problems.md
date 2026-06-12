---
title: "compiz fusion atlantis problems"
date: 2009-06-04
forum: Desktop Environments
---

### Post by mr_gourami on 2009-06-04
so im getting rather annoyed. i spent the last hour and not found a hint that anyone else is haveing this problem. i have 9.04 installed. compiz fusion was defaulted in. however there is no button for atlantis. there is for gears but no atlantis. everything i read says this should have been automatically installed... i can find no extra plugins in the repositories, online or well anywhere. is it no longer an option for jaunty? compiz fusion verision is compiz 0.8.2 i google that and i find virtually nothing...

how do i get cube atlantis to work?

---

### Post by UbuntuNerd on 2009-06-04
click on the link it should install [http://mirrors.kernel.org/ubuntu/pool/universe/c/compiz-fusion-plugins-unsupported/compiz-fusion-plugins-unsupported_0.7.6-1_i386.deb](http://mirrors.kernel.org/ubuntu/pool/universe/c/compiz-fusion-plugins-unsupported/compiz-fusion-plugins-unsupported_0.7.6-1_i386.deb)

---

### Post by Steelclan on 2009-07-23
> **UbuntuNerd said:**
> click on the link it should install [http://mirrors.kernel.org/ubuntu/pool/universe/c/compiz-fusion-plugins-unsupported/compiz-fusion-plugins-unsupported_0.7.6-1_i386.deb](http://mirrors.kernel.org/ubuntu/pool/universe/c/compiz-fusion-plugins-unsupported/compiz-fusion-plugins-unsupported_0.7.6-1_i386.deb)

I tried using that but I got and error saying something about i386.

---

### Post by Vectorferret on 2009-08-20
> **Steelclan said:**
> I tried using that but I got and error saying something about i386.
That probably using the 64-bit version of Ubuntu. Either way, you can install Atlantis through apt (or Synaptic) on any architecture in Jaunty.

Either:
1. Open Terminal
2. Type "sudo apt-get install compiz-plugins-unsupported"

Or:
1. Open Synaptic (from System > Administration)
2. Search for compiz-plugins-unsupported
3. Install it

---

