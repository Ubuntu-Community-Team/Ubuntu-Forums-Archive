---
title: "Unable to load module PKCS #11 for personal certificate"
date: 2023-02-17
forum: Desktop Environments
---

### Post by rafast2 on 2023-02-17
Hi all, 

I wanted to use the personal certificate on my electronic Identity card (DNIe in Spain) to authenticate myself on web pages. I have followed the steps I have found on internet but I am stuck on one of the final steps.

So far this is what I have:

Ubuntu 22.04 recently installed
MSI Creator intel i7, 32Gb RAM Nvidia 3050Ti

.deb is downloaded from this path
[https://www.dnielectronico.es/portaldnie/PRF1_Cons02.action?pag=REF_1112](https://www.dnielectronico.es/portaldnie/PRF1_Cons02.action?pag=REF_1112)

I have followed some tutorials found on the internet and I have check my SmartCard reader is working correctly and it can read data from my electronic identity card.

The problem comes when it is needed to install a "security device" and it is then when I should add a file called libpkcs11-dnie.so located in usr/lib. I received the errors you can see in the snapshots. 

This file is installed from the .deb file in the previous link.

I am wondering if this is due to the .deb file is developed for Ubuntu 21.04 and I am running 22.04.

Any help?

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=291802&stc=1[/IMG][IMG]https://ubuntuforums.org/attachment.php?attachmentid=291803&stc=1[/IMG]

---

### Post by ActionParsnip on 2023-02-17
Is the browser installed via snap? If so then you will need to grant the snap access to the files it needs

---

