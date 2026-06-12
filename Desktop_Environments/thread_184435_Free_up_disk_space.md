---
title: "Free up disk space"
date: 2006-05-29
forum: Desktop Environments
---

### Post by gte258v on 2006-05-29
What are some things I can do to free up some extra disk space?  I read somewhere about freeing disk space in Mac OS X by removing localizations.  Can I do something similar in Ubuntu, and if so, how would I do it?  There's no reason for me to have support for a bunch of languages I don't speak.  Any other ideas for freeing up space I didn't know I had?  Thanks for the help.

---

### Post by rcarring on 2006-05-29
Once you are sure that updated packages installed correctly and work as expected, you can use synaptic to remove the cached deb files. I think it is recommended to do this periodically.

---

### Post by aysiu on 2006-05-29
There's an option in Synaptic to just not keep .deb files after using them for installation.

---

### Post by jimrz on 2006-05-29
[QUOTE=aysiu]There's an option in Synaptic to just not keep .deb files after using them for installation.[/QUOTE]

aysiu-

   Will changing this setting cause Synaptic to delete .deb files retained from before the change? If not, how di I go about removing them?

---

### Post by aysiu on 2006-05-29
[QUOTE=jimrz]aysiu-

   Will changing this setting cause Synaptic to delete .deb files retained from before the change? If not, how di I go about removing them?[/QUOTE] Take a look at the image I posted--see that button that says *delete cached package files*? Press that to delete what's already been downloaded.

These files live in /var/cache/apt/archives. You can double-check this folder to see if they really got deleted.

---

### Post by jimrz on 2006-05-29
[QUOTE=aysiu]Take a look at the image I posted--see that button that says *delete cached package files*? Press that to delete what's already been downloaded.

These files live in /var/cache/apt/archives. You can double-check this folder to see if they really got deleted.[/QUOTE]

OOOPs...saw that when went to change the setting, by the time I got back you had already responded (boy you gotta be the quickest participant on these forums)

thanks  - jim

**EDIT** and certainly one of the most effective

---

### Post by gte258v on 2006-05-30
[QUOTE=rcarring]Once you are sure that updated packages installed correctly and work as expected, you can use synaptic to remove the cached deb files. I think it is recommended to do this periodically.[/QUOTE]

Thanks.  This was exactly the sort of thing I was looking for.  While that option in synaptic works fine, is there a way to set the same option at the command line?

---

### Post by henriquemaia on 2006-05-30
[quote=gte258v]Thanks.  This was exactly the sort of thing I was looking for.  While that option in synaptic works fine, is there a way to set the same option at the command line?[/quote] 
run

```
sudo apt-get clean
``` 
or 

```
sudo apt-get autoclean
``` 
The difference is that clean clears out  the  local  repository  of  retrieved  package files and autoclean clears  out the local repository of retrieved package files but  only  removes package  files that can no longer be downloaded, and are largely useless.

ps: the clean/autoclean explanation was copied from apt-get's manual page.

---

### Post by dtfinch on 2006-05-30
I've made the mistake of forgetting to empty the trash, making backups of my home folder including ~/.Trash, deleting old backups (to my trash), repeating... leaving me with many more copies of everything than I previously thought, stored recursively in folders named .Trash. Curious I've never made this sort of mistake on Windows.

---

### Post by marwal on 2006-05-30
Freeing diskspace - i think - involves more than 'apt-get autoclean'. language-packs for languages you don't speak, documentation, thumbnails, the examples-folder, unused themes, old logfiles, ... there must be a Gb or two waiting to be set free. Some guide for this - like how much can you strip away and still have a working system -  would be fun and educational to read.

---

### Post by ssam on 2006-05-30
you could clear out your ~/.thumbnails

it is where nautilus caches thumbnails of any thumbnailable files you look at. it can get quite huge after a while (i have seen it several hundred MB)

---

### Post by FredB on 2006-05-30
[QUOTE=marwal]Freeing diskspace - i think - involves more than 'apt-get autoclean'. language-packs for languages you don't speak, documentation, thumbnails, the examples-folder, unused themes, old logfiles, ... there must be a Gb or two waiting to be set free. Some guide for this - like how much can you strip away and still have a working system -  would be fun and educational to read.[/QUOTE]

Well, in order to get back some space, here are my steps :

```
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get clean
```

Where there is a lot (more than 10 packages) of upgraded packages, it really helps ;)

After all, my 80 Gb HD is having around 85% free with ubuntu, firefox, thunderbird and seamonkey source code + building tools ;)

---

### Post by matrooswolf on 2006-05-30
Thanks!  This cleared a whooping 3.2 GB on my disk!

One thing that was also eating diskspace away was Beagle, its index was 4 GB (if I remember well), (but I let it index my windows partition as well, which was maybe a bit too much).  I turned it off.

---

