---
title: "Dell Poweredge 2500 and Gutsy 7.10"
date: 2007-11-28
forum: Dell  Ubuntu Support
---

### Post by scottie4442 on 2007-11-28
I am just writing this for the benefit of those trying to do a similar install, maybe you will not have the same problems that I have had.  

My mission here is to get Ubuntu 7.10 Gutsy onto a Dell Poweredge 2500 with 2GB memory, a RAID 5 array with 144 GB of room, Dual 1.26 Ghz processors, and a DVD drive installed (I acquired the DVD drive from ebay).  I tried several different burned copies of Gutsy, both the DVD iso and Server x86 iso, the only one that worked for me is the minimal iso. I used the minimal iso burned to a disk and installed server, including LAMP and several other things, from the internet.  I got this to work with out any problems.  I am in the process of downloading the dell omsa for debian, to do this I added a line for a third-party repository as follows:
deb [ftp://ftp.sara.nl/pub/sara-omsa](ftp://ftp.sara.nl/pub/sara-omsa) dell  sara

Then I updated my repositories and when I searched for omsa it appeared in synaptic.  I selected it, and all the dependencies, and it seems to be downloading fine.  I will post followups to this as I finish other steps.

Hopefully this will help others

Scott Adams
Computer Network Instructor
Southeast Arkansas College
Pine Bluff, Arkansas

---

### Post by sickpuppet on 2007-12-05
Hi Scott - 

Thanks for this!

I recently 'inherited' a Dell PowerEdge 2500 with a similar spec and ran into problems attempting to start Ubuntu 7.10 Gutsy Gibbon Desktop from CD. The boot sequence fails shortly after the kernel has been loaded, dropping me to an ash (initramfs) prompt with some errors from (I guess) init. I'll provide the full text of the errors here when I have the machine in front of me.

I'll try the minimal ISO and report my efforts here.

(Edit: Can't help pointing out that I'm glad your sig makes it pretty clear you're not the Scott Adams responsible for this: [http://www.dilbert.com/comics/dilbert/archive/dilbert-20071202.html](http://www.dilbert.com/comics/dilbert/archive/dilbert-20071202.html))

regards
Ben

---

### Post by timslim on 2007-12-05
I've had the same problem as Ben.  Exact same description.  I'm going to try the minimal ISO that Scott Adams recommended.

Tim

---

### Post by sickpuppet on 2007-12-11
Hi Tim - 

Any joy with your installation? Turns out my CDs were all rubbish (and I was starting to blame the CDROM drive in the Dell after looking in /var/log/syslog). I'd used an old 800Mhz IBM box to burn the CDs, into which I'd temporarily installed a 48x CDROM drive. I used k3b to burn the images, and despite the fact that they checked out correctly in k3b, they were junk.

Bit of a waste of a weekend.

---

### Post by scottie4442 on 2007-12-11
The only way I could get it to install is using the minimal ISO, and installing the packages from the web, refer back to the beginning of the post.  After I completed the install and updates, everything seems to work great.

---

### Post by timslim on 2007-12-15
Thanks, I'll try a new CD burn on another system.  If that doesn't work, I'll go with minimal installation and download from web.

On our new Dell servers that we're ordering next year, I may go with Dell installed Redhat.  Ubuntu's interesting, but it's handy to have a good support organization behind you.

---

### Post by scottie4442 on 2007-12-15
I will be real honest, we have a couple of Redhat servers at work and I usually get better help for them on this board, we are also running 4 Ubuntu server machines, They call Redhat support and have to wait two ro three days for an answer, IT sends me the issue and I post it here and linuxquestions.org and I have an answer within hours.  I just wanted to say this and let you make your own decisions.  I do not work directly for IT, I teach Computer Networking at a 2-year school, but I am kinda the backup for IT, I have a few years more experience than the director, so I help out when I can.

---

### Post by sickpuppet on 2008-02-08
Hi, I know this is a bit stale, but I'm posting this reply for posterity:

In order to find out if your CDs are junk, first check the md5sum hash of the ISO you downloaded. Find the hashes here:

[http://releases.ubuntu.com/7.10/MD5SUMS](http://releases.ubuntu.com/7.10/MD5SUMS)

If they don't match, throw away the ISO image and download it again.

After you've burned the CD, boot off it and run the disk integrity check before attempting an install.

regards
Ben

---

### Post by scottie4442 on 2008-02-08
Did both of these and both checked good, the DVD drive still would not read the disk.  There is something about these drives that they do not like burned disks, I have a student that has a Dell laptop with a similar drive and his will not read a burned disk well either.

---

### Post by sickpuppet on 2008-02-08
> **scottie4442 said:**
> The only way I could get it to install is using the minimal ISO, and installing the packages from the web, refer back to the beginning of the post.  After I completed the install and updates, everything seems to work great.

Hi - 

Ended up putting Red Hat Enterprise 4u4 on that box, booting off the boot.iso (minimal 30Mb install CD) that comes on the CD install set and doing the rest of the install from the network.

So as Scott says the moral of the story is that the CDROM drive in Dell PowerEdge 2500s is a duffer at reading burned CDs.

regards
Ben

---

### Post by jd3010 on 2008-05-05
Hi all,

had the same problem, but got it solved by installing 6.10 and then upgrading through network to 8.10.

I updated manually the sources.list file to include all links to Hardy and to dapper-updates .... and it seemed to have worked.

Hope this helps

---

