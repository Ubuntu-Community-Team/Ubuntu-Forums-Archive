---
title: "Installing on new primary hard drive with existing secondary drive"
date: 2008-04-23
forum: Desktop Environments
---

### Post by LeeU on 2008-04-23
I currently have a Windows system on my desktop (using Ubuntu on my laptop for now). It has a primary drive (for the OS), and a second hard drive (for storing data). I want to change out the primary drive and install Ubuntu (w/Windows in VB), and keep the secondary drive with the data. If I replace the current primary drive with an empty new one, set as the master and leave the current second drive set as the slave, will Ubuntu know which one to use, so I don't delete all the data on the second one? OR, should I take all the drives out, install the new empty one, install Ubuntu on it, and once Ubuntu is up and running, then add the second one?

---

### Post by benerivo on 2008-04-23
Have both of them in the machine, then install. During the installation you will be given the option for which drive you want to use. If you have set them up correctly (ie os drive = master and personal data = slave), then you can choose the master as the installation target for ubuntu (it will be called hd0 or sd0, as opposed to hd1 or sd1 which is your data drive), and you can give the slave hard drive a useful mount point such as /media/Data.

---

### Post by LeeU on 2008-04-23
Thanks! That's what I was thinking but just wanted to make sure.

---

### Post by dailyfare on 2011-04-12
thank you, I'm new to xubuntu and this has been helpful. I did an installation pretty much exactly as described here and it worked great. I am having a hard time navigating the file system to view the secondary slave drive, can someone point me in the right direction?

---

