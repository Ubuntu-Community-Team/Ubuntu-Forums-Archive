---
title: "scientific linux vs ubuntu"
date: 2010-08-06
forum: Education &amp; Science
---

### Post by mansourk on 2010-08-06
Hi ,
Has any one experienced working with "Scientific linux"? what's the difference between these two linux distributions and is "Scientific linux" really better than ubuntu for scientists and science students?

---

### Post by earlycj5 on 2010-08-06
> **mansourk said:**
> Hi ,
Has any one experienced working with "Scientific linux"? what's the difference between these two linux distributions and is "Scientific linux" really better than ubuntu for scientists and science students?

Better?  Depends, do you want to use RPMs or DEBs?

Which has the community support that you're comfortable with?

Ubuntu's community here is pretty robust (for what I do).  

Since they're free, I'd say try both and use what you're comfortable with and offers the best support for what you do. That's hard for me to make a rec since I don't really know what you do.  :)

---

### Post by endotherm on 2010-08-06
I've generally found that aside from live cds, the task-specific distro mixes don't really bring a whole lot of extra stuff to the table. just install what you need on whatever base distro makes the most sense for you.

---

### Post by mansourk on 2010-08-07
Thanks for your replies. here is some more information about me : i'm a physics student and do some c++/fortran programming , somtimes i also use  scientific packages and softwares. once a physicist  advised me to use redhat for scientific works because some scientific package are guaranteed to work out of box on redhat but not other linux distributions and as far as i know scientific linux is redhat based and completely redhat compatible. 
any replies and discussions is appreciated.

---

### Post by slaanco on 2010-08-08
Redhat (I think you meant Fedora) usually includes newer versions of libraries and packages, which is both good and bad. For example the version of glibc which is used by ubuntu 9.10 (I am not sure about 10.04) is significantly slower than the one in Fedora. However, i do not know if the scietific linux is kept in the sync with the newest fedora releases.

From my personal experience, I've tried Fedora (Redhat) but found the support from community unsatisfying. Having said that I would recommend trying out what you like more :)

---

### Post by snowpine on 2010-08-08
You can learn a lot by comparing these lists:

[http://distrowatch.com/table.php?distribution=scientific](http://distrowatch.com/table.php?distribution=scientific)
[http://distrowatch.com/table.php?distribution=ubuntu](http://distrowatch.com/table.php?distribution=ubuntu)

As you can see, Scientific Linux is based on Red Hat (RPM package management), which means it uses older (but very well tested) packages/applications. It's rock solid and each release is supported for years.

Ubuntu is based on Debian Unstable (DEB package management). It is a cutting-edge distro meant to showcase the latest in Gnome desktop Linux. It gives you the latest packages every 6 months and is generally considered to be more user friendly.

They are both excellent distros, there is no "vs" and neither is "better". They are at opposite extremes of the stability vs bleeding edge spectrum (by design), so if you have good self-assessment of your needs, the choice should be obvious.

---

### Post by ssam on 2010-08-08
just to clarify some above points. Redhat make 2 linux distributions. Fedora which is fairly similar to ubuntu, though has some newer packages, and is a little bit more experimental. and Enterprise Linux (RHEL), which is conservative in packages and features, but supported for 7 years.

RHEL costs money, but comes with good support, so businesses often like it. because its open source anyone can take the source, recompile it, and give it away for free (as long as they pull out all the trademarks). several groups do this, the main being CentOS and Scientific Linux.

SL also adds some packages that the folks at Fermilab and CERN like to have in their default install (eg openAFS). The latest SL release, is based on quite old packages. This means you may have trouble with new hardware, and may hit bugs that have been fixed in ubuntu.

i have no issue running my scientific apps on my SL5 workstation at uni, or my ubuntu desktop at home. on SL5 i need to add a newer version of python, scipy, and GCC/Gfortran (there are new enough versions in the ubuntu repos). i dont think SL would run on my laptop, but ubuntu works great on it.

---

