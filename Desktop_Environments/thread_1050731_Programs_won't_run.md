---
title: "Programs won't run?"
date: 2009-01-25
forum: Desktop Environments
---

### Post by kcredden on 2009-01-25
Hey folks: I'm noticing this a lot. Does anyone else have problems getting programs to run either occasionally, or all the time?

I use Krusader as a file manager, and a lot of times a program won't run when I click on a file to view it (example: Kate for .TXT files)

The panel shows the hourglass spinning, but then it doesn't start. Sometimes I can either log off, or reboot and that solves the problem.

Today I've been unable to run GIMPShop too. Although I could before. The only way to start it, is with a terminal, in which I type 'gimp' but get this odd output

kcredden@zeus:~$ gimp
/usr/local/lib/gimp/2.0/plug-ins/print: error while loading shared libraries: libgimpprint.so.1: cannot open shared object file: No such file or directory

(gimp:14852): LibGimpBase-WARNING **: gimp: wire_read(): error
/usr/local/lib/gimp/2.0/plug-ins/script-fu terminated: Interrupt
gimp: terminated: Interrupt
kcredden@zeus:~$

This problem is especially bad for WINE programs. The only possible way I can run Dreamweaver, is by going into the /root/.wine directory and directly clicking on 'Dreamweaver' I cannot even start it via the terminal and SUDO. The programs don't even appear on the menu.

I had the same with Frostwire, but then when I ran it in a terminal, I found I didn't have the right type of Java. Once that was installed, it worked from the menu. - So I'm suspecting there's something not working or loading right but especially in Wine I can't trace the problem.

This also showed up today, when I downloaded Gramps' .DEB file, and tried to run it. In terminal, I typed 'sudo apt-get install *.deb (and it was the only one in the directory) said it couldn't find the file, and it spelled out the exact file name. So I tried installing it using Krusader by just clicking on it (which normally works) It says it needed 2 more packages, but clicking on the 'install' button did nothing. It sat there for a moment, then turned itself off.

Any idea what's going on?

***
Intel p4 3ghz
nVidia GeForce 7300
1g memory
Kubuntu 8.04.01/KDE 3.x
200, and 350g harddrives
***

---

