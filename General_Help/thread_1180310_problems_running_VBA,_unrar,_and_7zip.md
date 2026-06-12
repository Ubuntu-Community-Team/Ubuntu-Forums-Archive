---
title: "problems running VBA, unrar, and 7zip"
date: 2009-06-06
forum: General Help
---

### Post by adamspurgin on 2009-06-06
i got visualboyadvance, unrar, and 7zip from the package manager. they installed, but i can't find out how to run any of them. they're not in the application menu, i try running the files in the /usr/bin file, and nothing happens. I'm still kinda new to this.

---

### Post by michy99 on 2009-06-06
unrar and 7zip are command-line programs, but the Archive Manager in Applications->Accessories provides a graphical interface to them and other archive programs you have installed. To learn how to use them from the command line, enter these commands in a terminal:```
man unrar
man 7zip
```Try it for visualboyadvance,too. I don't know anything about that one.

---

### Post by adamspurgin on 2009-06-06
well, i'm not sure how it happened, but after a restart everything started working.

---

### Post by Legace on 2009-06-06
Unrar provides the ability to extract RAR archives. To do so, right-click on a RAR file and select "Extract here".

7zip should provide ability to create (and extract) a .7z archive.

---

### Post by kvarley on 2009-06-06
If you are extracting .rar archives then you will need "unrar" do you have this?

Code to install unrar:
> sudo apt-get install unrar

Code to extract all files:
> unrar e nameofpackage.rar

Hope this helps.

---

