---
title: "Trying to Install Ubuntu via VMWARE"
date: 2007-07-19
forum: Dell  Ubuntu Support
---

### Post by Kromax on 2007-07-19
HI,

im trying to install Ubuntu on my 
Laptop D620 Latitude from Dell

I have the latest VMWare(Full Version) and Ubuntu Download
Ive tried couple of diff installations i keep getting the same error every time over and over again.

**********
VMware Workstation unrecoverable error: (vcpu-0)
NOT_REACHED F(562):1742
A log file is available in "D:\Data\My Virtual Machines\Other Linux\vmware.log".  A core file is available in "d:\Documents and Settings\adm_ext946\Application Data\VMware\vmware-vmx-2088.dmp".  Please request support and include the contents of the log file and core file.  We will respond on the basis of your support entitlement.

**************

i have NO clue why i keep getting it any one has an idea 
if you need anymore info just ask ill be happy to post

---

### Post by porcorosso on 2007-07-19
Well, drat! I'm going to be no help to you. But I'm going to hang around to see what you learn. Because I need to learn it, too.

Only difference is that I'm thinking of installing Ubuntu under VMWare Player. I guess maybe I have to download an Ubuntu "appliance" for that, but I don't know for certain.

My search skillz must zuck. I looked to see if anyone had posted about this before I started a new topic, but I didn't see your thread until I had already posted.

---

### Post by ihristov on 2007-07-19
> **porcorosso said:**
> Only difference is that I'm thinking of installing Ubuntu under VMWare Player. I guess maybe I have to download an Ubuntu "appliance" for that, but I don't know for certain.

If you are going to use VMWare Player you cannot create new virtual machines so you need to download a ready-made "appliance".

Go to the [VMWare appliances site]("http://www.vmware.com/vmtn/appliances/directory/cat/45") and pick and download one of the numerous Ubuntu appliances from there. I would recommend you to select one that has VMWare Tools already installed.

Also make sure you have plenty of RAM for good performance. If you ask me you need to have 1 GB of RAM. You can get by with 512 MB, but don't expect it to be snappy.

---

### Post by ihristov on 2007-07-19
At what point in the installation are you getting this error?

Which file did you download? Did you double-check the MD5 sum for it? Maybe your download is broken.

---

### Post by porcorosso on 2007-07-19
> **ihristov said:**
> If you are going to use VMWare Player you cannot create new virtual machines so you need to download a ready-made "appliance".

Go to the [VMWare appliances site]("http://www.vmware.com/vmtn/appliances/directory/cat/45") and pick and download one of the numerous Ubuntu appliances from there. I would recommend you to select one that has VMWare Tools already installed.

Also make sure you have plenty of RAM for good performance. If you ask me you need to have 1 GB of RAM. You can get by with 512 MB, but don't expect it to be snappy.

Okay, thanks for confirming my suspicions, ihristov, and thanks for the advice. I'll stop hijacking this thread now since my issue doesn't really pertain to the OP. My apologies for that.

---

### Post by Kromax on 2007-07-20
Installation worked fine i followed this Guidelines

[URL="http://homepage.sunrise.ch/mysunrise/ekeller00/ubuntu/2a_UbuntuInWindows_VMware_e.html"]Ubuntu in Windows
with VMware Player and VMware Server[/URL]

---

