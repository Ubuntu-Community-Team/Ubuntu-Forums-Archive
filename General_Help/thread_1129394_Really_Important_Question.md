---
title: "Really Important Question"
date: 2009-04-18
forum: General Help
---

### Post by xxeder on 2009-04-18
will upgrading from 8.10 to 9.04 affect my dual boot with vista in any way?

---

### Post by xxeder on 2009-04-18
bump

---

### Post by doas777 on 2009-04-18
if you do it as an upgrade, no, probably not. 
however most recomend doing a clean install rather than an upgrade.
when doing a clean install you have the same risk you had when you created the dual-boot the first time: primarily that you'll format over the wrong partition.

if something gets messed up with grub, you can repair it like so:
[http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/)

have fun, and always be careful when working with partitioning tools.

---

### Post by krnekhelesh on 2009-04-18
First download the new version of ubuntu, burn it on to a cd. Then boot from that CD.

And then start the installation ( basically a clean install ). However during the installation you will be asked to choose the disk. Choose the partition where you have installed the older version of ubuntu. The new installation will write over it.

This is the most important step. If you do this step carefully then your windows partition would not be affected.

An upgrade on the other hand would require you to do these steps. However sometimes upgrades can get messy. Like some packages wouldnt have been properly installed or the upgrade stops in the middle. So a clean install is recommended.

Hope this helps.....

---

### Post by doas777 on 2009-04-18
oh, and if you do have problems with the partitioner and do actually delete the wrong partition, don't panic. Shutdown immediatly, and go to another computer. look up Testdisk, and download a recovery live cd of your choice (I like UbuntuRescueRemix). you can use testdisk to recover the partition, as long as it does not get badly overwritten.

have fun and best of luck

---

### Post by lisati on 2009-04-18
What I've normally done is similar to krnekhelesh's post [here]("http://ubuntuforums.org/showpost.php?p=7096830&postcount=4"):

[LIST=1]
[*]Make a backup of potentially important data
[*]Download ISO file and burn to CD
[*]Boot from CD
[*]Delete existing *ubuntu partition(s) using Gparted (available on the Live CD)
[*]Install, telling installer to "Use largest continuous free space"
[*]Apply any available updates (which can sometime fix hardware problems)
[*]Tinker with menu.lst if necessary 
[*]Restore data that was backed up
[*]Check that I have everything installed and configured that I want installed and configured (e.g. samba, wireless etc)
[/LIST]

---

### Post by Corin-EU on 2009-04-18
> **doas777 said:**
> 
however most recomend doing a clean install rather than an upgrade.
Who is most?

And why do they recommend doing a clean install rather than an upgrade?

Why is an upgrade not recommended?

---

### Post by doas777 on 2009-04-19
well, I can understand your question, but it is conventional wisdom that a clean install is a more sure and reliable method for deploying new operating systems. Upgrading can work, and it can fail. I've had both experiences over the years.

Here are some of the reasons that clean installs are often more sure:

1) media is formatted. no possibility of previous and possibly incompatible programs or program configurations continue to exist. 
All components of the previous os are gone, and cannot come back to haunt you later.

2) all software packages are being installed as part of a unified process, so there are no issues with unupdated dependencies or broken meta packages.

3) a clean install is simple and reasonably predictable. an upgrade is not. people often do things like install custom third party themes, apps, drivers, all of which will need to be compatible. each of these changes must be identified, and it must be determined exactly what action should be taken. obviously this is an impossible task. at least some users will experience zombie programs, unapplyable configurations, etc, and all of it will be complete aberration from a support perspective. 

4) performing a clean install takes far less time than trying to do a distro upgrade off the repos within the first 2 weeks after a release (my last one took 16 hours of downloading, due to swamped servers). 

if you store your data and home on a differant partition, clean installs only take about an hour for the install and an hour or so of reinstalling apps. most of your user configuration is preserved as well.

if an upgrade works for your system and your hardware, then do it. since I know of no way to tell, I just play it safe, and restart from scratch.

---

