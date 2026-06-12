---
title: "Bitpim in Ubuntu 9.04"
date: 2009-05-01
forum: General Help
---

### Post by amtnbiker16 on 2009-05-01
Does anyone know how to get an LG vx8300 to work in bitpim?
It wont detect the phone, but it knows what port it is on and says that the port is unavailable.  Btw, i ran bitpim as root, so its not a permissions thing.  Bitpim is already upgraded to the latest version I can find.
Any help would be appreciated.  This post is not redundant as far as I can tell, I could only find posts related to previous ubuntu and bitpim releases

---

### Post by Guitarmaster316 on 2009-05-01
I am having the same problem.  Hopefully someone smarter than I am can post a fix!

---

### Post by wizard10000 on 2009-05-03
Spam (searched for bitpim threads) but I got mine working.

I purged the 1.0.6 installation from Jaunty and installed v1.05 from Soureforge and my phone connected first time on /dev/ttyACM0 - wouldn't connect at all with the version of bitpim that comes with Jaunty.

Link to sourceforge archive:

[http://sourceforge.net/project/showfiles.php?group_id=75211&package_id=75636](http://sourceforge.net/project/showfiles.php?group_id=75211&package_id=75636)

---

### Post by Guitarmaster316 on 2009-05-03
Hey Wizard,

Tried installing 1.0.5 but it didn't support my phone LG LX570 Muziq.

Thanks though

---

### Post by wizard10000 on 2009-05-04
> **Guitarmaster316 said:**
> Hey Wizard,

Tried installing 1.0.5 but it didn't support my phone LG LX570 Muziq.

Thanks though

Just a thought - maybe try the 1.0.6 version on sourceforge?

---

### Post by amtnbiker16 on 2009-05-04
K, 1.0.5 works, thanks for the link.

---

### Post by quazi on 2009-05-04
1.05 fixed my problems.

---

### Post by wizard10000 on 2009-05-05
Might be a good idea for y'all to lock the version in synaptic so update manager doesn't keep prompting y'all to upgrade.  I did allow synaptic to update to 1.0.6 again just to see if maybe it was a missing library and the upgrade broke bitpim again so I purged again and reinstalled 1.0.5 - and everything works once more.

---

### Post by PatricioLearner on 2009-06-06
Getting the .deb package a
as noted above solve part of my problem too. 
I am trying to get the pictures out of VX8300, but it seems that bitpim cannot do it. Is there another way?

---

### Post by redgs95 on 2009-06-08
new to linux and ubuntu and want to know how to purge bitpim and install the earlier package(1.0.5) and also how to lock it from upgrading.:???:

---

### Post by PatricioLearner on 2009-06-10
The instructions go something like this:
to purge:
  System -> Administration -> Synaptic Package Management
  Then search for bitpim and select to uninstall

to install:
  follow [http://sourceforge.net/project/downloading.php?group_id=75211&filename=bitpim_1.0.5_i386.deb&a=45746945](http://sourceforge.net/project/downloading.php?group_id=75211&filename=bitpim_1.0.5_i386.deb&a=45746945)
  download and then just click on it


to prevent version from updating:
   System -> Administration -> Synaptic Package Management
  Then search for bitpim and -> package -> select Lock Version

BTW: I was able to get the pictures off the phone bitpim, if I recall correctly the connection was hard to establish, I think I had to keep the phone open for it to work.

---

### Post by redgs95 on 2009-06-10
[http://polygon89.wordpress.com/2008/08/31/how-to-get-bitpim-to-detect-your-cellphone-in-ubuntu-linux/#comment-196](http://polygon89.wordpress.com/2008/08/31/how-to-get-bitpim-to-detect-your-cellphone-in-ubuntu-linux/#comment-196)
This is where i found out how to get bitpim working. Thanks for the info here as well.

---

### Post by pgn674 on 2009-06-27
For me, versions 1.0.5 and 1.0.6 from [SourceForge]("http://sourceforge.net/project/showfiles.php?group_id=75211&package_id=75636") both worked, but 1.0.6.dfsg.1-1ubuntu2 from the repositories did not, on Ubuntu 9.04.

---

### Post by nxmehta on 2009-07-19
> **pgn674 said:**
> For me, versions 1.0.5 and 1.0.6 from [SourceForge]("http://sourceforge.net/project/showfiles.php?group_id=75211&package_id=75636") both worked, but 1.0.6.dfsg.1-1ubuntu2 from the repositories did not, on Ubuntu 9.04.

I see the same thing... what the heck is going on here?  What did the Ubuntu packagers for this change so that it breaks if you use the Ubuntu package?

---

### Post by butterman on 2009-08-24
Downgrading to Bitpim 1.05 worked for me too.

---

### Post by sir4taye on 2009-09-05
I'm testing 1.0.7. Lets hope for the best.

---

### Post by Riptie on 2009-09-14
> **butterman said:**
> Downgrading to Bitpim 1.05 worked for me too.
 
I can't seem to get bitpim to run after I downgrade... Have 1.05 installed...It doesn't show up in my Applications--->Accessories list
 
 
Anyone have any ideas...

---

