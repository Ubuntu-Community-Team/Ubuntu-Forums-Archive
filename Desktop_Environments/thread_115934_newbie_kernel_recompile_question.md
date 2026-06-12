---
title: "newbie kernel recompile question"
date: 2006-01-11
forum: Desktop Environments
---

### Post by nwcowboysfan on 2006-01-11
this is my first post, so I hope I am posting in the correct section...

I recently tried to recompile my kernel to take advantage of suspend2 since suspend and hibernate were not working correctly on my laptop. Everything went according to plan, except when I rebooted it used the old kernel. I see the problem but am not quite sure how to correct it. This is what is listed in my /boot directory:

abi-2.6.12-10-386        initrd.img-2.6.12-10-386     vmlinuz-2.6.12-10-386
config-2.6.12-10-386     memtest86+.bin               vmlinuz-2.6.12-hibernate
config-2.6.12-hibernate  System.map-2.6.12-10-386
grub                     System.map-2.6.12-hibernate

Secondly, if I screwed something up in the compile will I be able to load the old kernel?

Thanks for any help!

---

### Post by 23meg on 2006-01-11
Did the new kernel not appear in the GRUB boot menu? As long as you don't uninstall the old kernel you can boot with it. 

You may also find help in [this thread]("http://www.ubuntuforums.org/showthread.php?t=85064").

---

### Post by nwcowboysfan on 2006-01-11
nope...only the old kernel version appeared.

---

### Post by 23meg on 2006-01-11
Did you get any error messages when you attempted to install your kernel package with dpkg?

---

### Post by nwcowboysfan on 2006-01-11
hmmmm...that would probably be the problem. how do you install the kernel with dpkg?

---

### Post by 23meg on 2006-01-11
Once you've compiled your kernel image you have to install it with ```
sudo dpkg -i /path/to/file
```and then it will become available in the GRUB menu as an option, assuming you did everything else right. I suggest you read the guide I linked to in my first post if you haven't.

---

### Post by nwcowboysfan on 2006-01-11
thank you so much! I totaly missed seeing the link you provided in the earlier post. I looked for such a guide before I started this post but could not find it for some reason.

this kind of community help is what makes linux/ubuntu so great!

---

### Post by 23meg on 2006-01-11
Cool, I hope you get it sorted out. Remember to always do a search (see my signature) before asking a question; you're almost guaranteed to reach solutions faster that way.

---

