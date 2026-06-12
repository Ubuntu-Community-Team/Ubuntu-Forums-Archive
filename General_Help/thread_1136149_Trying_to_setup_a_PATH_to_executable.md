---
title: "Trying to setup a PATH to executable"
date: 2009-04-24
forum: General Help
---

### Post by whaler1 on 2009-04-24
Hi, I am trying to setup a executable path in the bash.bashrc file so I can get to sunstudio from the command line in the home directory.  I added the following 2 lines to bash.bashrc;

PATH=/home/sid/sunstudioceres/bin/sunstudio/bin:$PATH; export PATH
MANPATH=/home/sid/sunstudioceres/bin/sunstudio/man:$MANPATH; export MANPATH

but it doesn't seem to work, any ideas? ...and yes...I am still relatively new to Ubuntu 8.10.

Thanks

---

### Post by dcstar on 2009-04-24
> **whaler1 said:**
> Hi, I am trying to setup a executable path in the bash.bashrc file so I can get to sunstudio from the command line in the home directory.  I added the following 2 lines to bash.bashrc;

PATH=/home/sid/sunstudioceres/bin/sunstudio/bin:$PATH; export PATH
MANPATH=/home/sid/sunstudioceres/bin/sunstudio/man:$MANPATH; export MANPATH

but it doesn't seem to work, any ideas? ...and yes...I am still relatively new to Ubuntu 8.10.

Thanks
This will show you what is set:
```
echo $PATH
```
This will change the path for all users:
```
gksudo gedit /etc/environment
```

---

### Post by whaler1 on 2009-04-24
The "echo $PATH" command shows that sunstudio is included in the proper path.  The weird thing is that I can use the mouse to click on the executable and the Sunstudio package loads fine but when I use the terminal to navigate through to the folder where the sunstudio executable is located and then type 'sunstudio' at the command prompt the package does not load.  Is there someway to get a command line instruction to be recognized as an executable call?

---

### Post by dcstar on 2009-04-24
> **whaler1 said:**
> The "echo $PATH" command shows that sunstudio is included in the proper path.  The weird thing is that I can use the mouse to click on the executable and the Sunstudio package loads fine but when I use the terminal to navigate through to the folder where the sunstudio executable is located and then type 'sunstudio' at the command prompt the package does not load.  Is there someway to get a command line instruction to be recognized as an executable call?

Post the output of $PATH and the "ls -al" output of the directory.

---

### Post by whaler1 on 2009-04-25
D, thanks for your assistance.  My mistake was that the PATH to sunstudio actually pointed to a pointer to the sunstudio executable.  I was sloppy by not paying attention to file-types.  Once I finally realized what I had done it became a no-brainer.  My latest problem is that the latest ver of sunstudio express does not seem to be able to find the CC compiler which may be the subject of a new thread pretty soon.

---

