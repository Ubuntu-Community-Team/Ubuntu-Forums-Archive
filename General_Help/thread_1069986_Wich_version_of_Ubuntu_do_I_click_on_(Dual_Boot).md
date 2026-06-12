---
title: "Wich version of Ubuntu do I click on? (Dual Boot)"
date: 2009-02-14
forum: General Help
---

### Post by JimBuntu on 2009-02-14
I recently got Ubuntu working again on my dual boot laptop. However, when I start it up there are three different Ubuntu's and there recovery mode's that I can select along with Windows XP. I have been selecting the top one but the number seems not to be the highest one. Which one should I select? They are all 8.10 but there are some numbers along with each one that are all different. Which one should I select?

---

### Post by m_duck on 2009-02-14
The top one is probably best if everything seems to be working as it should be the newest one. Ubuntu leaves the old kernels in your grub config so if a kernel upgrade breaks your wireless (for example) you can boot using one of the old kernels so it works so you can find out how to fix it etc.

---

### Post by JimBuntu on 2009-02-14
Ok, thats what I figured. the only thing is that the highest one is not the highest number. The middle one has the highest number.

---

### Post by m_duck on 2009-02-14
Hmm, thats weird. I've no idea then, sorry. Unless of course you've editted the menu.lst yourself at some point to move one to the top and after a kernel update, Ubuntu has put the newest one at the top of the "Automagic kernels" bit, but still under your edit? Failing that, not the foggiest!

---

### Post by JimBuntu on 2009-02-14
Ok, thanks man. I will reboot later and try to write down exactly what it says and post it. Thanks though.

---

### Post by mb_webguy on 2009-02-14
You can edit the GRUB menu (such as to remove some of the older kernels listed) by changing options in the /boot/grub/menu.lst file.  

Or if you prefer to use a windowed application, install the startupmanager package.  This will show up as Start-Up Manager in the System->Adminstration menu.

---

