---
title: "External Harddrives"
date: 2009-04-20
forum: General Help
---

### Post by accooper on 2009-04-20
Why does Ubuntu always try to install it's self on an external hard drive?  I have now installed Ubuntu 8 times and every time I have to unplug the external hard drive to keep it from installing there.  Is there a way around this?  If so how in easy terms do I do that.

:guitar:

Andrew

---

### Post by codeseer on 2009-04-20
I'm pretty sure you should be able to select the drive you want to install to during the Ubuntu installation process. Does it not show but one drive in the screen where you are allocating partitions? You aren't using the 'automatic install' are you?

---

### Post by aeiah on 2009-04-20
i dont know why it defaults to your external drive and not your internal, but it is just defaulting there, that's all. you should be able to select the other drive quite easily. im guessing it sees that drive as being the biggest, perhaps? and as such just assumes its the one you want to use.

---

### Post by codeseer on 2009-04-20
You have 7 steps, technically, in the installation of Ubunut. When you place the CD in, you select to install, then you select your language for the install.

Then:

[LIST=1]
[*]Select language for the installed system.
[*]Select time zone for the installed system.
[*]Select keyboard layout for the installed system.
[*]Select the path for the partitioner to take.
[*]So on...
[/LIST]

I think maybe you're messing up at step 4, when you select the path for the partitioner to take.

Edit:

You should almost always be selecting 'Manual' from the list.

[[IMG]http://img257.imageshack.us/img257/91/partitionerselection.png[/IMG]](http://img257.imageshack.us/my.php?image=partitionerselection.png)

As you can see, there's a manual selection at the bottom.

[[IMG]http://img253.imageshack.us/img253/7153/partitionermanualscreen.png[/IMG]](http://img253.imageshack.us/my.php?image=partitionermanualscreen.png)

...and this is the screen you get when you select 'Manual'; it is a sub-step of step 4. This allows you real control over the partitioning.

You can clearly see that /dev/sda is my first drive and /dev/sdb is my second drive. Then indented below them are the partitions allocated on each.

(This is really an Ubuntu 8.10 install in VirtualBox with my Jaunty disk image threw in there for this demonstration.)

In manual mode, you want to allocate a swap partition that is equal to the amount of RAM you have in your system. Then decide if you want the / (root) partition to hold your /home mount point or if you want it in a separate partition, then partition the remaining space in accordance.

---

