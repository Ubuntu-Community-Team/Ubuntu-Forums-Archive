---
title: "How to make UCK remastered ISO UEFI-bootable?"
date: 2015-11-01
forum: Development CD/DVD Image Testing
---

### Post by ed-agoff on 2015-11-01
I am using UCK (Ubuntu Customization Kit) to customize xubuntu-14.04.1-desktop-amd64.iso and it works great, except the remastered ISO is not UEFI-bootable. How can I add UEFI boot support to the remastered ISO? 


Thanks and best regards,


Ed

---

### Post by leo_remick on 2015-11-05
Not sure if UCK's generated iso is UEFI ready by default... have you tried -->

isohybrid --uefi $ISO

if the image is not uefi it will say something along the lines of "can't find boot file"

---

