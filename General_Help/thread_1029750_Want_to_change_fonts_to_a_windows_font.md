---
title: "Want to change fonts to a windows font"
date: 2009-01-03
forum: General Help
---

### Post by Secret Neo on 2009-01-03
I'd like to change the system fonts to the fonts being used in windows. so how do i install fonts and how can i change the fonts?

---

### Post by namdung on 2009-01-03
Microsoft fonts are available in Ubuntu repository.
```
sudo apt-get install msttcorefonts
```

Fonts can also be easily installed by copying the fonts files to the following folder
***/usr/share/fonts***

Ubuntu will automatically detect the installed fonts and use it.

---

### Post by steveneddy on 2009-01-03
> **namdung said:**
> Microsoft fonts are available in Ubuntu repository.
```
sudo apt-get install msttcorefonts
```Fonts can also be easily installed by copying the fonts files to the following folder
***/usr/share/fonts***

Ubuntu will automatically detect the installed fonts and use it.

Totally correct.

I just wanted to add that you can add fonts for an individual user in the 

**.fonts**

folder, which is located in the /home folder.

I am generally the only user on my laptop and I choose to install fonts in .fonts because if I reinstall I can back up /home and still have all of my fonts.

---

### Post by Secret Neo on 2009-01-03
thx guys i did that but i wanna install a font now and i cant put it into the fonts folder, whenver i try to move it there it says permission denied.:(

---

### Post by chamber on 2009-01-03
Do as steveneddy said,

Just download the fonts, open the home folder hit ctrl + H to see all the hidden files and put the fonts in the .fonts folder.

Easy as.

---

### Post by Secret Neo on 2009-01-03
i opened my home folder and pressed ctrl-h and there is no.fonts folder, theres .fontconfig tho.

---

### Post by chamber on 2009-01-03
You can create the folder and then put fonts into it.

Thats how I get fonts for my conky scripts.

just make sure to name it .fonts.

---

### Post by namdung on 2009-01-03
> **Secret Neo said:**
> thx guys i did that but i wanna install a font now and i cant put it into the fonts folder, whenver i try to move it there it says permission denied.:(

Please use the sudo command for any file modifications outside ur home folder.

```
sudo mv *.ttf /usr/share/fonts
```

The code will move (mv) all fonts file in the given directory to the fonts folder. You may also use a copy option (cp). Pls remember that file names in Linux is case sensitive.

Also, the other easier way is to make a folder (if not already available) **.fonts** in ur *Home* directory and copy the fonts file. But this font will only be available to u.

---

