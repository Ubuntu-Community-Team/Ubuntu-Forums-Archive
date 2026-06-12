---
title: "How to install downloads"
date: 2005-03-18
forum: Desktop Environments
---

### Post by livingword26 on 2005-03-18
I have tried fedora, and Mandrake. Now I am on Ubuntu. One thing about linux I can't figure out is how to install a program you download from the internet, such as a web browser. Windows has a program that installs it and places a shortcut on the start menu to run this program. With linux when you download the program it shows you all the folders in the download but doesn't install it. Can anyone tell me , from the beginning, how to install a program? ](*,)

---

### Post by bored2k on 2005-03-18
[QUOTE=livingword26]I have tried fedora, and Mandrake. Now I am on Ubuntu. One thing about linux I can't figure out is how to install a program you download from the internet, such as a web browser. Windows has a program that installs it and places a shortcut on the start menu to run this program. With linux when you download the program it shows you all the folders in the download but doesn't install it. Can anyone tell me , from the beginning, how to install a program? ](*,)[/QUOTE]
 If the extension is .bin
chmod 755 ; sh filename.bin or sudo sh filename.bin 

If it is .rpm
sudo alien -d filename.rpm; dpkg -i filename.deb

If it is .deb
sudo dpkg -i filename.deb

If it is a .gz file
tar xzf filename.gz
then inside that dir if the app is .py python filename.py or sh filename.sh or java -jar filename.jar

If its a .gz to compile, you do
./configure
make
sudo make insall
 
all this in terminal

If errors pop, likely your in depedencies problems or different gcc versions .

---

### Post by livingword26 on 2005-03-19
1. Download firefox-1.0.1.installer.tar.gz.
2. From terminal type in:    
"tar zxf firefox-1.0.1.installer.tar.gz"  
3. Terminal answers: Cannot open: No such file or directory

---

### Post by bored2k on 2005-03-19
[QUOTE=livingword26]1. Download firefox-1.0.1.installer.tar.gz.
2. From terminal type in:    
"tar zxf firefox-1.0.1.installer.tar.gz"  
3. Terminal answers: Cannot open: No such file or directory[/QUOTE]
 it is not zxf its 
tar xzf

and no such file means your not in the dir it was downloaded ...

type ls, if you see the file, its ok, if not, youre not ok.

---

### Post by livingword26 on 2005-03-19
Typed in as described above. No message just new prompt. 
Contents of firefox-installer that was downloaded:
xpi
config.ini
firefox-installer
firefox-installer-bin
header.png
install.ini
license.txt
watermark.png

---

### Post by TravisNewman on 2005-03-19
[QUOTE=bored2k]it is not zxf its 
tar xzf

[/QUOTE]
Doesn't matter, I've always used zxf

---

### Post by bored2k on 2005-03-19
[QUOTE=panickedthumb]Doesn't matter, I've always used zxf[/QUOTE]
 Oh my bad then.

---

### Post by Jad on 2005-03-19
If you go over Ubuntuguide.org and install some of the software mentioned their, you will be somehow familiar with How to install X or Y...
its easy
What I have problem with is, if Y needed a blah.lib.2 and I have blah.lib.3 How to install the old one to get the application works?

---

### Post by TravisNewman on 2005-03-19
Usually just install it. Most things in my experience can share the drive with older/newer versions.

---

