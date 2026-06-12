---
title: "Hash Sum Mismatch Update Errors"
date: 2008-12-02
forum: General Help
---

### Post by volaer on 2008-12-02
Guys, do you have any idea on how can i can rid with this Hash Sum Mismatch errors??? 

I am trying to upgrade to 8.10 intrepid from 8.04. But this errors are really nasty and keeps on popping up causing my upgrade to fail.
This is the error code that appears:

[B]Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/binary-i386/Packages.bz2)  Hash Sum mismatch
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/source/Sources.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/source/Sources.bz2)  Hash Sum mismatch
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-security/main/source/Sources.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-security/main/source/Sources.bz2)  Hash Sum mismatch
Some index files failed to download, they have been ignored, or old ones used instead.[/B]

Please help

---

### Post by LinkedITS on 2009-12-16
I had the same exact problem. I tried Ubuntu, Mint 7, Mint 8 and every single time I would get the Hash Sum Mismatch Error when I try to install anything. Because I spent so much time searching for the answer to my problem, I am going to try to post this anywhere I see someone having problems with Hash Sum Mismatch.

After seeing breaker's post (he mentions the problem might be with bad RAM), I realize it could be a problem with my RAM because I remember that my machine used to have Windows 7 OS on it and it failed to install anything because it kept getting corrupt files error. Originally I thought the problem was because my computer was unable to support Windows 7. But one of the symptoms of bad RAM is having corrupt files and bad disk. Another symptom is having distorted graphics on the web pages which i notice was another problem I had. 

My computer had ordered a couple of the same computer, so I did a test and installed Mint 8 on a computer of the same model. I was able to install everything I wanted on the new computer without any of the Hash Sum Mismatch errors.

So that led me to conclude that I kept getting the Hash Sum Mismatch errors because i had a bad RAM. (OR at the very least it is a hardware problem isolated to that specific computer). I am going to change the memory in my problematic computer and see if that fixes the problem. I'll post an update within the week with the results.

---

### Post by LinkedITS on 2009-12-16
As I mentioned in a earlier post, the Hash Sum Mismatch might be caused by bad RAM so i devised a experiment to test out my Hypothesis. In the "experiment" that I performed, I took the RAM out of the "Good Machine" and put it into the "Bad Machine." Then I booted into the "Bad Machine with the Good RAM" and tried to install the ntp package. However the installation failed with Hash Sum Mismatch once again. 

Then I put the "Bad RAM" into the "Good Machine" and booted into it. The "Good Machine with the Bad RAM" was able to install properly without any problems at all.

This leads me to the conclusion that the problem is NOT the RAM. I hypothesize that the problem, although not with the RAM, is still related with the memory in some way. I will continue to look into this and post any updates I have.

---

### Post by volaer on 2009-12-16
> **LinkedITS said:**
> As I mentioned in a earlier post, the Hash Sum Mismatch might be caused by bad RAM so i devised a experiment to test out my Hypothesis. In the "experiment" that I performed, I took the RAM out of the "Good Machine" and put it into the "Bad Machine." Then I booted into the "Bad Machine with the Good RAM" and tried to install the ntp package. However the installation failed with Hash Sum Mismatch once again. 

Then I put the "Bad RAM" into the "Good Machine" and booted into it. The "Good Machine with the Bad RAM" was able to install properly without any problems at all.

This leads me to the conclusion that the problem is NOT the RAM. I hypothesize that the problem, although not with the RAM, is still related with the memory in some way. I will continue to look into this and post any updates I have.


Hello There Link TS,

I already have get rid of this hash mismatch error. I think it's not your RAM. Most probably its your mixed  program installations. Try these following commands in your terminal:


```
sudo apt-get update -o Acquire::http::No-Cache=True
sudo apt-get clean && sudo apt-get update && sudo apt-get upgrade

```

If you still get some problems try consulting this link:
[http://ubuntuforums.org/showpost.php...1&postcount=10](http://ubuntuforums.org/showpost.php...1&postcount=10)

Concerning your inability to install windows 7, I think it's not about your RAM. Try to go to your CMOS and check the connection of your hard disk, somewhere in SATA or IDE. As far as I know, when you install Vista or higher version of Windows, it has to be in SATA mode. But when you install XP or lower, it has to be in IDE mode. 

You were able to install Ubuntu in your laptop because it doesn't care whether or not it is in SATA or IDE mode. 

Hope this reply helps.:) Blessings!!!

---

### Post by volaer on 2009-12-16
By the way, I did had exact problems at the beginning. And I learned it through experience. I thought my laptop is a mess. But since I fixed and found out the problem, I never had any problems again. :)

---

