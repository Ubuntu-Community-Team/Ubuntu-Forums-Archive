---
title: "Make Ubuntu default GRLDR boot"
date: 2009-02-14
forum: General Help
---

### Post by lingenfr on 2009-02-14
Like the subject says, I would like to boot into Ubuntu by default rather than XP. I have looked at the various menu.lst under /ubuntu but the setup is a bit confusing. I would rather not hose my system. Thanks.

---

### Post by uidb4056 on 2009-02-14
You can install StartUp-Manager it is in the repositories, go to menu System-Administration-Synaptic Package Manager an press the search button, search for 'StartUp-Manager' an mark it to install, apply the changes and after that you will have under Administration menu a new option 'StartUp-Manager', start it and you can select the default OS startup among another set of possibilities, anyway be carefully changing things tha you don't know the consequences.

---

### Post by lingenfr on 2009-02-14
Thanks for the thorough reply. I know how to edit grub from within Ubuntu. That does not work with wubi/grldr. I expect that I will have to boot into windows and either edit one of the many menu.lst files or some similar file. Thanks.

---

### Post by uidb4056 on 2009-02-15
> **lingenfr said:**
> Thanks for the thorough reply. I know how to edit grub from within Ubuntu. That does not work with wubi/grldr. I expect that I will have to boot into windows and either edit one of the many menu.lst files or some similar file. Thanks.

Yeah! there was important information missing that you are running ubuntu from wubi install, in such case to set default ubuntu on boot you need to edit boot.ini file in windows (c:\boot.ini), at this point I've not XP available and can't tell you exactly how to change, but to change it you should be aware that it's a read only file and you need to change the attributes before edit.

---

### Post by lingenfr on 2009-02-15
I thought that posting in the WUBI forum and referencing GRLDR would be enough. I will provide more information next time. There is no boot.ini in C:\. I was expecting that the windows boot manager would point to a GRLDR menu.lst file. Bad guess on my part.

---

### Post by uidb4056 on 2009-02-15
> **lingenfr said:**
> I thought that posting in the WUBI forum and referencing GRLDR would be enough. I will provide more information next time. There is no boot.ini in C:\. I was expecting that the windows boot manager would point to a GRLDR menu.lst file. Bad guess on my part.
I'm sorry I was looking at the new posts and was not aware of the forum you was posting.

If you have Windos XP you should have a boot.ini file on C:\, may be you don't see it because have also an attribute of hidden file, then if you don't change in file explorer under Tools-Folder Options to show all hidden files and folders you don't see it.

You can check if really exist even you don't see running a dos window and run this command:

tpye C:\boot.ini

you will see the output with the contents of boot.ini

---

### Post by lingenfr on 2009-02-15
I just mounted it under Ubuntu. My boot.ini has the following. What changes should I make?

[boot loader]

timeout=15

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

c:\wubildr.mbr="Ubuntu"

---

### Post by uidb4056 on 2009-02-15
> **lingenfr said:**
> I just mounted it under Ubuntu. My boot.ini has the following. What changes should I make?

[boot loader]

timeout=15

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

c:\wubildr.mbr="Ubuntu"

You can try to change default line to have:

[COLOR=Blue]default=c:\wubildr.mbr[/COLOR]

Be sure to make a backup copy of boot.ini file before modify.

---

### Post by lingenfr on 2009-02-15
No offense, but I am going to wait for a post from someone who has done it and can maybe post theirs. As a mistake will leave my system unable to boot, I don't want to spend the rest of my weekend sorting it out. I agree that you are on the right track.

---

### Post by azmo35 on 2009-02-15
Hi,the master guru [caljohnsmith] says 
> [boot loader]
timeout=10
[COLOR="Blue"]default=c:\wubildr.mbr[/COLOR]
[operating systems]
c:\wubildr.mbr="Ubuntu"
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="XP" /noexecute=optin /fastdetect
you can edit the boot.ini from wubi/ubuntu under host, from this tread [here]("http://ubuntuforums.org/showthread.php?t=1021506"),i hope this help.

---

### Post by lingenfr on 2009-02-15
That took care of it. Thanks.

---

