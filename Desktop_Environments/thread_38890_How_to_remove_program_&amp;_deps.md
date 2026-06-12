---
title: "How to remove program &amp; deps?"
date: 2005-06-02
forum: Desktop Environments
---

### Post by SmokingGun on 2005-06-02
Hi,

was just wondering what the best way of removing a package & all it's dependies is?
For example, if i installed Beagle, it requires other packages, but then i want to remove Beagle, how do i find what other packages i installed along with it?

---

### Post by bored2k on 2005-06-02
You can go to synaptic, clic on properties (on top of beagle), and it will tell you its dependencies.  BTW beagle's are:

mono mono-jit mono-utils mono-mcs mono-assemblies-arch \
mono-assemblies-base mono-common libmono0 mono-devel
install libgconf-cil libgecko-cil libglade-cil libgmime-cil \
libgnome-cil libgsf-cil libgtk-cil libevolution-cil libgnomevfs2-dev \
libgnome2.0-cil libgnomeui-dev beagle

If you use aptitude remove nstead of apt-get, its supposed to do that. You could also try dselect or debfoster.

---

### Post by SmokingGun on 2005-06-02
Great. thanks

---

