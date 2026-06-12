---
title: "g++ is Installed but I am not able to compile"
date: 2009-01-20
forum: General Help
---

### Post by UNME on 2009-01-20
Hi All,

I am using ubunto linux on my machine ...
I recently installed g++ (As I have used wubi to installed ubuntu by default g++ was not there but gcc was there).

When I run command

$# g++ filename.cpp I get the error:

The program 'g++' can be found in the following packages:
 * g++
 * pentium-builder

Try: sudo apt-get install <selected package>
bash: g++: command not found

I am having admin login also.

Also how can I know things are set properly or not?

I installed following packages:

cpp-4.3_4.3.2-1ubuntu11_i386.deb
g++-4.3_4.3.2-1ubuntu11_i386.deb
gcc-4.3_4.3.2-1ubuntu11_i386.deb
gcc-4.3-base_4.3.2-1ubuntu11_i386.deb
libc6_2.8~20080505-0ubuntu7_i386.deb
libgcc1_4.3.2-1ubuntu11_i386.deb
libgmp3c2_4.2.2+dfsg-3ubuntu1_i386.deb
libgomp1_4.3.2-1ubuntu11_i386.deb
libgomp1_4.3.2-1ubuntu11_i386.deb
libstdc++6-4.3-dev_4.3.2-1ubuntu11_i386.deb
libstdc++6_4.3.2-1ubuntu11_i386.deb

thank you :KS

---

### Post by UNME on 2009-01-20
Also I am not having internet connected ... it is a test machine .. connected by lan to my rest windows machines

Also two packages where interdependent g++-4.3_4.3.2-1ubuntu11_i386.deb and libstdc++6-4.3-dev_4.3.2-1ubuntu11_i386.deb

so I installed them as follows:

dpkg -i g++-4.3_4.3.2-1ubuntu11_i386.deb libstdc++6-4.3-dev_4.3.2-1ubuntu11_i386.deb

I got following message:

tar: ./md5sums: time stamp 2008-10-24 22:15:04 is 50158923.593292163 s in the future
tar: ./control: time stamp 2008-10-24 22:15:04 is 50158923.592551106 s in the future
tar: .: time stamp 2008-10-24 22:15:04 is 50158923.592241299 s in the future
(Reading database ... 100615 files and directories currently installed.)
Preparing to replace g++-4.3 4.3.2-1ubuntu11 (using g++-4.3_4.3.2-1ubuntu11_i386.deb) ...
Unpacking replacement g++-4.3 ...
tar: ./md5sums: time stamp 2008-10-24 22:16:10 is 50158978.982345104 s in the future
tar: ./control: time stamp 2008-10-24 22:16:10 is 50158978.98125638 s in the future
tar: .: time stamp 2008-10-24 22:16:10 is 50158978.980717643 s in the future
Preparing to replace libstdc++6-4.3-dev 4.3.2-1ubuntu11 (using libstdc++6-4.3-dev_4.3.2-1ubuntu11_i386.deb) ...
Unpacking replacement libstdc++6-4.3-dev ...
Setting up g++-4.3 (4.3.2-1ubuntu11) ...
Processing triggers for man-db ...
Setting up libstdc++6-4.3-dev (4.3.2-1ubuntu11) ...

---

### Post by mrphd on 2009-01-20
Try doing:

```
sudo apt-get install build-essential
```

---

### Post by UNME on 2009-01-20
hi,

I got this:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package build-essential

I am using wubi I just installed ubuntu from ISO file (I downloaded it on server and copied it in client. Client is not having Internet)

thank you

---

### Post by UNME on 2009-01-20
I think few things get solved by making a closer look.

Folks I was using g++ but the latest command is g++-4.3, it works well.

Thanks

---

### Post by rodders on 2009-01-20
If g++-4.3 works then /usr/bin/g++ should be present. If it isn't you can, if you wish, add it with:

sudo ln -s /usr/bin/g++-4.3 g++

---

