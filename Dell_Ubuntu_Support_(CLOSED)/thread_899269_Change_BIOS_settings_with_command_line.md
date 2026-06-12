---
title: "Change BIOS settings with command line"
date: 2008-08-24
forum: Dell Ubuntu Support (CLOSED)
---

### Post by WoPr on 2008-08-24
Hi everyone!

I have several Inpiron 1525 laptops on a classroom running Ubuntu, and I would like to know if there is any form of change the BIOS settings of the laptops from the command line.

I have a central server who give the boot scripts to the laptops, so the idea is to change the boot scripts, boot up the laptops and make the changes automatically on the BIOS.

Anybody knows if there is something to do it?

Thanks a lot and best regards!!

---

### Post by bthoward on 2008-08-24
Highly doubtful you'll find something to get this done unless its provided by Dell.

---

### Post by superm1 on 2008-08-25
Depending on what types of things you are looking to change, the package you are looking for is libsmbios-bin.

---

### Post by sdennie on 2008-08-25
What specific settings are you trying to change?  A lot of "BIOS functionality" is exported via /proc or /sys so, there is a good chance that the things you want to change can be easily changed.

---

### Post by anjilslaire on 2008-08-25
<disregard>

---

### Post by WoPr on 2008-08-26
Hi!

Thanks for the answers. I am going to the explain the case and tell what I want to do:

- The laptops have a locked desktop for the classmates with many programs to use.
- In the BIOS they only have a boot option from the HDD with a password of unlock.
- I have a server with partimaged. I have a 1525 where I made the master ISO and put in the server.
- When I want to update the OS of the laptops with a new image, I have to go laptop per laptop unlocking the BIOS boot option from CD, put a modificated G4L CD, boot, wait until it reloads the new ISO from the server, quit the CD and quit the CD boot option.
- There is almost 50...

The thing is that the laptops on boot, they look for some boot scripts on the server (shell scripts), which I change for many purposes. I would like to have a manner of change the boot option from the laptops to network boot option.

The proccess would be:

1- Boot a locked laptop
2- Start the system
3- Look for the server boot scripts -> I change one of them to change the BIOS settiings on the laptops and reboot them.
4- The laptop starts with a network boot option.
5- I have a PXE server ready to accept connections and send a G4L modified boot image.
6- The image loads on the laptop.
7- Change the BIOS network boot and reboot laptop.
8- The laptop boots with the new ISO while I am having some cofee :-D

I hope to be explained well, because my English is a bit limitated :_(

I accept suggestions too, but remenmber that I don't want to go laptop per laptop no more!! :-D

Thank you again and and best regards

---

### Post by WoPr on 2008-08-26
I have done this:

[http://www.colino.net/wordpress/archives/2008/05/21/how-to-change-dells-bios-settings-from-a-linux-command-line/](http://www.colino.net/wordpress/archives/2008/05/21/how-to-change-dells-bios-settings-from-a-linux-command-line/)

But it seems that it does not work with a 1525 :_(

Best regards

---

### Post by superm1 on 2008-08-26
So in terms of other suggestions, how about this:

Set up network boot to always be tried first, hard drive second.  When you need to push updates to these, you turn on your TFTP server.  When you don't need updates pushed, you leave it off.  So if they try to boot with network plugged in, your DHCP server will tell them to try to connect to TFTP, it will fail out and then they carry onward with hard drive boot.

---

### Post by WoPr on 2008-08-26
Thanks for your answer superm1, but I have tried it with bad results. The thing is that I have to be aware of the laptops over the four classrooms so nobody plug one while the TFTP server is up, so this solution is not valid. Because of this I need the BIOS solution, or restoring a partimage ISO over a mounted partition, but I do not get yet :_(

Thank you and best regards

---

### Post by WoPr on 2008-08-29
Hi!

Any ideas/solutions/suggestions?

Thanks!!!  :guitar:

---

### Post by say2sky on 2008-09-05
I also want to know if Change BIOS settings with command line is possible?
or just read out  BIOS settings?

---

