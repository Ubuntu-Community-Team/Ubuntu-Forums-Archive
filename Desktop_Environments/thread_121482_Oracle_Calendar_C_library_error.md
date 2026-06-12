---
title: "Oracle Calendar C library error"
date: 2006-01-25
forum: Desktop Environments
---

### Post by anthro398 on 2006-01-25
Has anyone been recently getting this error message: "Warning: locale not supported by C library, locale unchanged" with Oracle Calendar desktop client?  I'm using 9.0.4.  This has been a recent change, maybe after an apt-get dist-upgrade recently.  I've reinstalled a couple of times to no relief.  Other than that, does anyone know of a replacement client for ocal?  

Thanks

---

### Post by jonobr on 2007-02-09
Hey ,


I was out from work for the past two weeks,
When I came back my ubuntu desktop had updates it needed to install,
I installed them, went to run ocal and got exactly the error you describe.

So, no fix in this post, just the sharing your pain brother.............:roll:

---

### Post by wsgrah on 2007-02-27
I was running into this with the new installation. Turns out there's a bug with the libc6. Anyway, the work-around is pretty simple...

You'll need to edit the cal_linux file in the installer to edit out the call to LD_ASSUME_KERNEL

Assuming you're in the install directory...

```

cp cal_linux cal_linux.bak

cat cal_linux.bak | sed "s/export LD_ASSUME_KERNEL/#xport LD_ASSUME_KERNEL/" > cal_linux

```

Then just run the gui/text/silent installer.

---

### Post by mollison on 2007-09-27
wsgrah's fix did not solve the problem to me. The problem is occurring at runtime, not at installation, and causes Oracle Calendar to terminate when it connects to the remote server (or sometime thereabouts).

I actually can only install OC with that fix, but doing so does not prevent the locale error from occurring.

Anyone know how to fix this? I'd love to be able to log into my calendar again.

---

### Post by mollison on 2007-09-28
OK, after struggling for a long time I finally managed to fix the problem. 

For posterity, I deleted the .OracleCalendar folder in /home/user/. Then when I started Oracle again, it (presumably) created a new one (I had to type in all my setting again), and started working fine again.

My earlier attempts to solve the problem by reinstalling Oracle didn't solve the problem because they left the same .OracleCalendar folder in tact.

No idea why something in the profile settings would cause such an error, or why it would just spontaneously come up... if anyone has any ideas, I've be interested in hearing them.

---

### Post by jonobr on 2007-10-09
Hey Mollison,

Confirming your fix, that worked for me too... GREAT JOB!!

Thanks for the post

---

### Post by Malkin on 2007-10-18
Thank you, mollison!  Your fix worked for me too!

I wasn't getting any error message, but as soon I as would try to login, it would just disappear and my calendar wouldn't ever come up.  I tried reinstalling several times, but deleting .OracleCalendar was what did the trick in the end.  Thanks!

---

### Post by mollison on 2008-01-10
I've discovered that if you save the 'profile' file in .OracleCalendar, you can avoid tying in your server and user information again.

---

### Post by mollison on 2008-01-24
In addition to the two problems above, I started getting a message saying I was missing libstdc++.so.5, and preventing Oracle from starting. 

I think aptitude removed that library when I was doing a recent install of something else.

Here are instructions to fix this problem - borrowed from [here]("http://www.debugmode.com/userforums/viewtopic.php?t=6125").

# change directory to /tmp directory:
cd /tmp/

# download deb package:
wget -c [http://lug.mtu.edu/ubuntu/pool/main/g/gcc-3.3/libstdc++5_3.3.6-13ubuntu2_i386.deb](http://lug.mtu.edu/ubuntu/pool/main/g/gcc-3.3/libstdc++5_3.3.6-13ubuntu2_i386.deb)

# unpack deb package to get library file
dpkg -x libstdc++5_3.3.6-13ubuntu2_i386.deb libstdc++5

# copy library file to /usr/bin directory
sudo cp libstdc++5/usr/lib/libstdc++.so.5.0.7 /usr/lib

# change directory to /usr/lib directory
cd /usr/lib

# create simbolic link to library
sudo ln -s libstdc++.so.5.0.7 libstdc++.so.5

---

