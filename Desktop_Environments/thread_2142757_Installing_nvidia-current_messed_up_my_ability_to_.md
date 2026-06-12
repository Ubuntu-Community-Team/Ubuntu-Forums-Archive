---
title: "Installing nvidia-current messed up my ability to run compiz?"
date: 2013-05-06
forum: Desktop Environments
---

### Post by GammaPoint on 2013-05-06
Hi all,

I just upgraded to 13.04 Xubuntu and was messing with getting Compiz working. It was working just fine for me (cube rotation was there, key commands, etc) except for the fact that wobbly windows was not working. From some website I got the idea that installing nvidia-current would fix my problem so I tried 'sudo apt-get install nvidia-current'. However, this broke everything and I couldn't have compiz running without all my windows being frozen (can't drag them at all). If I turn off compiz I can move them again. However, I want to get back to where I was before I installed nvidia-current, since Compiz *mostly* worked back in those good ol' days (an hour ago). 'apt-get purge nvidia-current' *should* remove that package I think, but it seems that my problem still exists.

Is anyone familiar with this problem or what I might be able to do to get back to where I started? I don't know if doing this modified some setting somewhere that I need to now go back manually and fix. 

Thanks for any input you can give!

---

### Post by GammaPoint on 2013-05-06
Just to say, my compiz option of 'move windows' is in fact selected, so that's apparently not the issue.

---

### Post by papibe on 2013-05-06
Hi GammaPoint.

Could you post the result of these commands?
```
lspci -nnk | grep -iA2 vga

apt-get policy nvidia-current

lsmod | grep nvidia
```
Regards.

---

