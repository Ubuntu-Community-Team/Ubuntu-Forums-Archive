---
title: "Ubuntu removed WinXP from GRUB! Can't get back to Windows"
date: 2006-08-08
forum: Desktop Environments
---

### Post by infiniti029 on 2006-08-08
I did a software update in Ubuntu, rebooted, and WinXP is no longer on my GRUB menu. Instead it was replaced by Ubuntu again! I know WinXP was either on HD(0,1) or HD(0,0). What do I put on the rest of the lines in the menu.lst file?

(I think I might have posted in the wrong catagory, sry.)

---

### Post by KillerKiwi on 2006-08-08
heres a nsippet from my grub (/boot/grub/menu.lst) its the last entry in the file
Help on grub [https://wiki.ubuntu.com/?action=fullsearch&context=180&value=grub&titlesearch=Titles](https://wiki.ubuntu.com/?action=fullsearch&context=180&value=grub&titlesearch=Titles)



```

title		Microsoft Windows XP Tablet PC Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

---

### Post by aceracer24 on 2006-08-08
Similar but differant problem. The windows XP config is still in menu.lst, but I had some funky stuff happen and Ubuntu crashed..sorta. Anyway, I loaded back into ubuntu and the link for windows partition was gone. I didn't think much of it until now...when I select windows XP partition from grub, it says something like unknown file type and I get a simple :

grub> 

but I can't type anything. Umm...what to do now?

---

