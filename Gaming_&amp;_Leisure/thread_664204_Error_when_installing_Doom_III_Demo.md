---
title: "Error when installing Doom III Demo"
date: 2008-01-10
forum: Gaming &amp; Leisure
---

### Post by tbuht_1 on 2008-01-10
I got the doom III demo for ubuntu 7.10 off of FileFront and during installation I get this error message:
```

Unable to find file:
'bin/Linux/x86/glibc-2.0/doom3-demo' in 

```

and the rest of the error message gets cut off for some reason.
Any help?
Thnx

---

### Post by Sockerdrickan on 2008-01-10
Maybe you have an incompatible version of glibc

---

### Post by tbuht_1 on 2008-01-11
Ah-ha...right you would be!
According to the readme:

```

Minimum requirements:
GNU/Linux system,
Pentium III, 1Ghz
256Mb RAM
Kernel 2.4, 2.6 is recommended
[COLOR="DarkOrange"]glibc 2.2.4 and up[/COLOR]


```

So could you please give me instructions on how to update this glibc file to at least the minimum?
Thnx for the reply!

---

### Post by Perfect Storm on 2008-01-11
Upgrade your Ubuntu to a newer version.

---

### Post by FriedChips on 2008-01-11
a newer version than gutsy?

EDIT:
Try here:
[http://packages.ubuntu.com/gutsy/libs/libstdc++2.10-glibc2.2](http://packages.ubuntu.com/gutsy/libs/libstdc++2.10-glibc2.2)

---

### Post by Perfect Storm on 2008-01-11
ah sorry, missed that part.

---

### Post by tbuht_1 on 2008-01-11
FriedChips, thanks for the reply.
I downloaded the package glibc 2.6.1, which is a tar file.
Could you give me specific info on how to install the file? (im a noob sorry)
Thanks

---

### Post by FriedChips on 2008-01-11
Please do not try and install glibc from that file, installing glibc from a package that is not made for gutsy could break things ( alot )... Are you running 64-bit by chance?

---

### Post by tbuht_1 on 2008-01-11
Yes, I'm running 64 bit, and im running into a lot of problems installing this tar file.
So what do you recommend downloading instead?

---

### Post by FriedChips on 2008-01-11
[http://ubuntu-utah.ubuntuforums.org/showthread.php?t=655055&page=2](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=655055&page=2)

check that thread out.. Looks like chrooting may be the key to success.. Or copying from a 32-bit install may help.... Honestly this stuff disgusts me, Ubuntu is a good distro but 64-bit is certainly it's weakest link. I think I am gonna switch back to Fedora 64-bit, it gave me much less problems. I am running into a similar problem with Ubuntu 64 myself, thats why I asked...

---

### Post by FriedChips on 2008-01-11
```
sudo linux32 bash ./doom3-demo-install-file.sh
```
give that a shot.

---

### Post by Cappy on 2008-01-11
> **FriedChips said:**
> [http://ubuntu-utah.ubuntuforums.org/showthread.php?t=655055&page=2](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=655055&page=2)

check that thread out.. Looks like chrooting may be the key to success.. Or copying from a 32-bit install may help.... Honestly this stuff disgusts me, Ubuntu is a good distro but 64-bit is certainly it's weakest link. I think I am gonna switch back to Fedora 64-bit, it gave me much less problems. I am running into a similar problem with Ubuntu 64 myself, thats why I asked...

Try what I mentioned here:
[http://ubuntu-utah.ubuntuforums.org/showpost.php?p=4049613&postcount=6](http://ubuntu-utah.ubuntuforums.org/showpost.php?p=4049613&postcount=6)
before you try a chroot.

---

### Post by tbuht_1 on 2008-01-11
aahh... shoot guys I gave u the wrong info!!! (forgive me)
i read 64-bit as amd-64 for some stupid reason.
but no i am running 32-bit (x86).
So please forgive me for being retarded and not being able to read...but can I get the instructions for 32-bit this time?

---

### Post by FriedChips on 2008-01-11
amd-64 is 64-bit....

---

### Post by tbuht_1 on 2008-01-11
yea it was a misread on my part. but no im running 32-bit.

well, now im kind of confused
intel core 2 duo is my processor which is 64 bit, but i also have 32-bit windows vista. So, Im thinking 32-bit...feel free to correct me if im wrong (im still new to this stuff lol)

---

### Post by Cappy on 2008-01-11
Try running
```
SETUP_LIBC=glibc-2.1
```
before you run the setup.

It is important that you run the installer in the same terminal window (don't open another terminal window to run the installer after you run that).

---

### Post by tbuht_1 on 2008-01-11
Okay I tried your command from the last post and then ran the setup from the other link you provided.  Here's what I got:

```

libc6 is already the newest version.
libc6-i386 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
aravind@aravind-laptop:~$ linux32 sh installer.run
sh: Can't open installer.run

```

---

### Post by Cappy on 2008-01-11
> **tbuht_1 said:**
> Okay I tried your command from the last post and then ran the setup from the other link you provided.  Here's what I got:

```

libc6 is already the newest version.
libc6-i386 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
aravind@aravind-laptop:~$ linux32 sh installer.run
sh: Can't open installer.run

```

That was for 64-bit ubuntu. Use the tip from my last post.

P.S. Use ```
./ filename_of_installer.run
```
to run the file. Obviously you should replace filename_of_installer.run with the actual filename.

---

### Post by FriedChips on 2008-01-11
can you post the output of
```
uname -a
```
that should tell us for sure if you are running 64-bit, but I'm pretty sure you are.

---

### Post by tbuht_1 on 2008-01-11
```

aravind@aravind-laptop:~$ uname -a
Linux aravind-laptop 2.6.22-14-generic #1 SMP Tue Dec 18 05:28:27 UTC 2007 x86_64 GNU/Linux

```
Sorry for confusing the crap out of all u guys. 

Okay, so Im guessing i have to try what u said earlier, which was the chrooting.  Im new to that also so I'm guessing I have to read thru that post.
And Cappy, I'll follow the instructions you gave me earlier for the 64-bit and let you know  how that goes.
Thanks

---

### Post by tbuht_1 on 2008-01-11
> **FriedChips said:**
> ```
sudo linux32 bash ./doom3-demo-install-file.sh
```
give that a shot.

Okay I tried that and then tried Cappy's earlier methods, but both still lead to the same message as earlier.

Can either of you explain in layman's terms what chrooting is and how I should go about it for this game? cause I got confused with that post.

---

### Post by Cappy on 2008-01-11
I posted a solution here:
[http://ubuntuforums.org/showpost.php?p=4117597&postcount=18](http://ubuntuforums.org/showpost.php?p=4117597&postcount=18)

but you might not be able to follow it (or adapt it if it is a little different)

---

### Post by Cappy on 2008-01-11
I just downloaded this one:
[http://www.gamershell.com/download_7202.shtml](http://www.gamershell.com/download_7202.shtml)

and it works perfectly when I run
```
chmod +x doom3-linux-1.1.1282-demo.x86.run
./doom3-linux-1.1.1282-demo.x86.run
```

Do you have a different version?

You must because I looked in the source of the doom3 I downloaded and it pretty much completely bypasses the glibc check that is causing you the problem

---

### Post by tbuht_1 on 2008-01-11
Sorry mate, but I downloaded your version and I still get the same message. Here's the message again:

---

