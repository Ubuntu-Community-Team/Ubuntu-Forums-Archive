---
title: "help pls replacing a 2nd linux install with /home partition"
date: 2009-04-22
forum: General Help
---

### Post by Ascenti0n on 2009-04-22
I have Ubuntu 8,10 and Kubuntu 8.10 on my system, on the same drive. I want to delete the Kubuntu install and remove the boot up options that go with it, and add a /home partition in it's place.

I want to have a separate home partition with my home folder copied over BEFORE installing/upgrading to Ubuntu Jaunty next week (I will stay with EXT3). 

Can someone show me what to do or point me to a 'howto' that will walk me through what I need.

thanks.

---

### Post by kpkeerthi on 2009-04-22
Here is an easiest and simplest route:

1. Backup the contents of /home/<your-user> an external media. 
2. Install Jaunty. Use Jaunty's installation wizard to create a separate /home
3. Restore the backed up contents back to your new /home/<user>. (You might want to selectively restore the dot (hidden) files)

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by Ascenti0n on 2009-04-22
I did think of that, but this solution doesn't address the Kubuntu installation and boot options does it?

---

### Post by kpkeerthi on 2009-04-22
There is an option in the install wizard where you can choose to install Jaunty on to "Whole Drive" with custom Partition Layout (where you will specify that you need a separate /home). Once the installation completes, all existing OS will be wiped out and a new GRUB will be set up, with Jaunty as the only boot option.

---

### Post by Ascenti0n on 2009-04-22
@kpkeerthi: thanks for your help :)

---

### Post by philinux on 2009-04-22
Choose manual partitioning.

---

