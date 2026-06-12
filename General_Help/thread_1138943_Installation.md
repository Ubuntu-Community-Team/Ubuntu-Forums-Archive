---
title: "Installation"
date: 2009-04-26
forum: General Help
---

### Post by ian9113 on 2009-04-26
I have recently downloaded Kubuntu (using windows) and am now using it in Demo mode, because I have not yet installed it. When using the installer, it says that my only drive is completely full, even though I know for a fact that I have 23gb of empty space on my C drive. I am worried that letting Kubuntu install on the drive will erase all of my files on Windows. Any help would be appreciated.

Thanks,
Ian

---

### Post by lisati on 2009-04-26
Have you done a disk cleanup and defragmented your hard drive?

With XP, go to "My Computer", right-click on the disk drive, and you will be able to run the disk cleanup and defrag tools.

---

### Post by Chris Musampa on 2009-04-26
At the partitioning stage of the install choose 'Manual' and define your new Kubuntu root partition (mountpoint = /) in your empty space.

Edit: Its not clear whether your talking about empty unpartitioned space on your drive or empty space in your windows partition. Also state whether you want to install kubuntu in windows or in its own partition.

---

### Post by luisfpg on 2009-04-26
If you're trying ubuntu and don't want to mess with partitions, you may download the Windows based installation, Wubi. There' a link for it under "Even more options" in the download page ([http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)).
It installs ubuntu inside a data file in the same windows partition.

Otherwise, you may, in the normal installation, set the option to install ubuntu side-by-side with windows. It will resize the windows partition and create a partition for ubuntu.

---

### Post by ian9113 on 2009-04-26
I'll do that then. Is there a Wubi installer for Kubuntu? And how do I remove Kubuntu from my system?

Just in case there isn't a wubi installer for kubuntu, here is what I am talking about. On the top it shows that I have zero free space:
[IMG]http://img340.imageshack.us/img340/5218/snapshot1i.png[/IMG]
On the bottom it shows that Kubuntu will take up all of that space...

---

### Post by mb_webguy on 2009-04-26
Yeah, assuming you don't want to replace Windows with Kubuntu, you need to shrink your Windows partition and create a new one to install Kubuntu.

Make sure you've [defragmented your drive]("http://itsfood.wordpress.com/2008/01/30/tech-how-to-defrag-in-windows-vista/").  Once that's done, boot from the Kubuntu LiveCD and use GParted (the partition editor) to [shrink the Windows partition]("http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/").  (Make sure you have a Windows installation disc handy in case you need to repair Windows).

Now you can install Kubuntu on the free space you just created.  The simplest thing to do would be to select the "Use the largest contiguous free space" option.  However, a lot of people that dual-boot like to have their OSes on small partitions, and have a larger partition to share data between them.  I wrote a [tutorial on my blog]("http://wysiwyb.blogspot.com/2008/08/world-without-walls-or-fences-pt3.html") a while back on how to do it, but a quick Google search will find lots of others.  Here's the official Ubuntu community documentation on [dual-booting with Windows]("https://help.ubuntu.com/community/WindowsDualBoot").

---

