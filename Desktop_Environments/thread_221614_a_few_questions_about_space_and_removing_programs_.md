---
title: "a few questions about space and removing programs and on the fly partitioning"
date: 2006-07-23
forum: Desktop Environments
---

### Post by maddbaron on 2006-07-23
Hello, i need help with somethings...


how can i remove:
gnome files? I hve both gnome and kde on my laptop when i first installed i used gnome then switched to kde and prefer it. but when i boot up i see a lot of g"whatever" stuff running like gdm and other stuff, i assume kde stuff starts with a "k", i want to remove the "g" stuff since i need space in my root folder...

also how do i remove linux images since i believe every few updates brings a new linux image assume the old ones remain, when i boot up i see a lot of them....would that also free space?

how do i remove language packs also? all i need is the english ones?

lastly, when i installed i created a bunch of partitions, 2 of them i dont use. is it possible to unmount them and use the space they have by adding them to existing partitons without losing files or messing up the system?

thank u in advance to anyone who can help.

---

### Post by aysiu on 2006-07-23
In terms of making space, you'll probably free up more space by clearing out /var/cache/apt/archives (where all the installation files are) than by removing Gnome. You can clear that out with this command: ```
sudo apt-get clean
``` If you want to get rid of Gnome, though, try this: [http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde)

To remove old kernels, go to Adept and search for *linux-image* and just remove the older ones. That won't free up that much space, but it will make your boot menu less cluttered.

You can add partitions to existing ones if...

1. You have a live CD. You can't modify partitions that are in use.

2. The partition is *after* (to the right of) the partition you're trying to add to. You can't add to the beginning of a partition, only to the end.

---

### Post by maddbaron on 2006-07-23
> **aysiu said:**
> In terms of making space, you'll probably free up more space by clearing out /var/cache/apt/archives (where all the installation files are) than by removing Gnome. You can clear that out with this command: ```
sudo apt-get clean
``` If you want to get rid of Gnome, though, try this: [http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde)

To remove old kernels, go to Adept and search for *linux-image* and just remove the older ones. That won't free up that much space, but it will make your boot menu less cluttered.

You can add partitions to existing ones if...

1. You have a live CD. You can't modify partitions that are in use.

2. The partition is *after* (to the right of) the partition you're trying to add to. You can't add to the beginning of a partition, only to the end.


yeah i was searching the site the partitioning thing seems waaay to complcated for me so i'mma just leave it alone.

but do u know how i can make kde programs run when they need to run instead of gnome programs? like i see gdm running and kdm running if i am in kde gdm doesnt need to run does it? also when i open a file the default is nautilus instead of konqueror, how can i fix that?

i have included a copy of the var achieve u mentioned...can i delete everything in there? also i see a tmp folder is it safe to remove everything in there, i had a problem about a week ago with my tmp folder getting too full and stopping the system from loading. i ran apt-get clean and it removed EVERYTHING which wasnt a biggie tho i lost pic files. i wanna remove all the stuff that is just like junk.

i have been on a junk file removing mission since my problem a week ago lol...dont want it to happen again...

---

### Post by aysiu on 2006-07-23
```
sudo apt-get clean
``` shouldn't be removing picture files. It just clears out all the .deb files in /var/cache/apt/archives

I don't know why Nautilus is your default file manager. In KDE, it's usually Konqueror.

But to get GDM to stop how about just uninstalling it, since you apparently don't want Gnome... ```
sudo aptitude remove gdm
```

---

### Post by maddbaron on 2006-07-23
> **aysiu said:**
> ```
sudo apt-get clean
``` shouldn't be removing picture files. It just clears out all the .deb files in /var/cache/apt/archives

I don't know why Nautilus is your default file manager. In KDE, it's usually Konqueror.

But to get GDM to stop how about just uninstalling it, since you apparently don't want Gnome... ```
sudo aptitude remove gdm
```

i have no idea i tried everything to login in a week ago nothing worked then i saw that code and typed it as a last ditch effort and it worked but all my files were gone....it was really weird...

i will try removing the space eating files i find 1st so far i found hidden stuff in the .trash and other things i dont need and once the /var/cache stuff is removed thats another 200mb's free maybe the linux images free up some more space...

---

