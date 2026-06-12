---
title: "Can I install a .bin package with Synaptic Package manager?"
date: 2010-10-02
forum: Desktop Environments
---

### Post by imcampos on 2010-10-02
I want to install CmapTools in my desktop, which runs v.10.04.
I have downloaded the .bin file from their site.
Is there a way to install it using Synaptic Package Manager?

---

### Post by sikander3786 on 2010-10-02
Simple answer no.

You can install it using the install instruction that came along it.

Synaptic was built to handle .deb only, and those too from the repositories. GDebi is used for offline .deb installation.

What do you really want to achieve by installing a .bin through Synaptic?

---

### Post by ankspo71 on 2010-10-02
Hi,
Installing bin files is usually just a matter of marking the file as executable, then running the file in the terminal, then following the instructions that appear (if any).

So right click on the file, choose properties, and go to the permissions and mark it as an executable. In the desktop that I use (KDE), the option is called "Is Executable", but in Gnome it might be called "allow executing file as program" or something similar.

Okay step one is done.

Next, open a terminal. These commands will change the directory that you will be working in.
A. If the bin file is on your desktop type this in the terminal:
```
cd Desktop
```
B. If the bin file is on your Downloads directory type this in the terminal:
```
cd Downloads
```
C. If the bin file is on your home directory you won't have to do anything here.

Next, type this command to list the files in the directory you just opened. This will confirm that you are in the right directory, plus it will make filename auto-completion work when you use the Tab key.
```
ls -a
```
If you are in the right directory, you should see the bin file that you downloaded.

Next, are a few possible ways to install a bin file so I'll list a few commands. (Note that most applications that need to be installed require sudo, so I usually recommend using sudo).

A.```
sudo ./packagename.bin
```
B.```
sudo sh packagename.bin
```
C.```
sudo bash packagename.bin
```

The first command is usually successful, but I put some other commands in there that may or may not work, just in case.

That should do it, unless your bin file has special instructions.

Here is a link that has a lot of installation howtos:
"How to install anything in Ubuntu"
[http://amitech.50webs.com/installing/index.php.html](http://amitech.50webs.com/installing/index.php.html)

---

