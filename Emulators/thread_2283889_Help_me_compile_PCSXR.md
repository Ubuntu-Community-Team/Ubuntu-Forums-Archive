---
title: "Help me compile PCSXR"
date: 2015-06-25
forum: Emulators
---

### Post by kilua3 on 2015-06-25
So yesterday I had a trouble with the PCSXR playing games so I decided that I should download the source code and compile my self so that the pete's plugins could work.

The instructions are very simple ./configure;make;make install, however when I do ./configure it tells me there no such files with that name?

Any help would be apreciated.

P.S:Using last source code availble and I already try to do the same with 1.9.9.3.

Edit:Solved the problem.
For anyone who has the same problem do this commands:
[I]sudo apt-get install subversion autoconf intltool libtool libsdl1.2-dev libgtk-3-dev libxv-dev libxtst-dev nasm
[I]cd pcsxr/
[I]./autogen.sh
[I]./configure
[I]make
[I]sudo make install
(cd pcsxr/ is the dir where you extracted the source code)[/I][/I][/I][/I][/I][/I]

---

### Post by coldraven on 2015-06-25
Are you running the./configure in the correct directory? You can check where you are with ```
pwd
```
then if the folder with the files is in /home/your_username/foobar do
```
cd /home/your_username/foobar
```
then try again with
```
./configure
```

---

