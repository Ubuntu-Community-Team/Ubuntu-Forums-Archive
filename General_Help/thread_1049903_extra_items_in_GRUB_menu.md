---
title: "extra items in GRUB menu"
date: 2009-01-25
forum: General Help
---

### Post by akh00 on 2009-01-25
I'm using Ubuntu 8.04 and Windows 7 beta in dual mode. After updating Ubuntu once, I noticed that the Ubuntu items in the GRUB list became doubled. So now I have two ubuntu items in the GRUB menu along with windows 7. how do i remove these extra items?

---

### Post by Despot Despondency on 2009-01-25
You could use a program such a gparted to reformat your hard drive. You should be able to delete the unwanted version of ubuntu and allocate the extra space to your other distributions. I think anyway, been a while since I've used gparted.

---

### Post by mb_webguy on 2009-01-25
Whoa, whoa, whoa!  Don't do any reformatting!  (Bad Despot Despondency!  Bad!  No cookie for you!)

What you're seeing is different kernels.  THIS IS NORMAL!  With the default GRUB settings, whenever the kernel is updated, an entry is added for the new kernel and the old ones are kept, so you have the option to boot into an older kernel if the new one causes problems for some reason.

If you don't want to see this, you can edit the GRUB menu.lst (using "gksudo gedit /boot/grub/menu.lst", and you should really save a backup copy before making any changes) to change the number of entries shown.  Here's the section you're looking for:```
## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

```
If you don't want to see the additional entries, change the line that says "# howmany=all" to "# howmany=1".  You can also change other settings in the GRUB menu if you want, such as adding colors to the menu or password-protecting entries.

Once you've made the changes and saved the file, you need to enter the command "sudo update-grub" to make the changes to the GRUB menu.

---

### Post by Montblanc_Kupo on 2009-01-25
For safety sake I would suggest making a backup of the menu.lst file first... and in fact, it's not a terrible idea if you're paradoid to copy it to an external device like a jump drive.

---

### Post by Despot Despondency on 2009-01-26
Wow, sorry. I thought there were multiple installations of ubuntu of his computer. That's how I got rid of them when I did that. Sorry again.

---

