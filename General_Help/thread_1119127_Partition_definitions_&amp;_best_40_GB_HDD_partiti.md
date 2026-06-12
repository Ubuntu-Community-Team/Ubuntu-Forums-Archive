---
title: "Partition definitions &amp; best 40 GB HDD partitions configuration?"
date: 2009-04-07
forum: General Help
---

### Post by neotester on 2009-04-07
I have recently installed Ubuntu 8.10 by default. It took control of all my HDD. It's OK. I intend to use Ubuntu all over my HDD but I know there is a recommended partitioning configuration.

I also don't know what / stands for or /boot or /etc or... everything regarding partitioning. I only know it's recommended that when you install Linux it's best that you create the SWAP 1.5 or 2 times your RAM memory. I have 512 MB RAM memory and 40 GB HDD and that EXT3 is the best file system format.

I would like to know what are the equivalents of Windows partitions in Linux and how much space I should give to each one (like what's the Linux equivalent for C:\Windows?) because I got somehow confused and don't know where to install software, where is ment to unpack software (looked around and realised Ubuntu loves .DEB's and let's say a new version of Mozilla Firefox I want to install - I'm going for terminal actions; I mean I would like to use ADD/REMOVE as a last resort, I want to know the logic in Linux).

How can I install Ubuntu (Linux mostly) right? Where are the personal files? Where are other partitions I can use but not loose when I reinstall Ubuntu?

---

### Post by mb_webguy on 2009-04-07
Here's a brief overview of the [Filesystem Hierarchy Standard]("http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard") used by Linux.

As a comparison to the Windows filesystem...

The root ("/") directory is roughly equivalent to C:\, although in a way it's more like My Computer, since in Linux partitions are mounted as directories within a unified filesystem rather than as independent "drives".  *Everything* is located somewhere under the root directory.

The /usr and /opt directories are equivalent to Program Files.  The /usr directory is for software installed through a package manager.  Software installed using a deb, by compiling from source, or by running and installer script or binary is usually located in /usr/local (as in "this software was installed locally, rather than through the distribution repos"), although it's occasionally located in /opt (as in "optional software").

The /home directory is obviously like the Documents and Settings folder, as it contains user data.

The /bin and /sbin directories are vaguely similar to the Windows directory, as they contain all of the OS-specific binaries.  The /bin directory contains all of the things a user would normally run, while the /sbin directory contains things primarily used by the system itself.

The /tmp directory is obviously like the Windows temp folder.

The /etc and /var directories don't have direct analogues on Windows.  The /etc directory contains system-wide configuration files, while the /var directory contains system-wide data files (such as system logs).

The /boot and /dev directories likewise don't have clear Windows equivalents.  The /boot directory contains the bootloader and other things needed to actually boot the OS.  The /dev directory contains all of the system device files, which allow software to interact with device drivers using standard I/O system calls.

The /media and /mnt directories are like My Computer in that they're where removable media are mounted.  The /mnt directory was originally where such devices were mounted, but the /media directory has pretty much completely taken over this role.  The /mnt directory is still a good place to put temporary mount points.

I think that covers most of the directories you're likely to actually deal with...

---

### Post by mb_webguy on 2009-04-07
As for partitioning schemes, for a personal computer (as opposed to a server) I like to have a separate /home directory.

Linux and a large number of applications can live happily on an 8GB partition.  I currently have my root directory on a 12GB partition, and I'm only using 5.6GB even though I have a *lot* of software installed.  Your /home partition can then use the rest of the drive space.  Doing this allows you to easily reinstall the OS if you need to without having to backup and then restore all of your user data.  (Backing it up is still a good idea, though.)

---

### Post by neotester on 2009-04-10
Okay. I took notes and I read the Wikipedia FHS.

Taking into considerration your recommendations I'm asking you if this partitioning configuration would be good next time I reinstall Ubuntu:

/             - 0,5GB - I have read [here]("https://help.ubuntu.com/8.04/installation-guide/powerpc/directory-tree.html") that a size like this is more than enough
/usr          - 4 GB  - *"A generous workstation or server installation should allow 4&#8211;6GB. "*
   /usr/local - 2 GB
/opt          - 4 GB
/home         - 10GB
/bin          - 3 GB
/sbin         - 3 GB
/tmp          - 2 GB
/etc          - 1 GB
/var          - 1 GB 
/dev          - 1 GB
/mnt          - 1 GB 
/media        - 2 GB
SWAP          - 1 GB
Feel free to corret me and recommend me better options.

Now, here's where I'm still confused: if I'm going to reinstall Ubuntu and I create the **/home**, this would be the partition (with my **personal data as in music, videos, docs**) that another time I choose to reinstall, won't disapear? I mean if I create it, it would be separate, right?

And let's say I would like to install **Mozilla Firefox**, I download the package (**through Synaptic Package Manager**), it will install into the **/usr partition** right? But is there another *"natural"* way I can install Firefox rather than through a package manager? Because I read on Psychocats that Ubuntu loves .DEBs so I said to myself *"Oh, cool, I'm going to look for .debs for each software, making my own <<library>> of .DEBs and I'll just install them whenever I want to"*. But that's when you guys tell me .DEBs go into /usr/local or occasionally into /opt. Is that good for the Linux system? It won't somehow damage it? Or, using the package manager Synaptic is the best way becase it's safer and... I guess because whenever I install software through it it's easier to uninstall it too?

The reason I'm asking this is because I would like to know how to install Ubuntu better and how to better install software I will use in the future.

---

### Post by drs305 on 2009-04-10
The only partition you must set up is /. You can add a /home and a /swap partition. The other ones you mentioned really don't need to be on their own partition for a normal user and will just complicate things for you. The sizes of each of the remaining folders will be expanded or contracted automatically. All you have to do is ensure the parent / folder has enough space (You can get by with a minimum or about 5, 8GB would probably be enough  but I'd allow for growth as recommended).

For basic setup, here is a good site for planning your installation. See particularly the section on planning partitions:
[http://www.psychocats.net/ubuntu/index]("http://www.psychocats.net/ubuntu/index")

You are correct about a separate /home surviving an upgrade, *as long as during the upgrade you identify the /home partition and don't format it* (if doing a clean install). On an on-line update, the data on your /home file won't be lost.

---

### Post by neotester on 2009-04-10
Psychocats was my first Linux documentations.
It says there: *"If you choose to create a separate /home partition, allocate between 5 and 10 GB for the / partition—that's about all you'll need for the Ubuntu system and programs. The rest should be for your personal files (in /home). "*

So I can basically create the / partition with 10 GB and /home partition with another 10 GB and use Linux this way in pretty good conditions and non-worries (like upgrading on-line or reinstalling Ubuntu without formating the / and /home) until I find out more about it?

---

### Post by drs305 on 2009-04-10
> **neotester said:**
> Psychocats was my first Linux documentations.
It says there: *"If you choose to create a separate /home partition, allocate between 5 and 10 GB for the / partition—that's about all you'll need for the Ubuntu system and programs. The rest should be for your personal files (in /home). "*

So I can basically create the / partition with 10 GB and /home partition with another 10 GB and use Linux this way in pretty good conditions and non-worries (like upgrading on-line or reinstalling Ubuntu without formating the / and /home) until I find out more about it?

It depends on where you plan on keeping your data and whether any other OS will be on the system. What would you be using the extra 20GB for? If you plan on keeping all your data within the /home folder you probably will want it larger than 10GB if you don't have any other use for the space. Many users following psychocat's setup would make / 10GB and use the rest for /home, so you would make the /home as large as the remaining space allows (reserving a GB or so for swap).

---

### Post by neotester on 2009-04-10
That's what I ment. 10GB for /, 1GB swap and the rest of it in /home.

---

