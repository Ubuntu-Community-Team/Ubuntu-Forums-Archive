---
title: "MATLAB R2010a Launcher problem."
date: 2011-04-11
forum: Education &amp; Science
---

### Post by cirdam on 2011-04-11
Hey, this is my first time in the Ubuntu forum. I've just installed Matlab R2010a just like it says here:

 [http://https://help.ubuntu.com/community/MATLAB/R2010a]("http://https//help.ubuntu.com/community/MATLAB/R2010a")

And i've added the desktop launcher just like the instructions says but when i launch it i get:

Could not launch 'MATLAB R2010a'
Failed to execute child process "matlab" (No such file or directory)

Any ideas?

Thanks!!!!

---

### Post by Richard85 on 2011-04-12
I have this exact same problem but with MATLAB R2010b. I followed the first three steps from [https://help.ubuntu.com/community/MATLAB/R2010a](https://help.ubuntu.com/community/MATLAB/R2010a)

and created got the launcher.

---

### Post by Richard85 on 2011-04-12
This guy seems be having a similar problem.
[https://help.ubuntu.com/community/MATLAB/R2010a](https://help.ubuntu.com/community/MATLAB/R2010a)
I tried sudo /usr/local/matlabR2010b/bin/matlab
and that worked but I want it to run when I click the icon I created.

---

### Post by Richard85 on 2011-04-12
Other threads ([http://ubuntuforums.org/showthread.php?t=1559906&highlight=matlab](http://ubuntuforums.org/showthread.php?t=1559906&highlight=matlab)) have suggested copying the matlab icon from the matlabR2010b/bin folder but that has not worked for me. I also tried creating a launcher but matlab will start up and then shutdown immediately.

---

### Post by perroazul on 2011-04-12
> **Richard85 said:**
> Other threads ([http://ubuntuforums.org/showthread.php?t=1559906&highlight=matlab](http://ubuntuforums.org/showthread.php?t=1559906&highlight=matlab)) have suggested copying the matlab icon from the matlabR2010b/bin folder but that has not worked for me. I also tried creating a launcher but matlab will start up and then shutdown immediately.

did you guys try starting matlab from the command line? usually the matlab installer aks during the installation if you want to add a symbolic link to /usr/bin which is all what you need in order to run matlab from the command line. I've been using this version of matlab since last year without any inconvenient. 
 
if you don't have the symbolic links, just runt the following command:
```
ln -s /usr/local/share/R2010a/bin/matlab /usr/local/bin/matlab

```
which assumes that you installed matlab in the directory /usr/local/share/R2010a/

---

### Post by Richard85 on 2011-04-13
Thanks so much! Worked Great!

I had to do

```
sudo ln -s /usr/local/matlabR2010b/bin/matlab /usr/local/bin/matlab

```

---

