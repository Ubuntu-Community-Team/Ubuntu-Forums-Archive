---
title: "How to install source packages (.tar files)?"
date: 2006-04-20
forum: Desktop Environments
---

### Post by ec2 on 2006-04-20
I now know how to install Debian packages, but i still need to install packages, that aren't available in the repositories. If anyone knows how to install .tar or any other type of files, please tell me...
I already know that first you hve to unpack, by "tar xzvf /root/package.tar" (this code might be wrong, i don't know... It works). And then i have to select the folder in terminal, by typing "cd /root/package/", then type "./configure" to edit something... and then type "make" or "sudo make install" but it never works! It just displays an error. So far, i have successfully installed not one package! Please help me...

---

### Post by krusbjorn on 2006-04-20
[QUOTE=ec2]I now know how to install Debian packages, but i still need to install packages, that aren't available in the repositories. If anyone knows how to install .tar or any other type of files, please tell me...
I already know that first you hve to unpack, by "tar xzvf /root/package.tar" (this code might be wrong, i don't know... It works). And then i have to select the folder in terminal, by typing "cd /root/package/", then type "./configure" to edit something... and then type "make" or "sudo make install" but it never works! It just displays an error. So far, i have successfully installed not one package! Please help me...[/QUOTE]

Did you change the "/root/package" to the actual directory of the tar-file? What is the error output from the make, make install and configure commands?

---

### Post by sYs^ on 2006-04-20
try this: ```
sudo apt-get install build-essential
``` and after this try to compile again :>

---

### Post by ec2 on 2006-04-20
I looked up "build-essentials" from [http://packages.ubuntu.com](http://packages.ubuntu.com) . Looks like these are the packages that are missing most of the time, when i'm installing packages. Hopefully this will solve my problem... Thank you!

---

### Post by Thirsteh on 2006-04-20
build-essentials is exactly what the name suggests. The essentials for doing any kind of building on a Linux system, at least C/C++ compilation. It contains things like GCC, the GNU C compiler, GCPP (or G++), the GNU C++ compiler, GDB, the GNU debugger, and various other libraries and headerfiles. When you've installed it, you should be able to compile most programs, those that you can't compile are either not supposed to be compiled on your system, or they will clearly state what package/library is missing, which can be simply apt-get'ed.

---

### Post by louis_nichols on 2006-04-21
[QUOTE=Thirsteh]build-essentials is exactly what the name suggests. The essentials for doing any kind of building on a Linux system, at least C/C++ compilation. It contains things like GCC, the GNU C compiler, GCPP (or G++), the GNU C++ compiler, GDB, the GNU debugger, and various other libraries and headerfiles. When you've installed it, you should be able to compile most programs, those that you can't compile are either not supposed to be compiled on your system, or they will clearly state what package/library is missing, which can be simply apt-get'ed.[/QUOTE]

Let's not forget to mention that if the configure script will ask for library "x.deb" (it's a generic name) then he (or she) will have to install package "x-dev.deb". This is a thing that was confusing me in the beginning.

---

