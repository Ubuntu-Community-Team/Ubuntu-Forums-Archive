---
title: "vmware player going blitz!!"
date: 2006-01-05
forum: Desktop Environments
---

### Post by alamba on 2006-01-05
Hi all,

I have vmware player installed on my ubuntu 5.10 laptop for a while now. During installation it did give me some errors on missing gcc, etc. which I downloaded and it installed just fine and have been using it ever since.

Yesterday the system popped up some updates and while installing those gave me a list of apps that were not updated and asked me to run "apt-get dist-upgrade".

This I did and it downloaded some packages including a kernel (i think). I invoked vmplayer today and it gives me the message below:

vmware is installed, but it has not been (correctly) configured
for this system. To (re-)configure it, invoke the following command:
/usr/bin/vmware-config.pl.

So I invoke vmware-config.pl and it gives me the error below:

None of the pre-built vmmon modules for VMware Virtual Machine Player is
suitable for your running kernel.  Do you want this program to try to build the
vmmon module for your system (you need to have a C compiler installed on your
system)? [yes]

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

Your kernel was built with "gcc" version "3.4.5", while you are trying to use
"/usr/bin/gcc" version "4.0.2". This configuration is not supported and VMware
Virtual Machine Player cannot work in such configuration. Please either
recompile your kernel with "/usr/bin/gcc" version "4.0.2", or restart
/usr/bin/vmware-config.pl with CC environment variable pointing to the "gcc"
version "3.4.5".

Execution aborted.

Not sure what's gone wrong. Oh the system did ask me to reboot yesterday after the upgrade which makes me think that it's now using a new kernel. But even if it is why is gcc missing now?

Regards,
Akshay Lamba

---

### Post by alamba on 2006-01-05
Well did'nt get a reply on this one. This is how I solved it:

1. Saw during boot that I was using kernel 2.6.12-i386
2. Reinstalled gcc 3.4.5
3. Installed linux headers for the above kernel
4. Re-ran vmware-config.pl

Went through smoothly and I got vmware player running again!!

However, here's the trouble spot still, when I run vmware player now, I get the below message:

This product has expired.
Be sure that your host machine's date and time are set correctly.
There is a more recent version available at the VMware Web site: "http://www.vmware.com/info?id=4".

Any clue? The link above just takes me to vmware's products page.

Akshay

---

### Post by alamba on 2006-01-05
ok..got it fixed finally...if you roll back the clock vmware works perfectly with no problems. However at current date and time it says product expired. This is version 1.0.0 of vmware player.

Download version 1.0.1 from the site and install the tar and you'll be good to go.

Akshay

---

