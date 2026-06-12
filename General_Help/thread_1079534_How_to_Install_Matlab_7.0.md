---
title: "How to Install Matlab 7.0"
date: 2009-02-24
forum: General Help
---

### Post by dvmuni on 2009-02-24
Hello to all
 I am new to Linux. I am trying to install Matlab7.0 from CD's
I have downloaded 3 CD's from Internet.
when I was installing 



root@eureka:/media/cdrom# ls
Desktop DB  install               inst_doc.pdf  mac_install_guide.pdf  update
Desktop DF  InstallForMacOSX.app  license.txt   readme.txt             utils
root@eureka:/media/cdrom# ./install
-------------------------------------------------------------------

    An error status was returned by the program 'xsetup',
    the X Window System version of 'install'. The following
    messages were written to standard error:

        Can't open display.

    Attempt to fix the problem and try again. If X is not available
    or 'xsetup' cannot be made to work then try the terminal
    version of 'install' using the command:

            install* -t    or    INSTALL* -t

-------------------------------------------------------------------
.: 15: Can't open /tmp/20317tmwinstall/update/install/cleanup.sh
root@eureka:/media/cdrom# sudo ./install

Setup aborted . . .
The installer cannot be run when your current directory is on the CD.
Change to the target MATLAB installation directory and rerun the installer.

root@eureka:/media/cdrom#

Please help me 

Thanks

---

### Post by taurus on 2009-02-24
Get out of root account.  When you are back at your regular account, copy the install to your $HOME and run it from there.

```
cp /media/cdrom/install .
gksudo ./install
```

p.s.  I hope this doesn't mean [-X.

> I have downloaded 3 CD's from Internet.

---

### Post by dvmuni on 2009-02-24
Thanks for the help and comment.

I have tried but it is giving this kind of error


root@eureka:/home/dvmuni# cd Matlab/
root@eureka:/home/dvmuni/Matlab# ls
Desktop DB            inst_doc.pdf  mac_install_guide.pdf  readme_lic.txt
Desktop DF            license.dat   MathWorks_R14_1.iso    readme.txt
install               license.lic   MathWorks_R14_2.iso    update
InstallForMacOSX.app  license.txt   MathWorks_R14_3.iso    utils
root@eureka:/home/dvmuni/Matlab# gksudo ./install

(gksudo:24390): Gtk-WARNING **: cannot open display:
root@eureka:/home/dvmuni/Matlab#

---

### Post by taurus on 2009-02-24
Look at the first sentence of my previous post again.

---

### Post by dvmuni on 2009-02-24
I have tried this one also...
No result

dvmuni@eureka:~$ ls
ABOUT-NLS  Desktop    Matlab  Pictures  Templates
[desktop   Documents  Music   Public    Videos
dvmuni@eureka:~$ cd Matlab/
dvmuni@eureka:~/Matlab$ ls
Desktop DB            inst_doc.pdf  mac_install_guide.pdf  readme_lic.txt
Desktop DF            license.dat   MathWorks_R14_1.iso    readme.txt
install               license.lic   MathWorks_R14_2.iso    update
InstallForMacOSX.app  license.txt   MathWorks_R14_3.iso    utils
dvmuni@eureka:~/Matlab$ gksudo ./intsall
dvmuni@eureka:~/Matlab$

---

### Post by dvmuni on 2009-02-24
if I am trying with
dvmuni@eureka:~/Matlab$ sudo ./install

Setup aborted . . .
The installer cannot be run when your current directory is on the CD.
Change to the target MATLAB installation directory and rerun the installer.

dvmuni@eureka:~/Matlab$

This  kind of error I am getting

Thanks

---

