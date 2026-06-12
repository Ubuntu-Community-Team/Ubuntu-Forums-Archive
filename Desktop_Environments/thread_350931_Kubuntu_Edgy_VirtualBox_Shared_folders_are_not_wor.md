---
title: "Kubuntu Edgy VirtualBox Shared folders are not working"
date: 2007-02-01
forum: Desktop Environments
---

### Post by P]-[L0 on 2007-02-01
Hey @all

I have an Kubuntu edgey as Host with VirtualBox and an WinXP running as Guest.
I installed all xalan packages (apt-get install xalan) and the Virtualbox dep.
Now I added an Share with 

VBoxManage sharedfolder add winxp -name "test" -hostpath "/tmp/test"

Now i try to find it in "Entire Network" but when I click on "VirtualBox Shared Folders" i am keep getting an error "Unable to browse the network. The request is not supported."

Anyone an glue what happens?

cheers

phlo

---

### Post by xilix on 2007-02-14
On [http://virtualbox.org/wiki/Editions]("http://virtualbox.org/wiki/Editions") you can see, that Shared Folders are only supported in the Closed Source Edition.

I also consider using VirtualBox, but without Shared Folders this makes no sense to me. 

Does anyone know how one could sail around this??? :(

---

### Post by xilix on 2007-02-14
You can also download the binaries of the full version (non open source) at virtualbox.org for personal use or evaluation.

---

### Post by nixitup on 2007-09-24
One thing that I have done to bypass this issue is to use a USB flash drive.  I can copy right to it in ubuntu then mount it in XP.  works alright, however I still a bit awkward.  The other suggestion which I haven't tried yet is creating a local FTP server either the kubuntu os or in xp.

---

