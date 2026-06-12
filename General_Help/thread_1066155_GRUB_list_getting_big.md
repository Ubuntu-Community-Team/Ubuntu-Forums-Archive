---
title: "GRUB list getting big"
date: 2009-02-10
forum: General Help
---

### Post by kdiggity317 on 2009-02-10
Im still kinda new to ubuntu but i have been able to work through most of my issues with dual boot with XP. One thing I notice is that when I get some updates it adds a new version number in my GRUB booter. Now it doesnt take much to edit the gurb so it boots to XP like it should, but I would like to get some of the older version numbers out of there cuz its just getting to be a pretty big list. Is there anyway I can get those ones I dont use to not show up? Thanks for the help.

---

### Post by pssturges on 2009-02-10
Easiest way is to install startup-manager from add/remove programs. This is basically a gui for editing all the grub options.

On the "Advanced" tab is a check box to "Limit the number of kernels in the boot menu". Check that, then specify how many want to keep. I recoment you keep at least 2 or 3 in case of problems after an upgrade.

Cheers
Phil

---

### Post by kdiggity317 on 2009-02-11
Okay that sounds good. The only question I have about that is can I select the ones I want to keep? Like I said Im dual booting and need to make sure the Windows XP is my default and is still there. So I need to make sure that I can get some of the middle versions out with out touching the top or the bottom.

---

### Post by mb_webguy on 2009-02-11
The setting mentioned by pssturges only affects Linux kernels.  Your Windows entry shouldn't be touched.

---

