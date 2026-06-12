---
title: "Dell and Googleearth"
date: 2010-08-07
forum: Dell Ubuntu Support (CLOSED)
---

### Post by littleoak on 2010-08-07
I have a Dell Dimension 5150 running ubuntu 10.04 and so far all attempts to get Googleearth working have failed. has anyone got this problem or has found an answer ?.

---

### Post by ptn107 on 2010-08-07
Here's how I did it.

1) Download [_here_]("http://earth.google.com/intl/en/thanks.html#os=linux")

2) Install
```
cd /home/phil/Downloads/
chmod u+x GoogleEarthLinux.bin
./GoogleEarthLinux.bin
```

I installed to /home/phil/google-earth.  So all I have to do to run it is type:
```
/home/phil/google-earth/googleearth
```
or make a shortcut to run it.

---

### Post by jcolyn on 2010-08-07
Most versions of GoogleEarth don't work right but there is a better fix. Go to [http://packages.medibuntu.org/](http://packages.medibuntu.org/) and click on the Medibuntu link at the top. Next [Repository Howto]("http://help.ubuntu.com/community/Medibuntu") and follow the directions. Once done go to a terminal and enter sudo apt-get update. After this go to your Synaptics package manager and in the search box type googleearth. Mark it for install and then apply.

Be sure to remove any old versions first..

Medibuntu is a trusted site by the way....

---

### Post by littleoak on 2010-08-10
Thanks jcolyn **That solved the problem**.

---

### Post by jcolyn on 2010-08-10
> **littleoak said:**
> Thanks jcolyn **That solved the problem**.

Glad I could help..

---

