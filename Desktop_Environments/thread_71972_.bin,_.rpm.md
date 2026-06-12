---
title: "*.bin, *.rpm"
date: 2005-10-04
forum: Desktop Environments
---

### Post by seismicmike on 2005-10-04
In my limited experience with linux, I have figured out how to install files that are *.tar.gz, now I just need to figure out how to install files that are *.bin or *.rpm. Any suggestions?

---

### Post by 23meg on 2005-10-04
.bin files are executables that can be run in x by double clicking or in the terminal by typing their name; they don't need installation (as long as they aren't installers themselves). 

.rpm files are packaged in red hat's package standard, rpm, and can be converted to .deb files (debian/ubuntu packages) by using the "alien" command. to convert them, first install alien by typing "sudo apt-get install alien" if it isn't installed on your system, then type "sudo alien [filename]" to produce a .deb package in the same folder. you can then install the .deb by typing "sudo dpkg -i [filename]".

---

### Post by az on 2005-10-05
> **23meg].bin files are executables that can be run in x by double clicking or in the terminal by typing their name said:**
> " to produce a .deb package in the same folder. you can then install the .deb by typing "sudo dpkg -i [filename]".


... or just

sudo alien -i (package.rpm)
To just install it..

---

### Post by seismicmike on 2005-10-05
SWEET! Thanks guys!

---

### Post by seismicmike on 2005-10-05
er... so after I do that... how do I run the program I just installed... ie: where's the executable?

---

### Post by migo on 2005-11-18
[QUOTE=23meg].bin files are executables that can be run in x by double clicking or in the terminal by typing their name; they don't need installation (as long as they aren't installers themselves). 
.[/QUOTE]

This isn't working for me, any other way to do it?

---

### Post by Pablo_Escobar on 2005-11-18
With bin, You have to set executable mask for the file.
Easy way:
Cd to the directory the file is in
chmod +x nameofthefile.bin
./nameofthefile.bin

Or rightclick it -> Properties -> 3rd tab and tick on the execute flag in users.
Then doubleclick it.

---

### Post by migo on 2005-11-18
Thanks!

---

