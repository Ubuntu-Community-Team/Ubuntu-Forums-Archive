---
title: "vmware install"
date: 2005-10-26
forum: Desktop Environments
---

### Post by jimmygoon on 2005-10-26
Your kernel was built with "gcc" version "3.4.5", while you are trying to use
"/usr/bin/gcc" version "4.0.2". This configuration is not supported and VMware
Workstation cannot work in such configuration. Please either recompile your
kernel with "/usr/bin/gcc" version "4.0.2", or restart /usr/bin/vmware-config.plwith CC environment variable pointing to the "gcc" version "3.4.5".

---

Please help. Thanks
I can't apt-get 3.4.5 and I can't export CC="/usr/bin/gcc-3.4.5" ... because it doesn't exist therefore I can't finish installation. please help thanks

---

### Post by Remmelas on 2005-10-26
sudo apt-get install gcc-3.4
CC="/usr/bin/gcc-3.4" rest_of_vmware_install_command

---

### Post by jimmygoon on 2005-10-27
[QUOTE=Remmelas]sudo apt-get install gcc-3.4
CC="/usr/bin/gcc-3.4" rest_of_vmware_install_command[/QUOTE]

thanks

--
What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]
--

Now what?

---

### Post by Remmelas on 2005-10-27
This one is a little more difficult, but it looks something like this

sudo apt-get install linux-headers-2.6.12-9-k7
note that you need to replace the linux-headers version with the one that matches the kernel you boot from.
Then, the headers will be placed, in this example
/usr/src/linux-headers-2.6.12-9-k7

---

### Post by jimmygoon on 2005-10-27
[QUOTE=Remmelas]This one is a little more difficult, but it looks something like this

sudo apt-get install linux-headers-2.6.12-9-k7
note that you need to replace the linux-headers version with the one that matches the kernel you boot from.
Then, the headers will be placed, in this example
/usr/src/linux-headers-2.6.12-9-k7[/QUOTE]

Wow. I hate to do this to you guys but how do you find your kernel version. I understand what to do with it (i think) but I don't know how to determine it ;)

thanks for working with me guys

edit: google DOES work miracles. For anyone else its "uname -r"... so lemme do that get back to y'all

edit2: 

---
The path "/usr/src/linux-headers-2.6.12-9-386" is an existing directory, but it
does not contain at least one of these directories "linux", "asm", "net" as
expected.
---

It continues...

edit3: AHAHHA I beat it!... for a while... it was "/usr/src/linux-headers-2.6.12-9-386/include"
......

---

### Post by jimmygoon on 2005-10-27
Thanks for dealing with me guys.

Its installed and running now. Thanks for all the support.

---

### Post by Remmelas on 2005-10-27
I'm not much help normally, but glad to help where i can, just went through the vmware install myself last week is the only reason i could even help.

---

