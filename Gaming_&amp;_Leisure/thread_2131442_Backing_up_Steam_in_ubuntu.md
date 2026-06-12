---
title: "Backing up Steam in ubuntu"
date: 2013-04-01
forum: Gaming &amp; Leisure
---

### Post by bartos on 2013-04-01
Has any one backed up Steam on Linux or specifically Ubuntu? I am using the Steam Linux client, not wine.

I am wondering what folders are needed to be saved to back up steam so I don't have to reinstall all games.
Has any one restored there folders and had steam work right away?

Thanks
Bart

---

### Post by Ranko Kohime on 2013-04-01
My assumption: hard drive crash, new system install, some other form where everything is wiped out but the backup.

My situation: I have on-site and off-site backup of most of ```
/home/ranko
```


That being said, all of the actual game payload should be stored in ```
~/.steam/Steam
```which is a symlink to ```
~/.local/share/Steam
```Best just to backup both to be on the safe side.  Restoring these will bring Steam up immediately once it's reinstalled, (you will still have to install it via the repo first, assuming that the OS was reinstalled), albeit the save data for each game being a different story.

Each individual game creates it's own save folder, though, for example: Amnesia the Dark Descent creates ```
~/.frictionalgames/Amnesia
```and Penumbra ```
~/.frictionalgames/Penumbra
```and World of Goo ```
~/.WorldOfGoo
```and so on.

If you don't want to backup your entire user folder (why not, if you have the backup space), then you'll have to hunt down each individual game's save folder yourself to include in the backup.

---

### Post by bartos on 2013-04-03
ok thanks .
will try it

---

### Post by bartos on 2013-04-09
Worked like a charm
Thanks

---

### Post by oldrocker99 on 2013-04-09
There is, also, the option to mount a separate partition as /home, so that when you reinstall, you select Something Else from the installer, mount and format your system partition /, and mount and NOT format the partition you use for /home. I've been using a second drive (sdb) entirely for /home, and on a laptop, I give / about 64-128 GB (plenty, I've found) and make a second partition and mount it as /home.

A good place to start:
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

If you have a single disk, doing this might take an hour or two, but it makes reinstalling a system just a matter of loading up all the software you had before, with all the settings preserved in .hidden directories in /home.

---

### Post by Perfect Storm on 2013-04-10
I have as oldrocker said, a seperated partition. I call that partition: /games (ext4)
All my games (steam, desura, LGP) goes to there. So whenever I feel in the mood to reinstall Ubuntu for whatever reason, I don't have re-install gigabytes after gigabytes.
I also have a multimedia partition and backup partition as well for other stuff :P
/multimedia (ext4)
/storage (ext4)

All of it is splitted between my HDDs, the total sum of 4 terabytes.

---

### Post by Ranko Kohime on 2013-04-10
> **oldrocker99 said:**
> There is, also, the option to mount a separate partition as /home, so that when you reinstall, you select Something Else from the installer, mount and format your system partition /, and mount and NOT format the partition you use for /home. I've been using a second drive (sdb) entirely for /home, and on a laptop, I give / about 64-128 GB (plenty, I've found) and make a second partition and mount it as /home.
The former is my current setup in my laptop.  I have an SSD for boot, and a 1TB HDD for /home.  Works nicely, and I've preserved my user folder for now 4 different versions of Ubuntu and a brief stint on Fedora 17.  Quite handy.  ;)

---

### Post by i4c on 2013-04-10
> **Artificial Intelligence said:**
> I have as oldrocker said, a seperated partition. I call that partition: /games (ext4)
All my games (steam, desura, LGP) goes to there. So whenever I feel in the mood to reinstall Ubuntu for whatever reason, I don't have re-install gigabytes after gigabytes.
I also have a multimedia partition and backup partition as well for other stuff :P
/multimedia (ext4)
/storage (ext4)

All of it is splitted between my HDDs, the total sum of 4 terabytes.

Very interesting, i have a few doubts if you don't mind me asking:

Do you have the gaming partition in the same harddrive as your OS ?
Do you execute the games and the respective configurations from that partition ?
How do u make ubuntu recognize(as in appearing in menus, gnome-do etc) the installed games(in games partition), since they aren't in home ?
Does the game being installed in a different partition from the OS affect how it performs(input lag,output lag, frames per second etc) ?

---

### Post by Perfect Storm on 2013-04-10
> Do you have the gaming partition in the same harddrive as your OS ?
No. I have that partition on another HDD.

> Do you execute the games and the respective configurations from that partition ?

The configuration/save game are saved in your home directory (usually hidden). But with steam games it save to the cloud. It doesn't matter if the games are on separate partition or on the same partition, you execute the games in the usual way.

> How do u make ubuntu recognize(as in appearing in menus, gnome-do etc) the installed games(in games partition), since they aren't in home ?

There are a few tricks to do this. 
1) the easist one: Backup the files (.desktop files) most of them can be found in your home directory (~/.local/share/applications) or if the game is installed systemwide (/usr/share/applications)
2) Write your own .desktop files and put them eg. systemwide and they'll pop in menus etc. etc.

> Does the game being installed in a different partition from the OS affect how it performs(input lag,output lag, frames per second etc) ?
It doesn't have an impact on the performance. I have internal HDDs, but it might have an impact if you use firewire/USB external HDD.

---

### Post by i4c on 2013-04-10
> **Artificial Intelligence said:**
> No. I have that partition on another HDD.



The configuration/save game are saved in your home directory (usually hidden). But with steam games it save to the cloud. It doesn't matter if the games are on separate partition or on the same partition, you execute the games in the usual way.



There are a few tricks to do this. 
1) the easist one: Backup the files (.desktop files) most of them can be found in your home directory (~/.local/share/applications) or if the game is installed systemwide (/usr/share/applications)
2) Write your own .desktop files and put them eg. systemwide and they'll pop in menus etc. etc.


It doesn't have an impact on the performance. I have internal HDDs, but it might have an impact if you use firewire/USB external HDD.

1 more question if u don't mind me asking, how do you install debs on your gaming partition ? I thought they could only be installed on the OS partition.

---

### Post by Perfect Storm on 2013-04-10
> 1 more question if u don't mind me asking, how do you install debs on your gaming partition ? I thought they could only be installed on the OS partition.
I rarely choose .deb files for games. ;)
Most games comes compressed or have installer script to choose from. Steam, Desura and LGP games(CDs/DVDs) you choose distination. Humble Bundle you can usually get them through Steam/Desura or they comes compressed.

---

