---
title: "Cockatrice install ubuntu 12.04"
date: 2012-12-23
forum: Gaming &amp; Leisure
---

### Post by googeek on 2012-12-23
Hey there ya'll. It took me ages to figure out this code, so I thought I'd share it. It's a splicing from the original cockatrice site and a helpful blogger. If you are a total newbie, the numbers represent the lines, add each one at a time to your terminal. To paste into terminal hit Shift+ctrl+v.

```
 
sudo apt-get install build-essential
git libqt4-dev qtmobility-dev libprotobuf-dev protobuf-compiler cmake
cd git clone
git://github.com/mbruker/Cockatrice.git
cd Cockatrice
cmake .
make
sudo make install

```
[LIST]
[*]Open the Cockatrice directory(folder) in the home directory.
[*] Open the oracle directory.
[*] Run the oracle app by double clicking.
[*] Click file> Download sets information.
[*] Select any and all sets you want and click Start download.
[*] Wait for it to finish and close.
[*] Go up one directory, open cockatrice directory.
[*]Run the cockatrice app by double clicking.
[/LIST]
  Once you log out and login again Cockatrice will be in your menu.
 ENJOY! :)

---

### Post by lisati on 2012-12-23
I've edited your post to use the default font size, in keeping with the forum code of conduct. Is the formatting correct?

---

### Post by googeek on 2012-12-23
MY bad! I just pasted from a document. :/ Thanks!

---

### Post by dcosiem on 2013-02-10
Hi, your second line doesn't work. Please help

> danny@danny-Inspiron-1720:~$ git libqt4-dev qtmobility-dev libprotobuf-dev protobuf-compiler cmake
git: 'libqt4-dev' is not a git command. See 'git --help'.

---

