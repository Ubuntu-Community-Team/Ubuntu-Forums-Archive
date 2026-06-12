---
title: "No build-essential no internet access"
date: 2006-07-22
forum: Desktop Environments
---

### Post by john_spiral on 2006-07-22
Hi,

I've done a hd install of xubuntu, similar to a dapper server install, from the xubuntu-6.06-alternate-i386.iso file, without burning a CD.

My question is simple, how does one get **make ** or **build-essential** going without net access.

Make is needed to install an USB ADSL dialler from source.

I've tried installing make via the build-essential_11.1_i386.deb file through the below command:

[FONT="Arial Narrow"]dpkg -i build-essential_11.1_i386.deb[/FONT]

it just moans about a zillion dependencies :-(

I'm hoping to share this info in the form of a HOWTO once I get my head round the whole process. The HOWTO will be aimed at old systems that don't have a CD like a lovely old sony vaio laptop.

When you reach the pearly gates, St Peter, and avid Ubuntu fan, will look most favorably upon thee for your assistance.

---

### Post by asplode on 2006-07-22
I'm under the impression that there is a Ubuntu Plus CD running around somewhere with multimedia and build essentials on it...

Also, something to keep in mind is certain programs require additional development libraries to compile, something that is above and beyond the normal scope of the build-essential metapackage.

---

### Post by mlind on 2006-07-22
I'm not sure about the xubuntu CD, but build-essential package should on the cd media, it's just not installed by default.
At least alternate install cd contains build-essential package.


If you don't have the cdrom, you need the .iso image. Mount it using loopback device
```

sudo mkdir /mnt/image
sudo mount -o loop dapper_image.iso /mnt/image

```

**/cdrom** symlink needs to point to this mount point (or /media/cdrom if you actually have a cdrom)
```

sudo ln -sf /mnt/image /cdrom
sudo apt-cdrom add

```

This should have added new entry to /apt/sources.list.
```

sudo aptitude update
sudo aptitude install build-essential

```
Should install build-essential from mounted image/cdrom.


If you modified /cdrom symlink, correct it the way it was
```

ln -sf /media/cdrom /cdrom

```

---

### Post by aysiu on 2006-07-22
The *build-essential* package isn't installed by default, but it is included on all copies of Ubuntu, Kubuntu, and Xubuntu (both Alternate and Desktop).

---

### Post by john_spiral on 2006-07-23
Hi thanks for the responses,

](*,) 

After typing:

sudo apt-cdrom add

I get the following error:

[FONT="Courier New"]using CD-ROM mount point /cdrom/
unmounting CD-ROM
waiting for disc
Please insert a Disc in the drive and press enter
mounting CD-ROM
E: Failed to mount the cdrom
[/FONT]

I even tried setting up the symbolic link as follows:

sudo ln -sf /mnt/image /cdrom/image

same error with a another code below.

any ideas?

more info:

I can access the mounted cdrom through /mnt/image

I'm mounting the following file: xubuntu-6.06-alternate-i386.iso

---

### Post by mlind on 2006-07-23
> **john_spiral said:**
> Hi thanks for the responses,


I even tried setting up the symbolic link as follows:

sudo ln -sf /mnt/image /cdrom/image

same error with a another code below.

any ideas?


It should be 
```

sudo ln -sf /mnt/image **/cdrom**

```

---

### Post by john_spiral on 2006-07-23
I tried:

sudo ln -sf /mnt/image /cdrom

and got the error above, I even tried

sudo ln -sf /mnt/image /cdrom/image 

and got the same error message, with a number below.

any ideas?

---

### Post by mlind on 2006-07-23
> **john_spiral said:**
> I tried:

sudo ln -sf /mnt/image /cdrom

and got the error above, I even tried

sudo ln -sf /mnt/image /cdrom/image 

and got the same error message, with a number below.

any ideas?

I just tried with .iso image and got it working

```

sudo mount -o loop cd.iso /mnt/image
sudo rm /cdrom
sudo ln -s /mnt/image /cdrom
sudo apt-cdrom **-m** add

```

ln -sf didn't overwrite the symbolic link like I expected, and apt-cdrom needs -m parameter so it won't try to mount anything by itself.

---

### Post by john_spiral on 2006-07-23
I'll give it a try thanks.

---

### Post by john_spiral on 2006-07-23
yes that did the trick, thanks very much ;)

---

### Post by mlind on 2006-07-23
> **john_spiral said:**
> yes that did the trick, thanks very much ;)

Were you able to install build-essential and its dependencies from the CD image?

---

### Post by az on 2006-07-23
All of the dependencies to build-essential (as well as linux headers and a whole lot others) are on the desktop cd as well as the alternate cd.

The Desktop cd has a repo that is apart from the live session.  Once installed and at the desktop, you have to reinsert the live cd and add the cd to your list of repos.

Simply typing 

sudo apt-cdrom add

should do the trick.  In ubuntu, inserting any cd with a repo on it ilwll start the package manager and you are good to go.


I don't know if this is the case with Xubuntu.

---

### Post by mlind on 2006-07-23
> **azz said:**
> All of the dependencies to build-essential (as well as linux headers and a whole lot others) are on the desktop cd as well as the alternate cd.

The Desktop cd has a repo that is apart from the live session.  Once installed and at the desktop, you have to reinsert the live cd and add the cd to your list of repos.

Simply typing 

sudo apt-cdrom add

should do the trick.  In ubuntu, inserting any cd with a repo on it ilwll start the package manager and you are good to go.


I don't know if this is the case with Xubuntu.

I'm not sure if you read the whole thread, but partial problem was that machine didn't have a cdrom drive. It was solved though using mounted cd image with apt-cdrom.

---

### Post by az on 2006-07-23
> **mlind said:**
> I'm not sure if you read the whole thread, but partial problem was that machine didn't have a cdrom drive. It was solved though using mounted cd image with apt-cdrom.

Aaah!  My bad.

---

### Post by john_spiral on 2006-07-24
***removed duplicate post***

---

### Post by john_spiral on 2006-07-24
I got build-essential going from the mounted .iso file no probs. It installed all the dependencies without a hitch.

:p

I'll be putting this info in a howto shortly using the useful commands from this thread.

On the same machine I'm attempting to setup a USB ADSL modem, having skipped the network portion of the install process.
Looks like I'm missing a pppd file or branch of files.

Is there a sudo aptitude install xxxxx command I can run to get the relevant networking files installed? In the long run I hope to use the system as a LAMP platform.

Thanks John

---

