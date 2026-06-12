---
title: "[SOLVED] Gfxboot Broken after Switch to Separate Boot Partition"
date: 2007-11-04
forum: Desktop Effects &amp; Customization
---

### Post by coldstatue on 2007-11-04
Hey all. Switched to a separate boot partition in preparation for the Gutsy upgrade. All is well except my gfxboot. I reinstalled per the how to here in the forums, but it's no good. After searching long and hard, I found a site where someone updated the menu.lst path for their gfx message.whatever. 

They did it like so

gfxmenu (hd1,6)/grub/message.blusplash

That is actually from my menu.lst, but I did it in the same format they did.

I still get the black GRUB screen with white selections in the upper-left.

Any help?

I have scoured through the gfxboot how to, and I found some people saying that you can fix this by installing the AMD64 deb of gfx boot. What? I *can't* install that. 

Thanks.

EDIT: I have done this after changes

sudo grub
find /grub/stage1
root (hd1,6)
setup (hd0)
quit

---

### Post by coldstatue on 2007-11-05
Got it. after:
sudo grub
find /grub/stage1
root (hd1,6)
setup (hd0)
quit

do 

sudo grub-install hdx,x

Use the same one you used for root, without parentheses.

My menu.lst entry was correct. 




Hope this thread helps someone. There are literally hundreds of pages of gfxboot issues in this forum, and many in there who are having this same issue, with no answer. It took a lot of searching and fiddling around.

If you are really new to linux, know that hd1,6 will be differnt for you! Use the gfx how to first!!!

---

