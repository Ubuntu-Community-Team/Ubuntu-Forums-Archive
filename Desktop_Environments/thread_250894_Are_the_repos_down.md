---
title: "Are the repos down?"
date: 2006-09-04
forum: Desktop Environments
---

### Post by lonelypauly on 2006-09-04
im following the instructions from the following thread on how to install a canon ip3000 printer...and the packages i need from synaptic are failing to download...my internet connection is fine...any ideas?

[http://ubuntuforums.org/showthread.php?t=38995](http://ubuntuforums.org/showthread.php?t=38995)

---

### Post by powder on 2006-09-04
I just quickly browsed over this how-to.  The only packages you need from the repos are alien and libxml1.  Try:

sudo aptitude update
sudo aptitude install alien libxml1

If this doesn't work your sources.list might be messed up.

---

### Post by lonelypauly on 2006-09-04
thank you...something is definitely wrong...have a look at this:

Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg
  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
0% [Connecting to us.archive.ubuntu.com (1.0.0.0)]

---

### Post by Najand on 2006-09-04
They are all working. I was apt-getting a few softwares and it was working just fun.
Well, for Canon ip3000, just download the "gutenprint" driver at 
[http://www.linuxprinting.org/show_driver.cgi?driver=gutenprint]("http://www.linuxprinting.org/show_driver.cgi?driver=gutenprint")
and use the PPD file for the BJC-7000. It must work fine and there is no need to convert those RPMs to Debs.

---

### Post by powder on 2006-09-04
> **lonelypauly said:**
> thank you...something is definitely wrong...have a look at this:

Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg
  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
0% [Connecting to us.archive.ubuntu.com (1.0.0.0)]

Could you please post your entire sources.list?  Just open a terminal and type:

gedit /etc/apt/sources.list

Then copy everything in there and post it here.

---

### Post by lonelypauly on 2006-09-04
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

---

### Post by powder on 2006-09-04
That sources.list looks fine.  Are you able to access the repos by clicking on the links in your web browser?

---

### Post by powder on 2006-09-04
I did some research and it seems your problem has to do with DNS.  If you are behind a router, see if you can update the firmware if an update is available.  Also, go to System -> Administration -> Networking and click on the DNS tab.  Make sure your ISP's DNS servers are in there.

---

### Post by lonelypauly on 2006-09-04
> **powder said:**
> I did some research and it seems your problem has to do with DNS.  If you are behind a router, see if you can update the firmware if an update is available.  Also, go to System -> Administration -> Networking and click on the DNS tab.  Make sure your ISP's DNS servers are in there.


Here is what i have

 DNS SERVERS:
192.168.0.1
205.171.3.65

Search Domains:
domain.actdsltmp

How do i go about fixing this problem...OR... downloading these files directly for now just so my moms printer starts working...this is all very silly...what a crap router this is...the isp is qwest in Phoenix, AZ

Thanks so much for helping guys.

---

### Post by powder on 2006-09-04
Call up Qwest and verify the DNS servers you are supposed to be using.  I can tell you right now the 192.168.0.1 is not pointing to a DNS server, it's probably pointing to your router.

There is no other way to install these packages because they may have dependencies which also must be installed in order for them to work.

---

