---
title: "how to compile print driver."
date: 2005-12-10
forum: Desktop Environments
---

### Post by dangerchris on 2005-12-10
I have a Konica Minolta 2400w. I found a driver for it at Sourceforge. The driver came as a tar.gz file. I unpacked it with Ark and extracted it to my  home folder (home/chris/md2300w-0.51) The instructions say to check for various files (foomatic etc.), I have these. The instructions say to go to the top level directory-

4. Enter the top-level directory and run "configure"

       $ cd m2300w-<version>
       $ ./configure

    5. Run make

       $ make

    6. Install the files (needs to be done as root)

	$ su
	Password: ********
	# make install

When i run these commands in the home/chris/md2300w-0.51 path I get an error message saying that no c compiler exists in the path. When I run it from the top level directory- chris@desktop:/ $ It tells me that no md2300w-0.51 exists. I think the problem has to do with the compiler and the file to be compiled need to be in the same folder?

 If anyone has any advice, I appreciate it.

Thanks

---

### Post by cwaldbieser on 2005-12-10
[QUOTE=dangerchris]I have a Konica Minolta 2400w. I found a driver for it at Sourceforge. The driver came as a tar.gz file. I unpacked it with Ark and extracted it to my  home folder (home/chris/md2300w-0.51) The instructions say to check for various files (foomatic etc.), I have these. The instructions say to go to the top level directory-

4. Enter the top-level directory and run "configure"

       $ cd m2300w-<version>
       $ ./configure

    5. Run make

       $ make

    6. Install the files (needs to be done as root)

	$ su
	Password: ********
	# make install

When i run these commands in the home/chris/md2300w-0.51 path I get an error message saying that no c compiler exists in the path. When I run it from the top level directory- chris@desktop:/ $ It tells me that no md2300w-0.51 exists. I think the problem has to do with the compiler and the file to be compiled need to be in the same folder?

 If anyone has any advice, I appreciate it.

Thanks[/QUOTE]
You need to install the compiler toolchain
```

$ sudo apt-get install build-essential

```
Then go to the top level directory:
```

$ cd /home/chris/md2300w-0.51
$ ./configure
$ make

```

I would reccomend using checkinstall:
```

$ sudo apt-get install checkinstall
$ sudo checkinstall -D

```
Answer some questions, and you are done.  Now you should be able to uninstall if things go wrong.

---

### Post by dangerchris on 2005-12-11
This worked well and the printer is up and running.

Thank you cwaldbieser,

---

### Post by lduperval on 2005-12-12
Hi,

I am looking at buying a laser color printer and it's between an HP Color Laserjet 2600n and the 2400w.

What kind of output are you getting from the device? Can you compare it to other laser printers you have tried?

Thanks,

L

---

### Post by Gsx_Eclipse on 2005-12-20
I am trying to install the compiler toolchain as mentioned above.  At the bash prompt I get the following message, "sudo: apt-get: command not found."  I too have the Konica Minolta 2400w. I am running Mac OS 10.4.3, and have downloaded the same m2300w-0.51 from Sourceforge.  Any help is greatly appreciated, as I am quite new to the Terminal!!!

---

### Post by anil_robo on 2005-12-20
1. Make sure you're not trying to run that command (apt-get) from MacOS! YOu have to run this command from Ubuntu! ;)
2. Go to Applications-->Add applications. It may ask for your user password. Enter that.
3. In the program that opens up, click File-->Advanced
4. Now there's a search button - click on it and search for "apt"
5. You'll find a package named **apt**
6. CLick on apt, and choose mark for installation
7. FInally click the "APPLY" button
8. CLose the window, and you should be able to use apt-get!

Edit: He turned out to be a mac user indeed! Poor me! I have never operated a mac, so I don't know how to compile a driver for mac. Someone please help gsx_eclipse! Thanks! :)

---

