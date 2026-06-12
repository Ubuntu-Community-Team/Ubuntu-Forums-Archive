---
title: "How to install Stata 10 on Ubuntu"
date: 2009-04-24
forum: Education &amp; Science
---

### Post by chrisby on 2009-04-24
In the terminal:

1. sudo mkdir /usr/local/stata10
2. cd /usr/local/
3. chmod a+rx /usr/local/stata10
4. cd /usr/local/stata10
5. sudo /media/cdrom0/install
6. select the linux version, dynamically linked
7. enter serial number, code, and authorization keys
8. when asked to initialize using ./stini use "sudo ./stinit"
9. enter desired fields
10. your GUI version wont run because it is looking for libtiff.so.3

This is old so make a symbolic link to your current version

ln -s /usr/lib/libtiff.so.4 /usr/lib/libtiff.so.3

11. add stata to your path so your system can see the executable by:
11.1 open the terminal
11.1 sudo gedit ~/.bashrc
11.2 add "PATH=/usr/local/stata10:$PATH; export PATH" to the end of the file
11.3 save
11.4 source ~/.bashrc



To update run with administrative privileges by:
1. open the terminal
2. sudo xstata-se (or whatever your version is)
3. within stata run: update query -> update all


enjoy!

---

### Post by frankwu55 on 2009-08-23
Hi Chris,

I installed STATA through the command line interface...and apologies if this sounds like a stupid question, but this is my first experience with Ubuntu.

How do I install STATA now? I already went through /stint and put in all the licensing info but how do I actually run the program now?

---

### Post by PGScooter on 2009-08-23
I don't know if chris will respond as his post was rather old.

You said that you "already went through /stint". I don't know what that means. Are you saying that you got up to step 8? Where you able to go through all of the steps listed in chris's guide? If so, the following should open stata ```
stata10
``` If that doesn't work you probably had trouble with one of the steps. You could also try ```
/usr/local/stata10
```

---