### Post by henriquemaia on 2006-05-30
[quote=ssam]you could clear out your ~/.thumbnails

it is where nautilus caches thumbnails of any thumbnailable files you look at. it can get quite huge after a while (i have seen it several hundred MB)[/quote]

You're right. Mine is 1.2 Gb now. That's a lot of space.

---

### Post by benhall on 2006-05-30
I find that a nice gui for looking at disk usage is filelight- it displays everything in an attractive logical form making it easier for clearing out unwanted files.

---

### Post by Horizon on 2006-05-30
[QUOTE=benhall]I find that a nice gui for looking at disk usage is filelight- it displays everything in an attractive logical form making it easier for clearing out unwanted files.[/QUOTE]
Cool, nice little program that is. using the commandline to check disk usage just feels too boring and unintuitive.

---

### Post by simplyw00x on 2006-05-30
```
sudo apt-get install localepurge
sudo localepurge
```
This will remove unecessary locales.

Also, try
```
sudo apt-get install baobab
```
That program shows you disk usage by folder. 

Also, try uninstalling old kernels through synaptic as they use about 300-400MB each.

---

### Post by matrooswolf on 2006-05-30
[QUOTE=aysiu]Take a look at the image I posted--[/QUOTE]
Sorry, completely OT, but Aysiu, I like your screenshot a lot, could you tell me more about the theme, font, (+ fontsettings)?  It looks nice sober and sharp.

---

### Post by aysiu on 2006-05-30
[QUOTE=matrooswolf]Sorry, completely OT, but Aysiu, I like your screenshot a lot, could you tell me more about the theme, font, (+ fontsettings)?  It looks nice sober and sharp.[/QUOTE] I'm using KDE with the Plastik theme, and I think Bitstream Vera Sans as my font.

---

### Post by matrooswolf on 2006-05-30
Thanks!  I was looking in the gnome themes I have installed, now I now why I didn't find it ;)

---

### Post by ketsugi on 2006-05-30
[QUOTE=matrooswolf]Thanks!  This cleared a whooping 3.2 GB on my disk!

One thing that was also eating diskspace away was Beagle, its index was 4 GB (if I remember well), (but I let it index my windows partition as well, which was maybe a bit too much).  I turned it off.[/QUOTE]

You might want to look into using extended attributes for your file system to reduce the index files. I have my Windows partition (8.2G in use) indexed, along with my home folder (20G in use), and my index file is only 70mb big.

I can't remember where the thread is but search the forum for "beagle" and "xattr".

---

### Post by cmarker on 2006-05-30
this is a great way to clean up lots of old thumbnails that you have not looked at in 7 days:

```

$find ~/.thumbnails -type f -atime +7 -exec rm {} \;

```

The source for this code and more information about it is here:
[http://ubuntu.wordpress.com/2006/02/15/clean-up-old-thumbnails/](http://ubuntu.wordpress.com/2006/02/15/clean-up-old-thumbnails/)

---

### Post by Skye on 2006-05-30
I've found that there are quite a few packages in synaptic that can be removed to free up space, especially the foreign font packs.  They usually go under the name of ttf-*region*.  

Also, you can remove various things in synaptic that you don't need.  My computer doesn't have bluetooth, so I removed all the things associated with bluetooth from synaptic.  I also don't use evolution, so I removed that as well.

It's time consuming, but you can just go down the list of installed programs looking for things you don't want or need- but be careful not to remove something critical to the system.

---

### Post by matrooswolf on 2006-05-30
[QUOTE=ketsugi]You might want to look into using extended attributes for your file system to reduce the index files. I have my Windows partition (8.2G in use) indexed, along with my home folder (20G in use), and my index file is only 70mb big.

I can't remember where the thread is but search the forum for "beagle" and "xattr".[/QUOTE]

Thanks I'll look into that (first get some sleep ;) 
I let Beagle index about 200GB which is a bit too much and not really necessary.

I have read something about xattr, but is that still necessary in Dapper (I mean as beagle is installed by default, shouldn't this work already?)

---

### Post by matrooswolf on 2006-05-30
[QUOTE=Skye]I've found that there are quite a few packages in synaptic that can be removed to free up space, especially the foreign font packs.  They usually go under the name of ttf-*region*.  

Also, you can remove various things in synaptic that you don't need.  My computer doesn't have bluetooth, so I removed all the things associated with bluetooth from synaptic.  I also don't use evolution, so I removed that as well.

It's time consuming, but you can just go down the list of installed programs looking for things you don't want or need- but be careful not to remove something critical to the system.[/QUOTE]

Is there a way to remove packages in a safe way (there are a lot of packages of which I have no idea what they are doing), or do we still have to wait for that? (Smart?)
Oops, I see that there is already a thread about that ...
[http://www.ubuntuforums.org/showthread.php?t=182437](http://www.ubuntuforums.org/showthread.php?t=182437)

---

