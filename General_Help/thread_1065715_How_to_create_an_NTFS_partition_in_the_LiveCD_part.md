---
title: "How to create an NTFS partition in the LiveCD partition editor? Please help!"
date: 2009-02-10
forum: General Help
---

### Post by Pipps on 2009-02-10
I am creating a multiple partition table for my Ubuntu installation. I am also intending to create a small (5Gb) NTFS partition, too.

I boot Ubuntu from the LiveCD, double click 'Install' on the Live desktop, and proceed through the usual installation steps. 

When I arrive at the partition editor, a create my Ubuntu partitions, but I attempt to create the additional NTFS partition, I find that there is no option for 'NTFS' within the 'Use as' drop-down menu.  

The only options which I have in this menu are:
- Ext3;
- Ext2;
- ResierFS;
- JFS;
- XFS;
- Fat16; and
- Fat32.

I would like to create a NTFS partition from the Ubuntu LiveCD partition editor. What should I do in order to achieve this?

---

### Post by plucky on 2009-02-10
> I boot Ubuntu from the LiveCD, double click 'Install' on the Live desktop, and proceed through the usual installation steps.



Don't select install,use the partition editor which can be found by selecting **System > Administration > Partition Editor**.

It is the same as using the [Gparted CD](http://gparted.sourceforge.net/) standalone.

If you still have problems,take a screenshot of your partition setup and post to the forum.

Good Luck

---

### Post by Pipps on 2009-02-10
Plucky, it sounds as if you haven't read my post fully.

As I've already said, I am using GParted, from the LiveCD. This is so that I don't have mounting issues when trying to move partitions around.

Using GParted in Ubuntu or in the Ubuntu LiveCD does not produce a different set of filesystem format options. 

So on this basis, my question still remains.

Can anyone help?

---

### Post by LowSky on 2009-02-10
I think you need to install ntfs-3g for Gparted to be able to create NTFS

side not, if it is such a small partition, then why not use FAT32, it is compatable with Linux and Windows, and wont suffer any of the permission issues that can sometimes plague NTFS

---

### Post by plucky on 2009-02-10
> **Pipps said:**
> Plucky, it sounds as if you haven't read my post fully.

As I've already said, I am using GParted, from the LiveCD. This is so that I don't have mounting issues when trying to move partitions around.

Using GParted in Ubuntu or in the Ubuntu LiveCD does not produce a different set of filesystem format options. 

So on this basis, my question still remains.

Can anyone help?

Please read the "quote" line in my post.

What I am saying is not to use the **install** option, but use the "try Ubuntu" option and then select the partition editor from the desktop.

I have just booted my 8.04 Live CD and created an NTFS partition on my test system,so I know it works.

I don't have the 8.10 Live CD so don't know if that option has been removed from Ibex.


Good Luck

---

### Post by ju2wheels on 2009-02-10
> **Pipps said:**
> I am creating a multiple partition table for my Ubuntu installation. I am also intending to create a small (5Gb) NTFS partition, too.

I boot Ubuntu from the LiveCD, double click 'Install' on the Live desktop, and proceed through the usual installation steps. 

When I arrive at the partition editor, a create my Ubuntu partitions, but I attempt to create the additional NTFS partition, I find that there is no option for 'NTFS' within the 'Use as' drop-down menu.  

The only options which I have in this menu are:
- Ext3;
- Ext2;
- ResierFS;
- JFS;
- XFS;
- Fat16; and
- Fat32.

I would like to create a NTFS partition from the Ubuntu LiveCD partition editor. What should I do in order to achieve this?

Before clicking on "install" on the live desktop, open synaptic or use the command terminal and install the package "ntfsprogs".

```

sudo apt-get install ntfsprogs

```

Then begin your install.

---

### Post by Pipps on 2009-02-11
Installing NTFSprogs makes no difference!

---

### Post by wildman4god on 2009-02-11
Just boot up the live cd to the desktop, and in gparted just create a new partition and select format to > ntfs, its not that hard I just did it last night when I tried out windows 7 beta, so I know it works, for future reference just tool around the program and see what options you have, thats probably the best way to learn stuff about computers and linux. When I first started using linux, i would ask all my questions on the forums and/or irc and people started snapping at me, so I just learned to figure it out. I can't remember exactly how to create the ntfs partition, I think, i first resized my ubuntu partition and right clicked the empty unallocated space and selected format to > ntfs, either way however you select what file system you want, the ntfs option should be there.

---

