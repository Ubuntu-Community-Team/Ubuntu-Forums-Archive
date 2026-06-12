---
title: "Cant Install Byond on my Linux"
date: 2006-09-01
forum: Desktop Environments
---

### Post by Mason W on 2006-09-01
Well I got my Linux yesterday and on my old Windows computer I used to go on Byond so I thought I would get Byond for my Linux desktop I downloaded it and  Extracted it fine just i can't install it both my brother and I have tried but we don't know how to so can anybody help me here:?:

---

### Post by Mikor on 2006-09-01
Here is what we have tried (my brother should have said...)

We looked in the readme file and followed the instructions, it said to edit the install script, so we did, it then said to open a console and type "make install". This just gives an error message saying the command could not be found.

---

### Post by b_martinez on 2006-09-01
Assuming you are in the correct path ,try 

sudo make install

instead. To install a program, you need to have root privileges, or at least root access. 
If you are not in the correct path then , after the 'tar -xvcf' or 'tar -xvjf', then

cd /home/(file-name)
sudo ./config && make && make install
(enter your password)

This should install it for you. I think. I haven't compiled anything in Ubuntu, but that's how I do it in FC5.
Bill

---

### Post by Mason W on 2006-09-01
I tried that, here is the terminal's output:

```
root@ubuntu-mason:~# cd ~/programs/byond
root@ubuntu-mason:~/programs/byond# make install
bash: make: command not found
root@ubuntu-mason:~/programs/byond#
```

---

### Post by b_martinez on 2006-09-01
There are other programs you need, like gcc (GNU c compiler) and maybe gcc++. I am in FC5 now, so I cannot check if the compilers are default installed or not.(Plus, getting close to time for a road trip.) So
1) start synaptic and search for gcc, and make sure you have it installed.
2)make sure you have the -dev files installed for Gnome, maybe the kernel,possibly some others.
Good Luck, and I will check in in around 8 hours.Hopefully, you will have solved this by then, or received more knowledgeable help.
Bill

---

### Post by b_martinez on 2006-09-01
There are other programs you need, like gcc (GNU c compiler) and maybe gcc++. I am in FC5 now, so I cannot check if the compilers are default installed or not.(Plus, getting close to time for a road trip.) So
1) start synaptic and search for gcc, and make sure you have it installed.
2)make sure you have the -dev files installed for Gnome, maybe the kernel,possibly some others.
Good Luck, and I will check in in around 8 hours.Hopefully, you will have solved this by then, or received more knowledgeable help.
Bill

add-on
Read the documentation for "BYOND". It should list all the necessary libraries (lib) and dependencies. Make sure you have them installed.
B

---

### Post by Mason W on 2006-09-01
Whereabouts would synaptic be?

I've installed everything from the add/remove programs menu

---

### Post by b_martinez on 2006-09-01
Since you have a terminal open, just type in synaptics
and hit the 'enter' key
Bill

---

### Post by Mason W on 2006-09-01
```
root@ubuntu-mason:~# synaptics
bash: synaptics: command not found

```

---

### Post by Iarwain ben-adar on 2006-09-01
Hi,
it's called synaptic (without the "s" )


Iarwain

---

### Post by Mason W on 2006-09-01
Right, i've got it working, however, I get an error when I try to run it:

```
root@ubuntu-mason:~# source /home/mason/programs/byond/bin/byondsetup
root@ubuntu-mason:~# DreamMaker
DreamMaker: error while loading shared libraries: libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory
root@ubuntu-mason:~# DreamSeeker
DreamSeeker: error while loading shared libraries: libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory
root@ubuntu-mason:~#
```

---

### Post by Iarwain ben-adar on 2006-09-01
Hi,
just try to install libc6 via synaptic then :D


Iarwain

---

### Post by ed_agamemnon on 2007-06-29
sudo apt-get install build-essential


then 'make' will work.

---

