---
title: "Which repository a package comes from?"
date: 2009-06-09
forum: General Help
---

### Post by michy99 on 2009-06-09
Is there any way in Synaptic Package Manager to see which repository a package comes from? Is there a way to find out the same thing with apt-get?

---

### Post by Hund on 2009-06-09
Rightclick on the package in Synaptic and choose properties. There you have "Maintainer".

I use aptitude instead of apt-get:

> aptitude show <package>

---

### Post by michy99 on 2009-06-09
Thanks for the answer, but that doesn't really tell me which repository it comes from.

---

### Post by TrakerJon on 2009-06-09
System > Administration > Software Sources > Ubuntu Software ...look at Download from: [http://xxxx/xxxxx/archive](http://xxxx/xxxxx/archive) will show where you pull updates from but you probably know that...apt-cache showpkg XXX will give basic info and where it came from.

---

### Post by michy99 on 2009-06-09
Here is what I'm trying to figure out...Say I have a certain package listed in Synaptic. I suggest to someone that this package might be what they are looking for. They tell me it is not listed in Synaptic on their system. Obviously, it is listed in some repository which I have in my sources list but they do not. Is there any quick way for me to figure out which repository that is?

---

### Post by oldos2er on 2009-06-09
apt-cache show [package name]

 In Synaptic, go to Settings, Preferences, and under Appearance make sure the box is ticked. Then under Columns and Fonts, make sure Section and Component are ticked.

---

### Post by TrakerJon on 2009-06-09
Well for example:

From a terminal window **apt-cache showpkg sun-java6-jre** gives you...

Package: sun-java6-jre
Versions: 
6-13-1 (/var/lib/apt/lists/mirror.cc.columbia.edu_pub_linux_ubuntu_archive_dists_jaunty_multiverse_binary-i386_Packages) 

I'm not sure but an educated guess is that it came from [http://mirror.cc.columbia.edu/pub/linux/ubuntu/](http://mirror.cc.columbia.edu/pub/linux/ubuntu/)...

---

### Post by michy99 on 2009-06-09
> **oldos2er said:**
> apt-cache show [package name]

 In Synaptic, go to Settings, Preferences, and under Appearance make sure the box is ticked. Then under Columns and Fonts, make sure Section and Component are ticked.

This still doesn't do it. For example, for the package tor, Section is comm and Component is main. Neither one tells me it comes from [http://mirror.noreply.org/pub/tor](http://mirror.noreply.org/pub/tor) (in this case I happen to know the answer already.)

EDIT: Somehow I missed the first line about apt-cache show (although I think it is actually apt-cache showpkg.

---

### Post by michy99 on 2009-06-09
> **TrakerJon said:**
> Well for example:

From a terminal window **apt-cache showpkg sun-java6-jre** gives you...

Package: sun-java6-jre
Versions: 
6-13-1 (/var/lib/apt/lists/mirror.cc.columbia.edu_pub_linux_ubuntu_archive_dists_jaunty_multiverse_binary-i386_Packages) 

I'm not sure but an educated guess is that it came from [http://mirror.cc.columbia.edu/pub/linux/ubuntu/](http://mirror.cc.columbia.edu/pub/linux/ubuntu/)...

Thanks, this pretty much gets me the answer I need. Seems like there should be an easy way to do it in Synaptic, but any method is better than none.

---

### Post by oldos2er on 2009-06-09
**apt-cache showpkg** and **apt-cache show** are similar, but not exactly the same.

---

