---
title: "Installation problems again"
date: 2006-05-12
forum: Desktop Environments
---

### Post by christoforever on 2006-05-12
hey guys i posted yesterday but with the help, i've still gotten no where. I'm trying to install the java sdk along with netbeans bundle. it is a .bin file. when i click the file it opens with gedit, and then gives me this message:

gedit was not able to automatically detect the character coding. Please, check that you are not trying to open a binary file and try again selecting a character coding in the 'Open File...' (or 'Open Location') dialog.

I also changed the permissions to execute the file, but still i get the same message. does anyone know what to do?

---

### Post by Omnios on 2006-05-12
First of all Ubuntu does not nessasserily run exicutables by clicking on them. You might want to try using the terminal, cd to the directory you have the exacutable in and type. sudo .filename or ./filename pertaing to what works. The .filename will run the exacutable.

---

### Post by depu on 2006-05-12
u have to first convert the .bin into an executable file use the terminal to go to the folder where u have the .bin file then
chmod +x filename.bin
then u need to have fakeroot installed to go ahead so
sudo apt-get install fakeroot java-package java-common
once u got those do
fakeroot make-jpkg filename.bin
this makes a .deb file in the same folder as in .bin then simply
sudo dpkg -i filename.deb
since u are installing the Sun java version u'll also have to do
sudo update-alternatives --config java
and select the option with sun mentioned in it (i think it was third in mine) do the same command for jar replace java in the above command by jar. 
If this doesnt help go check out the wiki at
[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

---

