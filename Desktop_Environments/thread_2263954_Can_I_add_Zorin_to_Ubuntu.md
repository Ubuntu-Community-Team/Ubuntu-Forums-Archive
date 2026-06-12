---
title: "Can I add Zorin to Ubuntu ?"
date: 2015-02-04
forum: Desktop Environments
---

### Post by hebdave on 2015-02-04
High I have looked on the net and there appears to be a whole host of booting problems with adding a third op. Or at least the computer sees it as a third op. on booting I mean - hence the problem I think ? I'm coming from windows being the first op, ubuntu the second added to it , and then trying to add Zorin causing the issue I believe. 

So instead **if I am going to do this at all** I think I should add Zorin repositories and packages into Ubuntu somehow- then have 2 ops only. Since I am a novice user of Ubuntu I am relatively clueless but can follow terminal instructions given. Beyond that I'd need explanation. I found this on my hunt in Google and wondered what it actually gave me [http://askubuntu.com/questions/469548/which-desktop-environment-does-zorin-os-use-and-how-to-get-for-ubuntu](http://askubuntu.com/questions/469548/which-desktop-environment-does-zorin-os-use-and-how-to-get-for-ubuntu)

Is the link going to give me an app effectively that is added to Ubuntu ? Will I need to enable the repository before it works in Ubuntu ? Will it harm the Ubuntu op. in anyway by adding these commands ? Will ubuntu suffer internal errors ( a thing I sometimes see). Or will I get booting errors ?

Currently I have a multiboot with a "purple grub screen" when booting with Ubuntu and windows options. Windows 7 was installed first and then I let the Ubuntu installer automatically assign the partitions with a 220 GB on each partition. But my idea is not to add a third partition with a new install of Zorin as stated. Instead I wanted to add packages and repositories if I am correct in saying that. Given I am a novice I am "winging it a bit" in what I am saying to you. So I may not be saying accurate statements. Hoping this is easy enough and someone would help me out. 

Thanks !! :)

---

### Post by yancek on 2015-02-04
Zorin uses the Ubuntu repositories.  If you comparee the sources.list for repositories on Zorin and Ubuntu I doubt you'll see any difference, except maybe if you are using different version.  Zorin is derived from Ubuntu and although there are differences, a lot of them are superficial meant to make it look more like windows.  Below is the top section of the sources.list file from Zorin 9.  Note they all say ubuntu.  All the rest of the entries are also ubuntu.


> #deb cdrom:[Zorin 9 trusty - Release i386 (20140712)]/ trusty main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates main restricted


You can install Zorin inside Ubuntu using virtual software such as Virtualbox or vmware.  Otherwise, you need to install Zorin to a separate partition.



---

### Post by Frogs Hair on 2015-02-04
Zorin uses a variation of the AWN dock as the bottom panel of  the desktop  which isn't available for Ubuntu through the official repository.

---

### Post by hebdave on 2015-02-05
Okay thanks for you help seems I cannot make it one big app for ubuntu. Thanks.

---

### Post by yancek on 2015-02-05
> Zorin uses a variation of the AWN dock as the bottom panel of  the  desktop  which isn't available for Ubuntu through the official  repository. 				

I'm not sure how that relates to the question asked by the OP.  The 'AWN dock' comes with the default installation.  I'm sure the big 'Z' icon on the Zorin menu isn't in the Ubuntu repositories either.  The point is that what the OP asked isn't going to work without virtualization and a default install of Zorin has only Ubuntu repositories.

hebdave:

An option which I don't think is what you want, is to put the Zorin iso inside Ubuntu and create an entry in the grub.cfg boot menu of Ubuntu and that way you will have Zorin inside Ubuntu.  Problem with that is it will be basically a Live CD, you can use it like you would an actual install but it will be read-only, no changes you make to it will be saved on reboot.

---

### Post by Frogs Hair on 2015-02-05
> I'm not sure how that relates to the question asked by the OP. The OP linked terminal commands for Zorin themes and icons which work fine in Ubuntu. The Zorin desktop environment components are not available in the Ubuntu repository and so can't be added as an extra session like lxde or xfce and so on .

---

### Post by egeezer on 2015-02-05
FWIW, I happen to be running a triple boot of Windows 7, Xubuntu, and Zorin - set it up just to see what Zorin was like.  No troubles for the month or so it's been running (classic distro-hopper here!), rather a nice distro but doesn't encourgage scripting.

---

### Post by Rex Bouwense on 2015-02-05
Back in my distro hopping days, I had 4 different distros installed on an ASUS netbook.  There was never a problem.  You should not be afraid to put Zorin on your computer in its own partition.

---

### Post by yancek on 2015-02-06
> The Zorin desktop environment components are not available in the Ubuntu  repository and so can't be added as an extra session like lxde or xfce  and so on . 				

I guess we are reading the OP request differently because what I read is that he some how wanted to add Zorin inside Ubuntu by simply adding repositories.  The only common ways to do that in Linux that I am aware of are virtualization of a frugal install, a Live CD on the hard drive.  

On the other hand, reading over the first paragraph in his initial post it seems more like all he wants is a third operating system on his computer to add to the other two which is a simple process.  The site below explains booting 145 operating systems on one computer with Grub Legacy.

[http://6697275.blog.163.com/blog/static/3969367520078191839530/](http://6697275.blog.163.com/blog/static/3969367520078191839530/)

---

