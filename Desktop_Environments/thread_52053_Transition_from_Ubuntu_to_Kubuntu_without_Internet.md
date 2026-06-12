---
title: "Transition from Ubuntu to Kubuntu without Internet"
date: 2005-07-26
forum: Desktop Environments
---

### Post by Ruskie on 2005-07-26
Hello,

I'd like to install the KDE enviroment on my ubuntu box; I've read in the Kubuntu.org faq how to do that (basically, apt-getting some packages from ubuntu repository).

Unfortunately, I don't have a broadband connection at home, so here's what I am planning to do:

1) getting the packages at office and saving them on my usb-key;
2) Copying it in a directory on my box
3) Transforming it in a local repository following these instructions:

> 
I created a directory "/home/mylogin/local_packages" and
downloaded the files I wanted to install into the directory
then...cd to that directory and run... 

sudo dpkg-scanpackages . /dev/null | gzip -9c > Packages.gz
(Note the "." and the capital "P")

This creates the Packages.gz file which Synaptic uses. (a directory of the files in the folder)

And then I added the following line to /etc/apt/sources.list:
deb file:/home/mylogin/local_packages ./

After this I started Synaptic and reloaded and the files are now incorporated. 


4) Apt-getting them from the local repository


In this way I hope to minimize the connection time required to install KDE... Do you see any problem in it?

I only see one: where do I get those packages? I know the names, but I don't know where to look for them! I tried browsing ubuntu repository from the web, but it is all made of bzipped files, I can't find any single package...
So the main question is: where can I find the kubuntu package for download?

Thank you very much anybody can help
Marco

---

### Post by derrick1985 on 2005-07-26
Can't you get the Kubuntu cd, add it to your etc/apt/sources.list file like the ubuntu cd is, and do it that way?

---

### Post by Ruskie on 2005-07-26
[QUOTE=derrick1985]Can't you get the Kubuntu cd, add it to your etc/apt/sources.list file like the ubuntu cd is, and do it that way?[/QUOTE]
 Uhm... I suppose I can, but I don't see why I should download and duplicate a lot of packages I don't need just to get the three I do...

I mean, if I don't find the three package I can do what you suggest, but getting the three packages alone would be better...

Thanks
Marco

---

### Post by elsewhere on 2005-07-26
[QUOTE=Ruskie]Uhm... I suppose I can, but I don't see why I should download and duplicate a lot of packages I don't need just to get the three I do...
[/QUOTE]

You'll find it's more than 3 packages... the kubuntu-desktop package is a metapackage that will require the kde core files + any ubuntu-specific libraries etc. that may or may not have been installed as part of your ubuntu installation.  The accessories / add-ons / dev are extra as well.  You're probably looking at around 20 packages for a base kde install with kubuntu customizations, more if you're looking for all the extras.

Still, you could probably fit it on a usb key of moderate capacity, but you'll have to make sure you have all the dependencies filled.  You can find the files at [http://archive.ubuntu.com/ubuntu/main/pool](http://archive.ubuntu.com/ubuntu/main/pool) where they're sorted by sub-directory alphabetically, and then by package.  You'll have to go into each package sub-directory individually and download the correct package file.  You can use synaptic to check the dependencies for kde and kubuntu-desktop you'll require, although many of them (particularly in kubuntu-desktop) are likely already on your ubuntu system.

Having said all that, I think you'll really find it easier to burn the .iso to CD, if only to avoid the chance of missing a required package and not being able to complete your install.

Hope this helps either way...

Cheers,
KV

---

### Post by Ruskie on 2005-07-27
[QUOTE=elsewhere]You'll find it's more than 3 packages... the kubuntu-desktop package is a metapackage that will require the kde core files + any ubuntu-specific libraries etc. that may or may not have been installed as part of your ubuntu installation.  The accessories / add-ons / dev are extra as well.  You're probably looking at around 20 packages for a base kde install with kubuntu customizations, more if you're looking for all the extras.

Still, you could probably fit it on a usb key of moderate capacity, but you'll have to make sure you have all the dependencies filled.  You can find the files at [http://archive.ubuntu.com/ubuntu/main/pool](http://archive.ubuntu.com/ubuntu/main/pool) where they're sorted by sub-directory alphabetically, and then by package.  You'll have to go into each package sub-directory individually and download the correct package file.  You can use synaptic to check the dependencies for kde and kubuntu-desktop you'll require, although many of them (particularly in kubuntu-desktop) are likely already on your ubuntu system.

Having said all that, I think you'll really find it easier to burn the .iso to CD, if only to avoid the chance of missing a required package and not being able to complete your install.

Hope this helps either way...

Cheers,
KV[/QUOTE]
 Okay, thanks a lot for hints!

---

