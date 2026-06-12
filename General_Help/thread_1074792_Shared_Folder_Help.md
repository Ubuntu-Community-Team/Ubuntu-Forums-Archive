---
title: "Shared Folder Help"
date: 2009-02-19
forum: General Help
---

### Post by Indyviews on 2009-02-19
My host is Ubuntu 8.10 and the Virtual OS is Windows 2000. I wish to have one folder titled "Images" on 2000 Desktop containing scanned images and to be able to access or move them to Unbuntu. (scanner won't work on Unbuntu)  I have made a folder on Unbuntu titled "Shared2" at home/steve/shared2.

I have enabled file sharing and done my best when enabling shared folders on Virtualbox and 2000 and this includes all types of Network paths on both. I am sure this is not the correct terminology. 

In the manual I read about the guest obtaining files from the host but not the other way around and also there is a bug that hinders this. I have seamless mouse, full size window, and my usb scanner works.

Could someone go through this step by step for me. I think my problem is with 2000 when I work with 'Network places'. After adding a Network place, nothing shows up on Ubutu network. If I click on what I made in 2000, it says \\VBOXSVR\shared2 is not accessible. This folder was moved or removed.

Thanks for any help.

---

### Post by dcstar on 2009-02-19
> **Indyviews said:**
> My host is Ubuntu 8.10 and the Virtual OS is Windows 2000. I wish to have one folder titled "Images" on 2000 Desktop containing scanned images and to be able to access or move them to Unbuntu. (scanner won't work on Unbuntu)  I have made a folder on Unbuntu titled "Shared2" at home/steve/shared2.
........
Could someone go through this step by step for me. I think my problem is with 2000 when I work with 'Network places'. After adding a Network place, nothing shows up on Ubutu network. If I click on what I made in 2000, it says \\VBOXSVR\shared2 is not accessible. This folder was moved or removed.

Thanks for any help.

For basic Samba/Windows filesharing to work then the host and VM have to be on the same IP subnet, you need to check if your Windows 2000 VM is in the same IP range as your host.

---

