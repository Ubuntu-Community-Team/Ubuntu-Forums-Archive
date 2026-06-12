---
title: "Openoffice fonts tar.gz files installation"
date: 2005-12-02
forum: Desktop Environments
---

### Post by pfabrikant on 2005-12-02
Hey,
I got Breezy Badger 5.1 a week ago and I don't really have a clue how things work.. But I really want to learn ! 
My openoffice just wont recognize hebrew fonts ( when loading existing *.doc or *.odt that I saved from Windows) and when I print a new document, the courser moves but there is nothing being written down. I don't really know how to install tar.gz files ( I downloaded some debian packages that should contain hebrew fonts). Should I download something else ? I enabled Hebrew language support, I have hebrew typing working in Linux but not inside Openoffice writer documents..
Also, The synaptic package manager doesn't recognize any of those tar.gz files as installable files. Why ?
Thanks a lot, and forgive me for the absolute abscence of any knowledge..
Eli

---

### Post by welsh_spud on 2005-12-02
To install the .deb file open up a terminal, change to the directory where the deb file is and type:

```
sudo dpkg -i <name>.deb
```

that should install whatever is in the deb. Note that if the deb wasn't made for Ubuntu, it may mess your system up. Be warned.

On a side note, if you find any hebrew fonts as a .ttf file, you can just put them  in /usr/share/fonts

After a quick google here are some hebrew fonts (i think...)

[http://www.student.northpark.edu/pemente/hebfonts.htm](http://www.student.northpark.edu/pemente/hebfonts.htm)

Normaly you wouldn't be able to just drag the font.ttf file to /usr/share/fonts because you don't have the user rights to do so, however there is a method I use to install fonts.

Open nautilus with sudo

```
sudo nautilus
```

this will bring up a file manager window that has root access. After that you can copy the fonts on your desktop to /usr/share/fonts

---

### Post by Silver Strike on 2005-12-02
For hebrew support (on all linux distributions) you can install the culmus package:
```
sudo apt-get install culmus
```
Although it seems that you already have that support natively.

The issue (as I see it) is that your document uses the "Arial" font (or any other font that's not installd on your system). In this case you have two options:
[LIST=1]
[*]Install the missing fonts manually (as welsh_spud wrote).
[*]Change the font the document uses to any hebrew font (like "Nachlieli CLM" or "FreeSans").
[/LIST]

Good luck :)

---

