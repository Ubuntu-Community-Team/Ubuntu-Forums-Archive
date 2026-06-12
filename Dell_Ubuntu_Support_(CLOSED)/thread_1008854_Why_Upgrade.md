---
title: "Why Upgrade?"
date: 2008-12-11
forum: Dell Ubuntu Support (CLOSED)
---

### Post by blueb73 on 2008-12-11
I got one of the first dell laptops with ubuntu pre-installed (inspiron e1505 running 7.04) and it does everything i need (cept play animated gifs!!)

what do I get if I upgrade to the latest version that I dont have now?  :confused:

thanks!

---

### Post by lisati on 2008-12-11
The main reason I can think of is to keep up with security updates.

---

### Post by iponeverything on 2008-12-12
Updates mostly. 

[http://www.ubuntu.com/news/ubuntu-7.04-end-of-life](http://www.ubuntu.com/news/ubuntu-7.04-end-of-life)

If you do decide to upgrade. 

- backup /home to CD or flashdrive - if there is anything that you might want keep.

- do the upgrade Incrementally as recommended in the above URL. 

7.04 -> 7.10 -> 8.04

I would do the upgrades via CD if possible.
(Do NOT choose the install from CD boot menu -- Boot the live CD)

---

### Post by blueb73 on 2008-12-12
> **iponeverything said:**
> Updates mostly. 

[http://www.ubuntu.com/news/ubuntu-7.04-end-of-life](http://www.ubuntu.com/news/ubuntu-7.04-end-of-life)

If you do decide to upgrade. 

- backup /home to CD or flashdrive - if there is anything that you might want keep.

- do the upgrade Incrementally as recommended in the above URL. 

7.04 -> 7.10 -> 8.04

I would do the upgrades via CD if possible.
(Do NOT choose the install from CD boot menu -- Boot the live CD)

my biggest fear is something crashes it, and my laptop becomes a paperweight   ](*,)

---

### Post by jsonder on 2008-12-13
I've re-installed 8.04 on my e1505 (was running 8.10 but don't like the kde4 changes to ksudoku).  8.04 has the buggy network manager which loses wireless WPA passphrases, so I use wicd instead of ubuntu's network manager.

Your computer should be compatible with 8.04 and it will have security updates for another couple of years.  I'd sure advise upgrading to keep your customizations, but a clean install gets rid of the cruft that you've accumulated.

I normally do an manual disk partitioning with "/", "swap", and "/home" partitions, giving 10-15 gig to the root partition, a gig or two to the swap, and the rest to the home partition where all of the user data is stored.  Then when I upgrade/downgrade with clean installs, I still have my data in the UNFORMATTED /home partition.

---

### Post by mkvnmtr on 2008-12-13
If your worried about your machine not working with the upgrade and loosing your system you can make an live disk from your current system to reinstall if you have problems you can't resolve. Use APToncd. It is in the repositories.

---

### Post by natehall on 2008-12-13
My 1420 Inspiron came with a 32 bit version of Ubuntu , but the chip is 64 bit. I did a fresh install with 8.10 64 bit . GIMP processes things a whole lot faster now. I pretty much do a fresh install with each new version of Ubuntu because it's a good reason to back up my data on at least a 6 month basis.

---

### Post by Old_Grey_Wolf on 2008-12-14
> **mkvnmtr said:**
> If your worried about your machine not working with the upgrade and loosing your system you can make an live disk from your current system to reinstall if you have problems you can't resolve. Use APToncd. It is in the repositories.

I was just browsing the forum and found this post. I was looking for something like APToncd. Nice tool. Thanks.

---

### Post by notwen on 2008-12-14
If you're not one to frequently upgrade, I would recommend at least keeping the LTS versions.  I have a Inpsiron 1420n that came pre-installed w/ Fiesty and it is currently running a vanilla Hardy install.  Check out the [Dell Linux Wiki]("http://linux.dell.com/wiki/index.php/Products/Client"), here is a link to [Dell's very own custom Ubuntu Hardy image]("http://linux.dell.com/wiki/index.php/Ubuntu_8.04#Dell_OS_Factory_Recovery_8.04.1_DVD_ISO") w/ all additional drivers/packages their N-Series machines need.  There is also a table of issues and the affected models and links that provide a fix/workaround for said problem.  I highly suggest you take a look.

I would also stress the security updates you will be missing out on in the future, hence why I keep my laptop on the LTS versions of Ubuntu as I don't have time to constantly re-install and get the machine working the way it was previously.  

Should you decide that you're ready and comfortable enough to go ahead and install this, be sure to backup any data you do not want to lose.  Dell's custom Ubuntu installers also setup a partition table including a restore partition just as they do when they send out new N-Series machines.  Please feel free to ask any questions you may have and myself and the others will do our best to answer them for you.  =]

---

