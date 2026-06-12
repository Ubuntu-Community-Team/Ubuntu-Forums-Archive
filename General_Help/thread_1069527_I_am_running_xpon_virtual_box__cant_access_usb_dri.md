---
title: "I am running xpon virtual box  cant access usb drives or shared folder"
date: 2009-02-14
forum: General Help
---

### Post by shateredsoul on 2009-02-14
I am running xp as guest on ubuntu, but Icant access usb drives or shared folder

any idea on how to make xp recognize usb devices through virtual machine? I installed the guest additions iso.  But still doesn't recognize (even when I unmount the externa, usb drive, etc)

Also, how can you access the shared folder from xp ?

thank you

---

### Post by shateredsoul on 2009-02-14
sorry... but bump =)

---

### Post by ju2wheels on 2009-02-14
Are you using VirtualBox OSE (open source edition) or the closed source edition?

---

### Post by shateredsoul on 2009-02-14
I'm using the ose version

---

### Post by ju2wheels on 2009-02-14
The OSE version does not support the use of device across USB. If you want that feature you will have to uninstall it and install the closed source version from their website.

---

### Post by shateredsoul on 2009-02-15
Oh ok,

I'm a newb.. I went to the site and it doesn't say anything about OSE or closed. 

I went to the following link

[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

and it has a version to download for ubuntu 8.1, but it has two versions

one for i386 and one for amd64.  I'm using an xps m140 dell.. any idea on which one I need?

Also, is this the closed version? I don't even know how i got the open source one...

Thanks a lot for tolerating my ignorance =)

-shatered

---

### Post by shateredsoul on 2009-02-15
also....

do i need to install any other packages to support the closed version?  I know the ose version needed additional install

and

to completely uninstall the open source version, do I just delete the virtualbox folder in home/user/virtualbox ?

---

### Post by ju2wheels on 2009-02-15
Yes that is the correct downloads page, and that is the closed source version. I checked the specs on your laptop and it appears to have a 32bit processor so the installer you want is the x86 version (aka i386, aka 32bit) (if your processor is not 32bit then it will complain about an incorrect architecture when you try to install it, and know that you the other one in that case).

> **shateredsoul said:**
> 
do i need to install any other packages to support the closed version?  I know the ose version needed additional install

No, the closed source version comes in one package and installs the kernel modules (the second package you are referring to most likely) automatically.

> **shateredsoul said:**
> 
to completely uninstall the open source version, do I just delete the virtualbox folder in home/user/virtualbox ?
You actually do have to uninstall the open source version, however you do not accomplish that by deleting /home/user/.virtualbox as this is your settings folder and not the actual program folder. Therefore you could leave the settings folder there.

To uninstall virtualbox ose run the following command in a terminal (Applications->Accessories->terminal):

```

sudo apt-get remove virtualbox-ose*

```

[edit]
Once you install the closed source version theres a few more steps you need to take in order to use the USB. You can follow the instructions in this older thread here: [http://ubuntuforums.org/showpost.php?p=6128352&postcount=6](http://ubuntuforums.org/showpost.php?p=6128352&postcount=6)

---

### Post by shateredsoul on 2009-02-15
Thanks wheels! works perfectly now.  You were very helpful and patient.  

Thanks again

-shatered

---

