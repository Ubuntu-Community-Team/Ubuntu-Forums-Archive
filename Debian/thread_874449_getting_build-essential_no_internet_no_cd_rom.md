---
title: "getting build-essential no internet no cd rom"
date: 2008-07-29
forum: Debian
---

### Post by redw0lf on 2008-07-29
I am trying to get the build-essential package so i can install wireless/wired internet.
This is on an eeepc and i only have access to a usb stick and other computers with internet
i have downloaded the following packages linked from [http://packages.ubuntu.com/hardy/i386/build-essential/download](http://packages.ubuntu.com/hardy/i386/build-essential/download) but have now hit a brick wall

g++-4.2 requires libstdc++6-4.2-dev but libstdc++6-4.2-dev requires g++-4.2

---

### Post by Sef on 2008-07-30
Moved to Debian Subforum.

---

### Post by benuski on 2008-07-30
Does the eee pc not have an ethernet port?  Because if it does, you should do everything you can to find an ethernet cable to borrow, even if that means just unplugging your wireless router for an hour or two or going someplace that has wired computers, unplugging those, and plugging the wire into your machine.  Your installation will be much easier, apt will remember what you installed and bring in all the dependencies automatically.

---

