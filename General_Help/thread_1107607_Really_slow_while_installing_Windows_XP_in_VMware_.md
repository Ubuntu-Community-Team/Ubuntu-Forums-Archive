---
title: "Really slow while installing Windows XP in VMware Workstation"
date: 2009-03-26
forum: General Help
---

### Post by Pidgin on 2009-03-26
I have installed the latest VMware Workstation 6.5.1 build-126130. However, when I starts to install Windows XP Professional, weird things happen. It is really quite slow during the installation. In fact, I am doing it. And I am not sure whether the installation can successfully end.
I put the virtual machine and related files on an NTFS partition. I am not sure whether it is the cause.
What has happened? How can I solve it? Thank you!

---

### Post by Xiong Chiamiov on 2009-03-27
You shouldn't really be using NTFS for write in Linux, unless you really have to.  The virtual machine will take care of making Windows run right, no matter the filesystem the image is stored on.

---

### Post by albandy on 2009-03-27
As Xiong Chiamiov said, don't install VM in a NTFS partition. And I recomend you to use VirtualBox, its free and works very well with Linux, and allow you to use CPU native virtualization (modern cpu's have this feature)

---

### Post by Pidgin on 2009-03-28
> **Xiong Chiamiov said:**
> You shouldn't really be using NTFS for write in Linux, unless you really have to.  The virtual machine will take care of making Windows run right, no matter the filesystem the image is stored on.

Wow, you are right. I have confirmed that the slowness is caused by putting the virtual machine on an NTFS partition. After creating a new virtual machine on an ext3 partition, VMware runs quite well.

---

### Post by Pidgin on 2009-03-28
> **albandy said:**
> As Xiong Chiamiov said, don't install VM in a NTFS partition. And I recomend you to use VirtualBox, its free and works very well with Linux, and allow you to use CPU native virtualization (modern cpu's have this feature)

I have tried VirtualBox for quite a time. It's really good. But I really want to use branch snapshot, which is lack in VirtualBox. See this post: [http://ubuntuforums.org/showthread.php?t=1107617]("http://ubuntuforums.org/showthread.php?t=1107617")
I think VMware Workstation supports native virtualization, too. And it supports DirectX up to 9.0c.

---

