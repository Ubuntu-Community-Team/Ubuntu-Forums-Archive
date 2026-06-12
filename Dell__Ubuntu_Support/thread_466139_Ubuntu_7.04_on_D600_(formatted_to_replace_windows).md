---
title: "Ubuntu 7.04 on D600 (formatted to replace windows)"
date: 2007-06-06
forum: Dell  Ubuntu Support
---

### Post by scrupul0us on 2007-06-06
I got my hands on a D600 that came with XP... i formatted it (making sure I flashed to upgrade the bios to A16 first) and installed 7.04 from the server disc

the install goes flawless until it reboots... i get an error that seems to be popping up alot with this version:

Int 14: CR2 c10000000 err 00000002 EIP c03f3c3e CS 00000060 flags 0010006
Stack: 373c0046 00000000 ffffffff c0490000 00000080 00400000 ffffff80

has there bee n any kind of resolve for this as of yet

---

### Post by Sunflower1970 on 2007-06-06
I did a google search and found this page:

[http://www.virtualbox.org/ticket/289](http://www.virtualbox.org/ticket/289)

It was happening to people who were using virtual box, but maybe one of the suggestions may help you...

---

### Post by scrupul0us on 2007-06-06
yea ive tried to boot options but to no avail...

ive read that some suspect its a 686 kernal issue... but as we speak im staring at the desktop using Damn Small Linux as a liveCD and its runing the 686 kernal (2.4.26 to be exact)

im a bit perplexed here... Ubuntu has never given me any issues

---

### Post by Sunflower1970 on 2007-06-06
Have you tried, maybe Linux Mint? Or PCLinuxOS? Maybe Ubuntu Studio will work...or even Debian Etch? Did the live CD of Ubuntu work? (Yeah, a lot of questions, I know...)  Have you tried to install Ubuntu from the live CD instead of the server install...? 

Maybe it has to do with the upgrade of the BIOS...?

---

### Post by scrupul0us on 2007-06-06
i tried installing b4 the bios upgrade... then had to reinstall windows 2000 to use the bios installer... then tried installing again

the live CD on the server disc doesnt work... as someone had stated in another thread anything that requires running the kernal results in this failure

i havent tried any other ubuntu distro/cd's as of yet

im gunna try my 6.10 cd when i get home later

---

### Post by scrupul0us on 2007-06-06
im gunna go ahead and bump this... ive seen so many cases of this using google... and ive seen many report of the d600 running 7.04 just fine...

doing the boot switches doesnt work and ive upgraded my bios...

---

### Post by scrupul0us on 2007-06-06
update:

i just installed server 6.10 and when it boots after the install my screen gets flooded with:

"uknown interrupt or fault at EIP 00000060 c0100295 00000294"

it covers the screen and the system eventually just reboots and cycles this


WTF is going on?

---

### Post by Sunflower1970 on 2007-06-06
I think you already tried this with Feisty, but maybe it'll work with Edgy..?

[http://www.linuxquestions.org/questions/showthread.php?t=459446](http://www.linuxquestions.org/questions/showthread.php?t=459446)
[https://answers.launchpad.net/ubuntu/+question/4234](https://answers.launchpad.net/ubuntu/+question/4234)
[http://www.linuxforums.org/forum/debian-linux-help/45141-i-cant-get-debian-installed-booting-problems.html](http://www.linuxforums.org/forum/debian-linux-help/45141-i-cant-get-debian-installed-booting-problems.html)

Also:
[http://www.tonywhitmore.co.uk/cgi-local/wiki.pl?MeejaBox/TakeThree](http://www.tonywhitmore.co.uk/cgi-local/wiki.pl?MeejaBox/TakeThree)

[http://readlist.com/lists/vger.kernel.org/linux-kernel/51/259282.html](http://readlist.com/lists/vger.kernel.org/linux-kernel/51/259282.html)

Here's some more info on it:
[http://www.vmware.com/community/thread.jspa?messageID=592160](http://www.vmware.com/community/thread.jspa?messageID=592160)

hopefully something will work :(

---

### Post by scrupul0us on 2007-06-06
well the alternate CD worked for me... i installed it selecting the command line option... very strange tho... i wonder whats different

---

### Post by scrupul0us on 2007-06-07
strange thing with the alternate CD install.. when it boots... it kinda just chills at "Running Local Boot Scripts"

i have to press enter to be presented with the login prompt... never seen that before

---

### Post by bsmith1051 on 2007-06-26
> **scrupul0us said:**
> I got my hands on a D600 that came with XP
Did you buy a used laptop?  My office uses Dell laptops and in my experience more than half of them break inside of 3 years -- and the D600 would be about that old if not older.  The problem is simply that laptops get carried around a lot and they must develop cracks in the motherboard or something.  I've had lots of D600's get flaky and tried having the motherboards replaced under warranty.

---

