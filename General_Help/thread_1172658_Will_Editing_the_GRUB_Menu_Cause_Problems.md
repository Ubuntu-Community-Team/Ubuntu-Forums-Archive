---
title: "Will Editing the GRUB Menu Cause Problems?"
date: 2009-05-28
forum: General Help
---

### Post by ntowakbh on 2009-05-28
I want to edit the GRUB menu.  However, will editing it cause problems when I get a kernel update, such as will it make it difficult for Ubuntu to add the latest boot option?  I want to add a few lines just before the operating systems entries.

---

### Post by michy99 on 2009-05-28
I think you are safe as long as you put them before the line that says:```
### BEGIN AUTOMAGIC KERNELS LIST
```

---

### Post by ntowakbh on 2009-05-28
> **michy99 said:**
> I think you are safe as long as you put them before the line that says:```
### BEGIN AUTOMAGIC KERNELS LIST
```

Many thanks!

---

### Post by 73ckn797 on 2009-05-28
The only changes that I have ever made were with designating which line to default to for booting and I have inserted descriptions to know whether I am booting into a 32 or 64 bit kernel or using the ext3 or 4 file system from the grub menu.

See example:
```
title        Ubuntu 9.04 64bit Ext4, kernel 2.6.28-11-generic
```

---

