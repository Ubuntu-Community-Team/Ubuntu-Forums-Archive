---
title: "Stupid question about installing applications"
date: 2008-12-03
forum: General Help
---

### Post by Rocket Sock on 2008-12-03
Ok, I just got back into using ubuntu (This time for the long haul). 
One thing that I never quite got is, where is synaptic and add/remove programs saving everything to? I've got a small / partition and my large /home partition, which does it save the applications and such to? And If Its /, then how do I change it?

Another stupid question along the same lines, what goes on when the package managers work? Obviously they download, unpackage, and install, but do they delete all then junk, like the source files or whatever (Im new, bear with me please).

---

### Post by girishsasikumar on 2008-12-04
Well for you first question, the files are saved in 
```
/var/cache/apt/archive
```
U can take a look of this folder and it would contain most of the packages you have downloaded and installed.

U can change whether your package manager saves your downloaded deb packages or deletes it using "synaptic package manager -> preferences -> ".

Regarding your question on how to change your apt-get cache i recommend this post
[http://ubuntuforums.org/showthread.php?t=144779]("http://ubuntuforums.org/showthread.php?t=144779")

I feel it is better to keep your deb packages as long as you dont have a serious hard drive space constrain because it helps in creating apt-on-cd like in below 
[http://aptoncd.sourceforge.net/]("http://aptoncd.sourceforge.net/")

---

### Post by Rocket Sock on 2008-12-04
Thanks, I did get a responce on that from another of my posts, but I'm still confused, and my post isnt exactly getting alot of attention, so perhaps one of yall can clear this up.

When I was getting ubuntu set up, I looked around for the "best" partition set up. 
I got :
10 GB /
2GB swap
and whatevers left to /home

Now, since apparently, programs are installed to / by default (And Im assuming if I change it, the important files that I keep root for will too?), what is my best option? I plan on installing a good number of linux apps, and just as many apps and games under Wine. I've already installed several things such as Wine. 

My question is, what would you advise I do?

---

### Post by linorics on 2008-12-04
I'm not totally understanding what your asking, however this is my knowledge on the subject. 

synaptic and other programs install thing's normally in 
/bin, /usr/bin, and /sbin

also look into using "apt-get" to install software too. Its a shell tool, so no pretty gui, but it works really nice. 

Also when I'm trying to find where a program is installed I use
"whereis nameofprogram" so an example would be

Input:
whereis apache2

Output:
apache2: /usr/sbin/apache2 /etc/apache2 /usr/lib/apache2 /usr/share/apache2 /usr/share/man/man8/apache2.8.gz

So you can see all the places that have apache2 in them.


hope this helped a little :)

---

### Post by ajcham on 2008-12-04
I would have advised a little more than 10GB for /

I'm currently using just shy of 10GB on my 15GB / partition, and I expect I'll cross the threshold soon enough.

That said, don't worry about your Wine apps.  Wine installs software into a virtual C: drive in your home partition (/home/*USERNAME*/.wine/drive_c), so those programs will not consume your / partition.

---

### Post by Rocket Sock on 2008-12-04
> **ajcham said:**
> I would have advised a little more than 10GB for /

I'm currently using just shy of 10GB on my 15GB / partition, and I expect I'll cross the threshold soon enough.

That said, don't worry about your Wine apps.  Wine installs software into a virtual C: drive in your home partition (/home/*USERNAME*/.wine/drive_c), so those programs will not consume your / partition.

Ok, well that makes things easier. So If i plan on using more than just a few apps that I get through the package managers, you would advise more space put to /?
Is there a way to repartition ubuntu, because just getting this thing set up on my MBP was a pain enough (The installation was easy, it was just getting the damn thing to boot)

---

### Post by ajcham on 2008-12-04
> **Rocket Sock said:**
> Ok, well that makes things easier. So If i plan on using more than just a few apps that I get through the package managers, you would advise more space put to /?


It's difficult to say, without knowing how you intend to use the system.  In retrospect though, a 10GB / partition was probably better advice than I gave it credit for. You can install well more than just a few apps in that space.  As I said, I am still under that threshold myself, and if I'm honest I have a lot more installed than I really need, such as games I don't play, or multiple apps for the same purpose when I really only need one or two of them.

I also have both Gnome and KDE installed, along with a plethora of apps that come bundled with each, not to mention several other Window Managers.  If you stick with a single Desktop Environment, you will use far less space.

For me, I like trying out a range of software, and if there's no urgent need to remove it I'm happy to leave it there, just in case I should ever decide to use it again.  If I were running low on space there must be several GB I could free up without missing anything.

---

### Post by CatKiller on 2008-12-04
> **Rocket Sock said:**
> Ok, well that makes things easier. So If i plan on using more than just a few apps that I get through the package managers, you would advise more space put to /?

10 Gigs is a **lot** of apps. Some of the games are quite big though, as you'd expect, with maps, textures, sounds and so on. If you find out that you're running out of space, then 10 Gigs wasn't quite enough. If you don't, then it was fine.

```
sudo apt-get clean
``` is a quick way to remove the cached package files.

> Is there a way to repartition ubuntu, because just getting this thing set up on my MBP was a pain enough (The installation was easy, it was just getting the damn thing to boot)

Yes. It's quite straightforward. Boot from the Ubuntu cd (since you can't modify a partition that's mounted, and your / partition is necessarily mounted to run the program in the first place). Run System -> Administration -> Partition Editor. This runs GParted, which is a simple graphical tool to manage your partitions. Make your /home partition smaller by dragging the right-hand end of the box that represents it to the left. Then drag the whole box to the right, effectively moving the unpartitioned space to the right of your / partition. Then make your / partition larger by dragging the right hand-end of its box to the right.

You will now have transferred some free space from your /home partition to your / partition.

If your swap partition is between these two partitions, then you'll need to move that too. This will have been automatically mounted for performance reasons. You can unmount it with the command ```
sudo swapoff -a
```

---

