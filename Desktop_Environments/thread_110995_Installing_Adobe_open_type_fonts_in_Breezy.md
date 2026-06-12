---
title: "Installing Adobe open type fonts in Breezy"
date: 2006-01-01
forum: Desktop Environments
---

### Post by gpierce on 2006-01-01
Hello,

I have a CD with the whole Adobe Font Folio (Open Type Edition). I am uncertain as to how to install them so that applications like Open Office and firefox can see them. I have tried creating a directory .font in my home directory but that doesn't seem to work. I fear that I may have to edit my xorg.conf, but I am really quite unsure. Any help would be appreciated.

Greg

---

### Post by mcduck on 2006-01-01
they should be in .fonts directory under your home dir.

---

### Post by kaamos on 2006-01-01
If you create a directory .fonts, you wont be able to see it right away. Directories starting with a dot are hidden and can be made visible by pressing ctrl+h

Copy the fonts to /home/yourusername/.fonts and run this command in terminal```
fc-cache -fv
```

---

### Post by gpierce on 2006-01-01
[QUOTE=mcduck]they should be in .fonts directory under your home dir.[/QUOTE]

I've tried this already and they still are not available. I have them in /home/gpierce/.fonts. Is this what you meant?

---

### Post by gpierce on 2006-01-01
[QUOTE=kaamos]If you create a directory .fonts, you wont be able to see it right away. Directories starting with a dot are hidden and can be made visible by pressing ctrl+h

Copy the fonts to /home/yourusername/.fonts and run this command in terminal```
fc-cache -fv
```[/QUOTE]

Thanks, but still don't see them in OO.o.  Could it be that open type fonts just aren't supported? I will go to the OO.o web site and see if there is anything posted on this.

Greg

---

### Post by gpierce on 2006-01-01
Ok, well it seems the fonts are accessible from within other applications such as Evolution, but not Open Office. Looking in the online forums on openoffice.org, I found this [http://www.oooforum.org/forum/viewtopic.phtml?p=115084](http://www.oooforum.org/forum/viewtopic.phtml?p=115084). So it seems I am not the only one.

Greg

---

