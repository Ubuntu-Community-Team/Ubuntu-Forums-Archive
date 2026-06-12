---
title: "transcode install"
date: 2005-06-02
forum: Desktop Environments
---

### Post by BigShyBear on 2005-06-02
I am trying to install transcode on a new Kubuntu 5.04 installation on a computer with an AMD Athlon 2200+ processor and an MSI K7N2 Delta motherboard, with an ATI Radeon 7000 (RV100) video card. (I'm pretty sure on the AMD Athlon 2200+ part is important, but right now, I don't know for sure.)
I run 'sudo apt-get install transcode'
and I get back:
"The following packages have unmet dependencies:
  transcode: Depends: libavcodeccvs (>= 2:20041227-woody0.1) but it is not going to be installed
             Depends: libdvdread2 but it is not installable
             Depends: libvorbis0 (>= 1.0rc3-1) but it is not installable
             Depends: libxvidcore4 but it is not going to be installed
E: Broken packages"

I go through synaptic and try to install the listed library files, and none will install, all point back to libc6

"Depends: libc6 (>=2.3.2.ds1-21) but 2.3.2.ds1-20ubuntu13 is to be installed"
I look in synaptic and synaptic says that libc6-i686 2.3.2dsl-20ubuntu13 is installed.
Is there any updated libc6 anywhere?  Or any help on how I get around this?

Thanks ](*,)  ](*,)  ](*,)  ](*,)  ](*,)  ](*,)

---

### Post by Joey French on 2005-06-02
I have the same issue.

---

### Post by BigShyBear on 2005-06-02
Made the mistake of looking in the Kubuntu forums, Google, the unoffical Kubuntu FAQ at [http://kudos.berlios.de/kf/kf1.html#h2add](http://kudos.berlios.de/kf/kf1.html#h2add), and tried to install from source.

The trick is in the Ubuntu forums,  under DVDRIP
[http://ubuntuguide.org/#dvdrip](http://ubuntuguide.org/#dvdrip)
need to run apt-get in a slightly different mode:
sudo apt-get -t testing install transcode

---

