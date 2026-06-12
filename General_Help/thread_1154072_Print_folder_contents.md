---
title: "Print folder contents"
date: 2009-05-09
forum: General Help
---

### Post by accooper on 2009-05-09
Does anyone know of a program that will allow me to print the out the contents of a folder?

:guitar:

Andrew

---

### Post by StOoZ on 2009-05-09
just list them all to a file and then send it to the printer for printing... in case thats what you're after

---

### Post by todak on 2009-05-09
```
ls /folder/folder > file_list.txt
``` will spit out a list into your home directory of all files in that particular folder. For instance, ```
ls /home/dave/Downloads > files.txt
``` gives me a text file of ```
dban-1.0.7_i386.exe
DVD Identifier 5.2.0 Setup [Database.10-JAN-09].exe
DVDShrink32.exe
ebook2cw
EP2009.04.10.mp3
Icom
Image_wizard_advanced.py
KochMorseTrainer Install.exe
pmagic-4.1.iso.zip
Scribus Image Assistant.py
stylus-toolbox_0.2.7-1_all.deb
truecrypt-6.1a-ubuntu-x86.tar.gz
vx2cmd111.zip
webcore-fonts_3.0-2_all.deb
``` which is a list of all the files and subfolders in my Downloads folder. I can then either print them out, or just browse through the list to see what I have. ```
ls -R /home/dave/Downloads > files.txt
``` will create a list of all files in all subfolders of my Downloads directory. ```
man ls
``` for more examples.

---

