---
title: "Grub not Counting Down"
date: 2009-04-19
forum: General Help
---

### Post by itsonlybarney on 2009-04-19
I recently installed Xubuntu on my spare laptop computer, and when I start the computer, the computer doesn't get past the Grub menu, unless I manually choose the Kernel I want to use. 

Basically, it gets to the screen where the countdown occurs, but the countdown doesn't actually go down, and the only way to start Xubuntu is to actually hit the 'Esc' key, and then manually select the correct kernel. I'd rather not do that, I can post my menu.lst file if you want, but it looks identical to another computer where it works fine using the exact same options.

Any possible ideas and help would be appreciated.

---

### Post by meierfra. on 2009-04-19
See what happens if you replace  the battery in your motherboard.

---

### Post by spcwingo on 2009-04-19
Could you post your menu.lst.  It's under /boot/grub/menu.lst.  It could be something as simple as no default entry or no timeout, etc.

---

### Post by itsonlybarney on 2009-04-19
Not sure what I did, but I installed some updates, and it now seems to be working, not sure what the problem or difference is. 

But works now.

---

