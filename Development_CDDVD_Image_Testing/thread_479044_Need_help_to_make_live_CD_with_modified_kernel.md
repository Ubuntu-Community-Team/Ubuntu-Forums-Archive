---
title: "Need help to make live CD with modified kernel"
date: 2007-06-19
forum: Development CD/DVD Image Testing
---

### Post by lavinaz on 2007-06-19
Hi,

Currently, I have to modify 2.6.10 kernel for my project and must create a Live CD using that kernel. 

Some available guidelines can only install new programs into an existing live cd. Someone please help me. Thanks.

---

### Post by smartboyathome on 2007-06-20
I think you will have to do this the old fashioned way - by following the instructions on this page:
[https://help.ubuntu.com/community/LiveCDCustomization?highlight=%28livecd%29](https://help.ubuntu.com/community/LiveCDCustomization?highlight=%28livecd%29)
Uck won't do this, neither will Reconstructor. So that seems like the only option.

---

### Post by lavinaz on 2007-06-25
Thanks for the link.

I have  successfully created the LiveCD with squashfs for 6.06 LiveCD. However, 5.0.4 LiveCd uses cloop to compress the file system. Do you have any guideline for that?

---

### Post by smartboyathome on 2007-06-25
I would not know of anything for cloop. Try Wikipedia :)! I would suggest that you stick with a newer distro (5.04 is no longer supported, and from what I heard, doesn't have any repos anymore), though.

---

