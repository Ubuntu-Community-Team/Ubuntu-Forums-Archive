---
title: "where does Ubuntu place all the packages before installation"
date: 2009-11-22
forum: Desktop Environments
---

### Post by yazirazlam on 2009-11-22
Hi,

Can anyone help me with the following issue.

I have installed ubuntu version 9 which is without samba, Winbind and Samba client packages. I have checked the forums to dowload the packages updates by typing **apt-get update** but i gave the **"407 proxy authentication required"** error message. I have manually downloaded the packages from packages.ubuntu.com, however, i don't know where do i have to place these packages so that i can install it on ubuntu.

Can anyone suggest the path where i have to copy my packages so that i can install it from the "**Terminal**". Also, if I paste any file in the **file system** the OS says that you don't have the permissions to move data on to this folder.

Or Can anyone suggest me where can i find Ubuntu with complete packages.


All your help will be appreciated.

Thanks,
yasir

---

### Post by wilee-nilee on 2009-11-22
I think you need to go to software sources and open the multiverse repositories then run a sudo update or reload in synaptic.

---

### Post by yazirazlam on 2009-11-23
Hi, 
 
Thanks for the quick reply. Actually i don't have internet connection on my computer that's why i cannot get the updates from the internet. I have downloaded my required packages but i don't know which directory do i have to put these files so that Package Manager can install it.
 
One option is that i can put all the downloaded packages named samba, winbind, krb5-user into CD and add CD into software sources. However, I can't do it because the server on which i have installed ubuntu that server is at the remote location and i am remotely connecting to it.
 
 
THanks,
Yasir

---

### Post by oldrocker99 on 2009-11-23
Look in /var/cache/apt/archives/.

You can, you know use

> locate *.deb

to find where files are.

:guitar:

---

### Post by yazirazlam on 2009-11-24
Thanks for a quick reply. I have checked /var/cache/apt/archives/ path but i only found **lock and partial file **in there. 
 
 
I have downloaded the packages and just need to install it on UBUNTU. I just need to know where do i **place the downloaded packages **(samba, Krb5-user) so that Ubuntu package manager can install it without asking for the internet connection. Normally, Package manager requires internet connectivity to download the packages.
 
Thanks for the help so far.

---

