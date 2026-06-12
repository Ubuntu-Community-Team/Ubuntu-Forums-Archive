---
title: "Old versions of Skype for Linux ? Which versions do you still have on your disks?"
date: 2008-12-29
forum: General Help
---

### Post by frenchn00b on 2008-12-29
Hello,

Unfortunately, there is only apps for windows:
[http://www.oldapps.com/skype.htm](http://www.oldapps.com/skype.htm)
 
Which versions of skype do you still have ? tar.gz or debs (distro)?
Thanks !

---

### Post by braddcadd on 2008-12-29
I am running Skype 2.0.0.72, in Ubuntu 8.10.  I think I installed with deb downloaded from the skype website, but I can't remember.  Good luck.

---

### Post by frenchn00b on 2008-12-30
For who wants, I have :
skype_debian-1.3.0.53-1_i386.deb
and the skype-2.0.0.72.tar.bz2 (available on skype website)

---

### Post by i_baked_cookies on 2010-02-10
Hey everyone, I need Skype 2.0.0.72!

I can't find this anywhere online, Skype's taken it off their site, and I've googled my heart out trying to find this somewhere.  If anyone has it, please send it to [email]superdoopersauce@gmail.com[/email]

Thanks!

---

### Post by olalaaa on 2010-03-08
[COLOR=Red]I think I have the best of old versions and I will put it for everybody [here]("http://skype-old-version.blogspot.com/2010/03/skype-old-version.html") .

I also googled a lot for this old Skype .deb version ( in my computer it works like a charm, in Ubuntu 8.04 ) therefore I wanted to be sure that it is old enough ( immediately after Ubuntu hardy being released or alike ) , so that I could easily upgrade it if needed thereafter.

I re-installed the Ubuntu 8.04..**4** (last version of Hardy) then I googled the name of the package 2.0.0.68 so I found it in an alternate repository ;)[/COLOR]

Please install Medibuntu's repository to Ubuntu (if you didn't do it already) so that the link will work for you instantly :

For that, just open a Terminal and write the following (copy-paste from here) :

```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```( I copied that code above from this page here 
[https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories](https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories) so anyone can follow it safely if he wants it. )

---

### Post by gordintoronto on 2010-03-08
> **i_baked_cookies said:**
> Hey everyone, I need Skype 2.0.0.72!


Why?  I am using 2.1.0.47, and it works very nicely. It came from the Medibuntu repository via Synaptic.

---

### Post by olalaaa on 2010-03-09
Yes, but for those that didn't like Ubuntu's last distros (for various reasons) and wanted to step back to LTS version ( Ubuntu 8.04 ), it is IMPOSSIBLE to find other version that actually work on their computers. Skype website offers no longer packages for 8.04 versions - and this is bad from their part.

I performed a clean install of my Ubuntu Hardy in my computer (as most of people do sometimes) just to find myself without any option of installing Skype again.

Therefore I searched until I found in an old mexican repository ( :p kudos to them ) and I downloaded the Skype package before it left ;) .

If you like, after downloading the Skype old version, you can upgrade it (however I doubt you can do it - because they no longer support us - even if Hardy is L-T-S !!! )

---

