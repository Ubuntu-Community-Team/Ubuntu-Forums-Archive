---
title: "compile linux application to run in Windows?"
date: 2010-03-12
forum: Desktop Environments
---

### Post by tanyeun on 2010-03-12
hi guys,

one of my friends is a complete windows user
he likes some applications I use on linux

I am wondering how to compile linux application
to run in windows?

eg. output single exe file?

thx,

David

---

### Post by River~~ on 2010-03-12
hi David,

I don't actually know if you can do exactly what you are asking maybe other people will be able to tell you more. 

In case it's not possible, I have two alternative suggestions for you. 

1. if your friend is going to do a lot of this, I'd suggest he installs co-linux. This works a bit like the opposite of Wine(*), ie you install it on a windows box, and then most Linux software runs without needing to be re-compiled, etc. Colinux comes in distro flavours just like regular linux does, so you'll be wanting to install a Ubuntu kernel. There is an archived thread [here](http://ubuntuforums.org/showthread.php?t=81444) that will give you an idea of what is needed. I don't know if colinux is still being maintained, or if K-K is available for it.

The big advantage of this method is that, once the initial work of the install is done, your friend can run synaptic and download and install any of the software you can,  and almost all of it will work directly from the binaries.

2. If there are only a small number of apps your friend wants, then what I'd do is to install Cygwin on the windows box -- Cygwin provides a linux-like environment complete with a bash shell, POSIX, etc. Install the Cygwin developer tools, then proceed as for a traditional linux make & install.

By "traditional", I mean that you won't have apt / synaptic etc to resolve dependencies and so on, before starting on the make process. If you have not doen this before, I'd suggest you practice within your favourite Linux flavour before trying to do it on Cygwin.  There are plenty of tutorials on the web -- when I did my first traditional linux compile it took a day or so to get the hang of it.

hope that helps, or at least that it is of interest.
regards,
R~~

---

### Post by sgosnell on 2010-03-12
You would have to compile it with a Windows compiler, and use Windows libraries instead of Linux libraries.  It's going to be a lot more trouble than it's worth, if it's even possible.  The big problem is the libraries.  You'll need to know a lot about C++ programming.

---

### Post by tanyeun on 2010-03-13
thanks for the advice guys

so if I want to compile it and run in windows
I have to find the equivalent libraries

David

---

### Post by abohsin on 2010-03-13
Hi,

I think your friend likes linux and sees an advantage in it, but for one reason or the other he is reluctant to make the switch. I have met these people, and found three answers:

1. Install VirtualBox on Windows, boot the vbox from ubuntu live cd, then install it on the virtual hard disk. This way he can have both windows and ubuntu running on the same machine.
2. This is the easiest part, use a live cd or live usb with persistence space, which u can make from you ubuntu machine, the drawback is that he will have to reboot to access the ubuntu machine.
3. This is probably the best option, install ubuntu inside windows. Just load the ubuntu cdrom while windows is running and let it install itself inside windows. This will give your friend a dual boot installation without doing any installation dos-level at all. Then again he will have to reboot to enter the linux os.

A personal piece of advice, don't go through compiling linux binaries to windows, it may not perform the same way as it does on linux, and this will cause your friend to freak away from linux after he had just come to like it.

---

### Post by Tikkyca on 2010-03-13
Well i don't know how to do that,but he can use ubuntu in virtual machine.

---

### Post by dmillard10 on 2010-03-13
My suggestion, as has been stated before, is a virtual machine.  With the "seamless" mode in VirtualBox and a decent computer, you can have the Ubuntu menus at the top and the Windows menus at the bottom.  Everything works (or at least worked for me) fairly seamlessly.

---

### Post by kellemes on 2010-03-13
Running KDE-apps on Windows without having to recompile.
[http://techbase.kde.org/Projects/KDE_on_Windows/Installation#KDE_Installer_for_Windows]("http://techbase.kde.org/Projects/KDE_on_Windows/Installation#KDE_Installer_for_Windows")

GTK-apps you need to recompile for sure.. unless there already is Windows-binary available.

---

### Post by tanyeun on 2010-03-14
thanks guys

very useful suggestions :D

David

---

