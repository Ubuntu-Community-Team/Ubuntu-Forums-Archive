---
title: "multibooting with vista"
date: 2006-06-10
forum: Desktop Environments
---

### Post by tunads on 2006-06-10
how do i set up grub so i sees vista.  I installed vista first, followed by ubuntu and now when i start the computer grub does not see vista and boots right into ubuntu.  how do i fix this.

other notes:
os's installed -  windows vista (beta 2) x86
                        ubuntu 6.06 x64


please remember i'm a newbi and i don't know how to do anything  :-)

---

### Post by zxee on 2006-06-10
Maybe you want to post your /boot/grub/menu.lst? But if you can use a text editor and know which partition vista is installed on getting dual booting working should be possible.  Just open the above listed file with gedit at the terminal do 'sudo gedit /boot/grub/menu.lst' Then scroll down that file until you see ## End Default Options ##. After that line you should see your ubuntu entry. Below the ubuntu entry start a new line with: title vista next line: rootnoverify (hd?,?) Note where I have typed question marks you need to provide the actual #'s that designate the drive & partition vista is installed to. So for example if vista is the 1st partition on the master (A) drive the drive designation would look like this (hd0,0) Grub always begins counting from 0. The next line after the rootnoverify line is: chainloader +1
And that should do it. Save your changes and when you reboot you should be able to select and boot into vista.

---

