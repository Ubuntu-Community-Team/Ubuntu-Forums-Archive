---
title: "C Header files that matches the running kernel"
date: 2005-02-28
forum: Desktop Environments
---

### Post by ichoudhury on 2005-02-28
I am trying to install VMware and keep getting a msg 


What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]

I tried every path I could think of, but get something like below

The path "/usr/X11R6/lib/modules/linux" is an existing directory, but it does
not contain at least one of these directories "linux", "asm", "net" as expected.

Thanks for your pointer.  I ran into something similar before, but can't remember what I did then.

---

### Post by Juergen on 2005-03-01
Have you installed 'linux-source-2.6.8.1'?

---

### Post by ichoudhury on 2005-03-01
I don't think so.  I used the default install and did not select any packages.  Now, what would be the best way to perform that?

Thanks

---

### Post by az on 2005-03-01
install build-essential and linux-headers.  Use the linux-headers package that exactly matches your running kernel.

---

### Post by ichoudhury on 2005-03-01
Could you please share the exact command here for me?

apt-get install build-essentials 
apt-get install linux-headers

Not doing that for me...  I am doing it from the Root Terminal.

---

### Post by az on 2005-03-01
uname -a

apt-cache search linux-headers

sudo apt-get install linux-headers-2.6.8.1-3-386
sudo apt-get install build-essential

---

### Post by ichoudhury on 2005-03-03
Thank you, finally got that taken care of... but ran into another brick-wall  ](*,) 

I install and configure VMWare Workstation all the way.  I create the "Guest OS" profile and then reboot (because for some reason it is not seeing the bootable CD).  And each time I come back up to run VMware ....

I get 

"VMware  Workstation is installed, but it has not been (correctly) configured for your running kernel. To (re-)configure it, you must run "vmware-config.pl".  I do that everytime and it allows me to bring up vmware by typing vmware.  But after a reboot, I am back on the same boat.  I haven't really looked at this in anywhere but decided to post here to see if anybody noticed something like this.....I hope somebody have  [-o<

---

### Post by ichoudhury on 2005-03-11
I even bypassed that by installing the patch  \\:D/ 

Guess what?  Run into yet another issue.  Basically I kept the Network setup for "Bridge" setup but guess OS will never get an IP.  I tried the other networking configuration from the vmware configuration, but didn't work.  Oh well, I am going to give up on VMware at least for few days.  Meanwhile, I am trying to configure something else  :grin: 

Thanks!

---

