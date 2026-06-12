---
title: "Xubuntu 12.04 LTS - Support for how long?"
date: 2012-05-14
forum: Desktop Environments
---

### Post by taylorkh on 2012-05-14
The xubuntu help and support page states > Below you’ll find a plethora of resources that will make getting help and resolving issues a snap. Getting help with Xubuntu is easy! The currently supported Xubuntu releases are:

    Precise Pangolin 12.04 LTS, until April 2015It is my understanding that starting with 12.04 the Ubuntu support duration is 5 years on both server and desktop. Is this not true of the Ubuntu variants? 

I am considering Xubuntu as an alternative to Unity but I would like to have a longer support timeline.  Can anyone clarify this for me?

TIA,

Ken

---

### Post by kc1di on 2012-05-14
As far as I understand all derivatives will be supported for 5 years. 

I have xubuntu on one of my machines

---

### Post by The Cog on 2012-05-14
Only 3 years for Xubuntu: [http://xubuntu.org/news/12-04-release/](http://xubuntu.org/news/12-04-release/)
Why they have chosed to ignore the Ubuntu LTS schedule is a mystery to me.

---

### Post by kc1di on 2012-05-14
> **The Cog said:**
> Only 3 years for Xubuntu: [http://xubuntu.org/news/12-04-release/](http://xubuntu.org/news/12-04-release/)
Why they have chosed to ignore the Ubuntu LTS schedule is a mystery to me.

Sorry to hear that. but it's still a good one

---

### Post by taylorkh on 2012-05-14
Well this sucks. I guess I will go with CentOS 6.2 after all. It is supported until 2020.

Ken

---

### Post by kc1di on 2012-05-15
Here's what it says on the xubuntu down load page:

```
The 12.04 release, codenamed Precise Pangolin, is a Long Term Support release, which means it has support for 3 years. To learn more about the release, please refer to the release announcement, which has links to complete release notes as well as highlights of the improvements in the release.
```

---

### Post by egeezer on 2012-05-15
Could be worse - Lubuntu is only supported for 18 months.  The variants apparently are at liberty to set their own support schedules, since they are not paid by Canonical.

---

### Post by j2snowden on 2012-12-12
14.04 LTS comes in April 2014 so you will have full year (12 months) to  upgrade from 12.04 LTS to 14.04 LTS. And you'll definitely wil want to  upgrade (new kernel,new faster intel drivers, working AMD 6 and 7 series  ;), new nvidia drivers, support for Nvidia Primus (better than  Bumblebee).



Some people still have problems with Thunar taking a long time to start  for the first time. This is due to gvfs checking the network, preventing  Thunar from starting until gvfs finishes its operations. To change this  behaviour, edit /usr/share/gvfs/mounts/network.mount and change **AutoMount=true** to **AutoMount=false**.

---

