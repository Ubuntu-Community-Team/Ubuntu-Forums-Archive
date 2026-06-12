---
title: "Wolfenstein ET 32bits on Ubuntu Dapper 64bits, how?"
date: 2006-08-05
forum: Gaming &amp; Leisure
---

### Post by Theimon on 2006-08-05
After searching for ages :/ here, google, linux-forums you name it, I can't find a solution for this.

Wolfenstein Enemy Territory is a 32bits application and from what I understand Ubuntu 6.06 64bits is backwards compatible with 32bits (though limited). 
I followed the normal procedure for installing W:ET. Downloaded the file, extracted the tar (so you get the install script), made it executable (chmod a+x), but when I run it as root I get this error:
```

theimon@CP353526-a:~$ cd /home/theimon/Desktop/
theimon@CP353526-a:~/Desktop$ sudo ./et-linux-2.55.x86.run
Password:
Verifying archive integrity... All good.
Uncompressing Enemy Territory 2.55...........................................................................................................................................................................................................................................................................................................
This installation doesn't support glibc-2.0 on Linux / unknown
(tried to run setup)
See http://zerowing.idsoftware.com/linux/ for troubleshooting
The setup program seems to have failed on unknown/glibc-2.0

See http://zerowing.idsoftware.com/linux/ for troubleshooting
```

Now, the link given is worthless. It gives just one suggestion which doesn't work ($ sh linux32 et-linux...etc.etc.)
So my question for you guys is: How can I get it to run? I'm all out of ideas and since I'm very new to Ubuntu (and Linux in general) I can't think of any new ideas either :/

Some system specs:
AMD Athlon64 3000+ @ 1,8GHz
2x512MB RAM (Dual Channel)
Maxtor Diamond Max 10 250GB SATA
nVidia 6600 128MB

Any help would be appreciated, thx in advance.

---

### Post by pharcyde on 2006-08-06
try this
```
apt-get install linux32
linux32 sh et-linux-2.55.x86.run
```

---

### Post by Theimon on 2006-08-07
This did the trick :) Thank you so much!

---

### Post by stlegend9 on 2007-10-11
I have wolfenstein et as a ".run" and have the same problem. Where would i put this code you have suggested?

---

### Post by stlegend9 on 2007-10-11
i opened up the terminal and put ur code but i get

```
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package linux32

```

---

### Post by csurigao on 2007-12-17
Try this:

sudo apt-get install linux32

Hope that helps!!!!!

---

