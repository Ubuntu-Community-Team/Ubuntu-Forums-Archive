---
title: "usb mass storage permissions"
date: 2005-07-19
forum: Desktop Environments
---

### Post by bmgz on 2005-07-19
I have just purchased and installed a new mass storage device. The problem is I want to set permissions specific to the actual device and not the device file.

I am assuming that this cancels fstab as an option. I know that I can identify the device by writing a hotplug usermap script, however I donno how to identify the device file this way (I think they call this a 'catch22'). The actual device file differs, as I have multiple hotplug devices THIS external hd alternates from sda to sdb etc...

umm Ok ive lost track of myself.. and my thoughts, I hope you understand what my problem is.. :roll: 

TIA

---

### Post by bmgz on 2005-07-19
..and I want the device automagically mounted as per usual with it's specific permissions!

---

### Post by bmgz on 2005-07-20
Ok I think I found a simple solution - setting a volume label. *DUH*  \\:D/ 

I incedently bumped into this on redhats docs whilst looking for something totally unrelated..


[http://www.redhat.com/docs/manuals/linux/RHL-7.3-Manual/ref-guide/s1-filesystem-ext3-create.html](http://www.redhat.com/docs/manuals/linux/RHL-7.3-Manual/ref-guide/s1-filesystem-ext3-create.html) 
*"Once you have created and formated a partition, you should assign it a label using the e2label command. This allows you to add the partition to /etc/fstab _**using a label instead of using a device path**_, thereby making the system **more robust**. [1] "*

---

