---
title: "Computer monitor is flickering when i am using Ubuntu 6.."
date: 2006-12-08
forum: Desktop Environments
---

### Post by hm_naveen on 2006-12-08
hi,
I installed latest Ubuntu OS in to my personal computer. I am really happy with this Linux falvour. But when i am using my computer with Ubuntu computer monitor is flickering very much. Please help me to resolve this issue. 
I will be waiting for your kind help...

---

### Post by studiesrule on 2006-12-08
It would be nice if you told me your version and sys specs, especially your gfx card.

For the third time in 20 minutes, i shall be suggesting this fix (I think it's the only thing i know actually). As a generic solution, whenever you have gfx problems, then enter terminal mode, alt + ctrl + F2, login and type:
sudo dpkg-reconfigure xserver-xorg
follow the steps
If this doesnt' immediately work, do it again, and when it comes to the drivers section, choose vesa, which almost always works. Then you can expreriment with the other drivers that seem to fit your gfx card name.

---

