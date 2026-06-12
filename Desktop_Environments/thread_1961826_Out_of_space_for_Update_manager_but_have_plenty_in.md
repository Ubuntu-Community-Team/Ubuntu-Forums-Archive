---
title: "Out of space for Update manager but have plenty in reality."
date: 2012-04-19
forum: Desktop Environments
---

### Post by rjjnewbie on 2012-04-19
I am totally new to Linux/Ubuntu. I installed on a box with WIN7 as dual boot. Seems to be working fine.
However when I try to install updates using Update manager I am told I have a very small amount of space.
When I look at my home folder, it indicates three devices OS, 255MB files and 175 GB Files. I went back to Ubuntu's partitioning tool and saw I had 8 partions, three for Windows and five for Ubuntu 

The ones for Ubuntu are
                         .................Type                      .....Size(MB) ......             Used (MB)               
/dev/sda5         ext2                               .............254 ....................                          46
/dev/sda6         swap                           ..........1998 .....................                             0
/dev/sda8         ext4............                             3558                        ................3158  
/dev/sda9         swap..........                            6431 .....................                             0
/dev/sda7         ext4 ......                         174814                        .................2940

Obviously I have plenty of space on the sda7 partition but Update manager is not seeing it. What can I do?

Thanks for any help. Please give it step by step because I probably won't understand if you leave out anything.

---

### Post by for.i.am.root on 2012-04-19
Hi

Post the output of mount. You have free space, but where is it?

Mount will tell us where your free space is and what we need to move around.

Applications - Accessories - Terminal

mount

---

### Post by jerrrys on 2012-04-20
Just because you have free space on other partitions does not mean that it will be used.

sda8 is the one being used and is running out of space.

sda9 is way big for a swap partition.  Why two swaps?

sda5?  What is it?

Open a terminal and enter:

df

Lets see if that makes any sense.

---

