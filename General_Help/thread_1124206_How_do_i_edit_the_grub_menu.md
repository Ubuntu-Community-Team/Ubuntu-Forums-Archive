---
title: "How do i edit the grub menu?"
date: 2009-04-13
forum: General Help
---

### Post by Macfunky on 2009-04-13
I have recently installed Ubuntu on my parents computer so when i come home i can do work on it rather than working on Windows. I have installed it on its own partition. Problem is my parents get easily confused with computers and when i turn it on by default, unless you scroll down and pick windows XP, it will boot into Ubuntu. Doesn't seem like the hardest thing in the world to do but my parents keep forgetting this so i would like to find out how to edit the grub menu so that by default it will choose Windows XP and boot that up unless otherwise instructed to do so. Can anyone help me out? Thanks

---

### Post by sahabcse on 2009-04-13
Hi 

Type the below command in terminal and It will open the grub menu file. Then u can edit the file. 

#sudo gedit /boot/grub/menu.lst

---

### Post by hyper_ch on 2009-04-13
you need to edit the /boot/grub/menu.lst file

---

### Post by zika on 2009-04-13
> **Macfunky said:**
> I have recently installed Ubuntu on my parents computer so when i come home i can do work on it rather than working on Windows. I have installed it on its own partition. Problem is my parents get easily confused with computers and when i turn it on by default, unless you scroll down and pick windows XP, it will boot into Ubuntu. Doesn't seem like the hardest thing in the world to do but my parents keep forgetting this so i would like to find out how to edit the grub menu so that by default it will choose Windows XP and boot that up unless otherwise instructed to do so. Can anyone help me out? Thanks
You might find useful Start-Up Manager for that. ("startupmanager" in Synaptic or "sudo apt-get install startupmanager" in Terminal)

---

### Post by Aubergines on 2009-04-13
just edit /boot/grub/menu.lst

There's a line a the top of file
```
default 0
```
This corresponds to the boot options nearer the bottom of the file. Each boot option starts with "title". The first boot option is 0 and they count up from there. So if Windows is 3rd boot option you'll change.
```
default 2
```

---

### Post by logic++ on 2009-04-13
> **zika said:**
> You might find useful Start-Up Manager for that. ("startupmanager" in Synaptic or "sudo apt-get install startupmanager" in Terminal)

You should use this instead of messing with the grub menu file.

---

