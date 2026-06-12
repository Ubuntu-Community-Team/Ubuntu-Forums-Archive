---
title: "help with packages instalation"
date: 2006-05-08
forum: Desktop Environments
---

### Post by armis on 2006-05-08
helo im using ubuntu 5.10,the problem is when i try to install packages simply like this cube_2005_08_29_unix.tar.gz 
i turn on the terminal,and type "sudo apt-get install cube_2005_08_29_unix.tar.gz" then i launch the proces,i can online see two lines,buld dependecy tree,after that line comes out,terminal turns off,and nothing is hapening,help?

---

### Post by ruzle0 on 2006-05-08
i think you have downloaded the source to the program.
copy the file you have to a directory to keep everything in one place then move to that directory
then
```

tar –zxvf filename.tar.gz 
./configure
make
sudo make install

```

i think apt-get can only install packaged source files for ubuntu, and maybe debian's packages.
When you do this you will likely get errors for other missing source packages, make a note of the names and install them too, then try again from the stage you got to. 
after you have done the tar command one of the files will have a list of dependencies if you don't want to find out by the error.
the pakages you will need when you compile normally have dev(development) at the end of the name

I'm not very experienced either yet so someone might be able to give you more accurate information.

---

### Post by armis on 2006-05-08
iwen that doest help,terminal just turns off

---

### Post by ruzle0 on 2006-05-08
how far did you get before the terminal closes,
do you see any error messages if you open terminal again and type
dmesg

---

### Post by Omnios on 2006-05-08
You might find this interesting. Quick short guide on installing software other than repo.
[http://ubuntuforums.org/showthread.php?t=171822]("http://ubuntuforums.org/showthread.php?t=171822")

---

