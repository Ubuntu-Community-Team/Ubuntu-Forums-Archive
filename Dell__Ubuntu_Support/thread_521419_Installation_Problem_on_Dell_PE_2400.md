---
title: "Installation Problem on Dell PE 2400"
date: 2007-08-09
forum: Dell  Ubuntu Support
---

### Post by ev500cburke on 2007-08-09
Hello.

I’m having significant problems installing Ubuntu 6.06 LTS (Server Edition) on a Dell PowerEdge 2400.  The installation freezes every time, but at different points during the installation process.  It has frozen thus far during CD-ROM detection, partitioning, time zone setup, and others.  When frozen, I cannot Alt-FX to any other console… the only option is to do a hard reboot.

The machine specs are as follows:
[LIST]
[*]PowerEdge 2400, Dual 1000Mhz PIII
[*]Dell PowerEdge PERC 3/DC 2Ch Raid Controller 64MB 0C705
[*]2GB RAM
[*]IBM Seagate 18 GB U160 SCSI HDD FRU
[/LIST]

I have confirmed the integrity of the CD (although, once it succeeds, pressing CONTINUE simply loops over the CD Integrity Check…. Here again, the only option is a hard reboot), and did run through a memory test.

Any help would be tremendously appreciated.  I am anxious to get these servers operational, and I’m convinced Ubuntu is the way to go.  Please let me know if there are any additional I can provide (e.g. log dumps, etc.)


---- FOLLOW UP --------------------------------------------------------

As a point of follow up (for the benefit of others), I had 4 machines on which I wanted to install Ubuntu Server.  They were:

>  PowerEdge 2400
>  PowerEdge 2500
>  PowerEdge 4400
>  Gateway Select Desktop

On all but one of them (the 4400), Ubuntu Server 6.06 and 7.04 were running into fatal errors during the installation (all at different points).  This occurred both before and after a complete firmware and BIOS update.

Using the Xubuntu Alternate Install CD, I was finally able to install LTS 6.06 on all the machines without a hitch (by selecting the “Install a Server” option from the main menu). This may help others that are running into similar problems.

It appears the packages are the same on both the regular Server CD Download and the Alt. Install Download.  **So the question is – what is the difference between these installation paths?**
Just wanted to finalize the post, and possibly throw something in the queue for discussion.

---

### Post by jd3010 on 2008-05-05
Hi,

had the same problem witha 2500, but got it solved by installing 6.10 and then upgrading through network to 8.10.

I updated manually the sources.list file to include all links to Hardy and to dapper-updates .... and it seemed to have worked.

Hope this helps

---

