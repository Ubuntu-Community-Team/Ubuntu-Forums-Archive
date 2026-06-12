---
title: "[SOLVED] How do I install AirStrike?"
date: 2008-12-31
forum: Gaming &amp; Leisure
---

### Post by Jammanuser on 2008-12-31
Hi, I'm kind of new to Linux, and I wanted to install the game "Airstrike"...but I can't figure out how to install it! :confused: I tried the Add/Remove feature of Ubuntu 8.10, along with Synaptic, but I got an error message in Add/Remove saying the application conflicted with other installed software, and telling me to use Synaptic to resolve the conflict...which I did, but it says it depends on libsdl-image1.2 (>=1.2.5) but it is not installable. I tried installing that thing with "sudo apt-get install livbsd1-image1.2" but it didn't work as well! :confused: :confused: :confused: 

Can anyone tell me how exactly to install this game??? I'm very confused why it doesn't work...a detailed description on how to install it would be nice! :P

Thanks in advance! :popcorn:

-Jam man

:guitar:

P.S. this will be my first game I (want to) install on Ubuntu, just as a test...it would be nice if I could figure out how to install it!

---

### Post by tommcd on 2008-12-31
First run:
```
sudo apt-get update
```
Then post the output of:
```
sudo apt-get install airstrike
```
The output should give a reason why the game, or it's dependencies, can not be installed.

---

### Post by Jammanuser on 2008-12-31
> **tommcd said:**
> First run:
```
sudo apt-get update
```
Then post the output of:
```
sudo apt-get install airstrike
```
The output should give a reason why the game, or it's dependencies, can not be installed.

Ok, I ran sudo-apt get update, and then I did "sudo apt-get install airstrike", and here's the output for that:

```
~$ sudo apt-get install airstrike
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  airstrike: Depends: libsdl-image1.2 (>= 1.2.5) but it is not installable
E: Broken packages
```

Hope it helps someone figure out what the problem is...because like I said above, I can't figure out how to install "libsdl-image1.2" either, not with sudo apt-get install, nor with synaptic! ;)

Thanks for the reply! :)

-Jam man

:guitar:

---

### Post by tommcd on 2009-01-01
It seems you may have some broken dependencies somewhere. Post the output of:
```
sudo apt-get install  libsdl-image1.2
```
Also post the output of:
```
sudo aptitude why-not libsdl-image1.2
```
This should tell you why libsdl-image1.2 can't be installed.

Also, try opening synaptic, click the "reload" icon, then click "broken" in the left column. It should list any broken packages on your system. Then click edit > 'fix broken packages' from the menu. Then choose 'apply marked changes', then 'apply' and this should fix any broken packages. See the bottom of this page for more info:
[https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)

---

### Post by Jammanuser on 2009-01-01
Ok...here's the output as requested. 

sudo apt-get install libsdl-image1.2:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libsdl-image1.2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libsdl-image1.2 has no installation candidate

```

sudo aptitude why-not libsdl-image1.2:

```
Unable to find a reason to remove libsdl-image1.2.
```

Hope this helps you figure out what the problem is! :)

-Jam man

:guitar:

EDIT: I also looked in Synaptic, after clicking the Reload button...but couldn't find any thing called "Broken" in the left column! :confused:

EDIT #2: never mind...I found it under "Custom Filters", but there's nothing in it. Nothing shows when I select "Broken"! :-k

---

### Post by Jammanuser on 2009-01-01
I also just tried aptitude, instead of apt-get, but still didn't have success. :( Here's the output:

```
sudo aptitude install airstrike
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following packages are BROKEN:
  airstrike 
The following NEW packages will be installed:
  airstrike-common{a} 
The following packages will be REMOVED:
  linux-headers-2.6.27-7{u} linux-headers-2.6.27-7-generic{u} 
0 packages upgraded, 2 newly installed, 2 to remove and 0 not upgraded.
Need to get 1929kB of archives. After unpacking 49.3MB will be freed.
The following packages have unmet dependencies:
  airstrike: Depends: libsdl-image1.2 (>= 1.2.5) which is a virtual package.
The following actions will resolve these dependencies:

Keep the following packages at their current version:
airstrike [Not Installed]

Score is -9881

Accept this solution? [Y/n/q/?] n

*** No more solutions available ***

The following actions will resolve these dependencies:

Keep the following packages at their current version:
airstrike [Not Installed]

Score is -9881

Accept this solution? [Y/n/q/?] n

*** No more solutions available ***

The following actions will resolve these dependencies:

Keep the following packages at their current version:
airstrike [Not Installed]

Score is -9881

Accept this solution? [Y/n/q/?] y
The following packages will be REMOVED:
  linux-headers-2.6.27-7{u} linux-headers-2.6.27-7-generic{u} 
0 packages upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 52.0MB will be freed.
Do you want to continue? [Y/n/?] n
Abort.

```

I hope someone can figure out what the hell is going on! :( Its beginning to piss me off...

-Jam man

:guitar:

---

### Post by tommcd on 2009-01-02
I'm not sure why apt-get can't find libsdl-image1.2 for you. Are you running 32 bit or 64 bit Ubuntu? Run **uname -a** to find out if you are not sure. I'm not sure why aptitude wanted to remove the linux-headers packag either. Are you able to install other packages and get Ubuntu updates? The libsdl-image1.2 package is available for me:
```

tom@ubuntu:~$ apt-cache policy libsdl-image1.2
libsdl-image1.2:
  Installed: (none)
  Candidate: 1.2.6-3
  Version table:
     1.2.6-3 0
        500 http://us.archive.ubuntu.com intrepid/main Packages

tom@ubuntu:~$ aptitude show libsdl-image1.2
Package: libsdl-image1.2
State: not installed
Version: 1.2.6-3
Priority: optional
Section: libs

```

This guy had a similar problem and solved it by using aptitude to update his packages:
[http://ubuntuforums.org/showthread.php?t=473318](http://ubuntuforums.org/showthread.php?t=473318)
I'm not sure what he means by this statement though:
> i just try to update my package with sudo aptitude and use G for update
I don't know what he means by "use G for update".

I suppose you could try updating your package list with:
```
sudo aptitude update
```
and then try and install airstrike. I would use apt-get instead of aptitude to install though. It is generally not a good idea to mix apt-get and aptitude for installing packages, since they handle dependencies a bit differently, as you saw when aptitude wanted to remove the linux-headers package.

---

### Post by Jammanuser on 2009-01-02
> **tommcd said:**
> I'm not sure why apt-get can't find libsdl-image1.2 for you. Are you running 32 bit or 64 bit Ubuntu? 

I'm using 64-bit...:-k

---

### Post by Jammanuser on 2009-01-02
Never mind...i figured it out! :) Thanks for your help. It turns out that i didn't have the necessary repositories enabled in synaptic...once enabling, i was able to install airstrike, with synaptic, which of course also installed libsdl-image1.2 in the process! :D

Cheers! :popcorn:

-Jam man

:guitar:

---

