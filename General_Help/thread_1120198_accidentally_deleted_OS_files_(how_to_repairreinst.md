---
title: "accidentally deleted OS files (how to repair/reinstall ubuntu)"
date: 2009-04-08
forum: General Help
---

### Post by Mmmtobacco on 2009-04-08
Hi there,

After I installed ubuntu, i tried to experiment with different GUIs apart from the original install using the download manager. I downloaded the kmd(?) files to try to imitate a Mac desktop and was unable to work some of the addons so I reverted back to the default UI. To reduce the clutter, I went to delete all the files for the other GUI and unchecked all of the files associated with my current UI. As I was looking at the files being deleted, i started seeing files being deleted that were in use by my current UI and I was unable to cancel the process. As a result, all files, including the fonts, were deleted and I was left with a desktop with all characters in the fonts replaced by boxes and the download tool missing.

Is there any way to repair the installation of ubuntu? If not, what's the proper way of uninstalling and reinstalling ubuntu if i'm dual booting with windows xp currently?

Any help woild be appreciated.

---

### Post by coffeecat on 2009-04-08
> **Mmmtobacco said:**
> Is there any way to repair the installation of ubuntu?

I don't know, but there's one thing I would try before a reinstall. Can you open a terminal? If you open a terminal, can you read it? If you can't, press Ctrl-Alt-F1 and you will be presented with the login prompt for a virtual console. Login.

Whether you are in a terminal or a virtual console, try this command:

```
sudo apt-get install ubuntu-desktop
```'ubuntu-desktop' is the metapackage for all the constituent packages of the Ubuntu (gnome) desktop and will reinstall anything that has been uninstalled. Hopefully that will restore your gnome desktop. Once everything has been installed, reboot with:

```
sudo shutdown -r now
```I don't know about the fonts. I'm hoping it's not the fonts that have ben uninstalled, rather something of the GUI that renders them.

Because you've tagged your thread 'ubuntu', I'm assuming you are indeed using Ubuntu Gnome. If you are using Kubuntu or Xubuntu, substitute 'kubuntu-desktop' or 'xubuntu-desktop' in the above command.

**Edit:** it's nearly midnight here and I'm going to bed now, so sorry I can't follow this for a few hours. There are plenty around who will, no doubt.

---

### Post by Mmmtobacco on 2009-04-08
When i went to reboot into unbuntu just now, it didnt bring up the gnome interface at all. it put me right into the virtual console. i entered in the install command and it all worked fine it seemed, but i rebooted with the shutdown command and it put me back to the console, no desktop to be found...

any ideas?

---

### Post by coffeecat on 2009-04-09
I may have misunderstood your original post - I was tired. When you said 'delete all the files for the other GU' I made the assumption that you had uninstalled something, and that the installer had then merrily uninstalled a load of essential stuff for the GUI. Of course, you probably did precisely what you said - that you deleted a load of files, and presumably some essential files got deleted in the process. Which, if you did, you must have invoked administrator privileges. Whatever - apologies for the misunderstanding.

Anyway, assuming that you did a delete things rather than an uninstall them, the system may be beyond repair, particularly if you deleted files in system folders such as /usr or /etc. (If you deleted stuff in a system folder, you could very well have lost your font files.) Please post more specific details of what you did. Which 'UI" (I presume you mean desktop environment such as gnome) did your flavour of Ubuntu come with? What was the 'other GUI'? Where were the files you were deleting?

But try this. Boot up until you get to the console login. Log in and at the prompt issue this command:

```
startx
```If the GUI loads up we can see what ever else might be missing, although it might be simpler just to reinstall. If it doesn't, then its time to rescue personal data from that installation (if any) and reinstall.

To answer the last questions of your first post, you don't need to uninstall Ubuntu before reinstalling. You merely reinstall over the old installation - the partitions of the old installation simply get reformatted. There's a couple of ways of doing that with the live CD, so if you need them I can give further details.

---

### Post by Mmmtobacco on 2009-04-09
i tried the startx command and it gave me the following error

"error in locking authority file /home/(my username)/.Xauthority"

i'd rather just install again from scratch, what's the process of uninstalling ubuntu and reinstalling it?

---

### Post by coffeecat on 2009-04-09
I think you're wise. Sometimes it's quicker reinstalling than trying to fix a broken system.

I'm assuming that you have the most straightforward installation layout there, just three partitions: your Windows C:, your Ubuntu root (/) partition, and a Linux swap partition. If you have anything more complicated you'd better post back.

By the way, you haven't said which version of Ubuntu you are running. There are minor differences in the installer between Hardy, Intrepid and Jaunty, but I don't think this will affect what I'm going to describe.

Boot up with the live CD. Go to System > Administration > Partition Editor. Don't do anything with it, but make a note of what it tells you. If you do have just three partitions, it will probably tell you that Windows is a NTFS partition on sda1. Make a note of the sda numbers of the Linux swap partition and the ext3 partition.

The ext3 partition is your old root ( / ) partition which we can reuse. Now start the installer and at the partitioning stage choose 'Manual'. What you want to do is to tell the installer to re-use the old root partition as the new one and to reformat it. (Don't worry about the swap partition - that'll be picked up automatically. I can't give you more details of the design of the installer at this stage because this is where it differs from release to release. It's fairly straightforward but can be a bit baffling if you're not used to it.

If you don't like that approach, go back to where you'd opened the Partition Editor. Mark the two Linux partitions for deletion. There might now be an empty extended partition. Mark that for deletion as well. Now click 'apply'. If all goes well the space formally used by Linux is now showing as unallocated. Leave it so and close the partitioner. Now start the installer.

At the partitioning stage, select 'Guided - use the largest continuous free space'. The installer will set up the partitions for you and when you have OK'd that, it will install the system, and reinstall the grub bootloader as a dual-boot for you.

Usual caveats. Things can go wrong when you use a partitioner. Back up any valuable data before starting and if you have data you want to retrieve from the old Ubuntu install, you can do that from the live CD. Before you start either the partitioner or installer, use the Places menu to find and mount your root partition, navigate to /home/yourusename and copy anything you want to a USB drive. Unmount the old root partition before using the partitioner or installer.

---

### Post by Mmmtobacco on 2009-04-09
FIXED

thanks very much. everything works great now. ):P

---

### Post by mcloser on 2009-04-09
> **Mmmtobacco said:**
> FIXED

thanks very much. everything works great now. ):P


hi coffeecat, something similar happened to my intrepid. i'm reclaiming stuff that i want to keep before paving it over, maybe with xubu ???

thanks for your help, there's a lot more people than just the onewho wrote the original email that you help, all us newbies will hit stuff like this.

now if I could only find a good thread to tell me how to install my ubu x64 along with my vista I would be really in clover.  GRUB dosen't seem to handle vista very well.

thx

---

### Post by soltanis on 2009-04-09
If you need to save some files before doing a re-install, you can extract them off the disk using a live CD (like the Ubuntu one for example, knoppix also works) and copying them to a flash drive or something.

In the future, if you ever get the chance to repartition, I would advise you to create a separate partition (with lots of spare space, I would make it the same size or even twice as big as your / partition if you like multimedia) for your /home directory. That way, if you ever need to reinstall or even decide to switch distributions, you can do that by simply installing the new distro to your root partition, and still having your /home partition with all your documents/music/videos/projects.

---

