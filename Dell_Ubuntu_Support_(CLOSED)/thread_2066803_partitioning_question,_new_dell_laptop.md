---
title: "partitioning question, new dell laptop"
date: 2012-10-05
forum: Dell Ubuntu Support (CLOSED)
---

### Post by mr michaelD on 2012-10-05
first time poster here.  i have a new dell inspiron 17R laptop and am trying to install ubuntu.  at present i am booted from the installer on a USB thumb drive and actually running just fine.  the laptop shipped with win7 preinstalled.  i have not run through the initial setup routines; i couldn't abide the MSFT EULA and 'crashed' the system without accepting them.  i then booted from the USB thumb drive into 12.04.1 LTS and am working in the partitioning tools.  for now i want to leave the windows partitions intact in the event i ever need them for anything and i would like to be able to poke around the pre-installed apps using WINE once i'm up and running.

i'm including screenshots of the map as reported by the ubuntu installer partition tool and gparted.  shouldn't i be able to simply shrink the sda3 and then create a new one for linux to use?  if i do shrink it, best guesses as to how much to leave allocated?  any opinions on whether i should use gparted or ...?

its notable that when i view the partition map from the ubuntu installer partition tool the sizes are not the same as what gparted reports; they're all larger [sda3 is 729074 mb].  should i be concerned about that?

thanx in advance

---

### Post by Bucky Ball on 2012-10-05
Welcome.

DON'T shrink sda3 with Gparted. This can cause major issues. Boot to Win and shrink it with the Win software there. Defragment a couple or several times before attempting this because Win tends to spew data all over the partition so you will get an inaccurate read of available space.

Give Win what it needs (just operating system then 30Gb but check minimum requirements) and once the Win partition is shrunk *using Win software*, reboot to the LiveCD to install Ubuntu. During the install you will get to the partitioning section.

* Choose 'Something Else'
* You will see the Win NTFS partitions there quite clearly; leave 'em alone
* Create free space with everything but the Win partitions
* Create an extended partition with the free space
* Install Ubuntu onto logical partitions inside that

Done. For more clues:

[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)

I advise you grab a pen and paper and perhaps beverage and make a plan before commencing this. Have it clear how you want to partition because there are many options. Will you want to share data between Win and Ubuntu? You will need an NTFS partition to do so because Ubuntu can read/write to NTFS and EXT (the filesystem used for Ubuntu) but Win can't read and write to EXT.

---

### Post by oldfred on 2012-10-05
In addition.

Your second screen shot shows sda3 as the location to install the boot loader. DO NOT do that, it both prevents you from booting with grub and corrupts the Windows NTFS partition. You should install the grub2 boot loader to sda not sda3. And Windows has to have its own boot info in every NTFS partition boot sector.

---

### Post by mr michaelD on 2012-10-05
@bucky ball & @oldfred ...

thank you kindly for the replies and the information.

i didn't notice or recognize the boot loader designation; i will set it to /dev/sda when i install.  it is defaulting to the USB stick i'm booting from, /dev/sdb. 

i'm kind of at a loss as to how to proceed, given the info provided.  i've yet to complete the initial set up of win7 and i can't say i really want to.  since i haven't set it up i can't boot windows to run the suggested tools to shrink the OS partition.  the biggest reason i don't want to do that is that i don't agree with the EULAs but can't proceed without checking them.  

the only reasons i'm inclined to keep the win7 partitions at all is in the event i need them down the road [i can't imagine what for though] and i'd like to be able to toy with some of the pre-installed apps via WINE once i'm up and running in linux.

at this juncture i'm tempted to just go ahead and use one of the partitioning utils to shrink the win7 OS slice down to about 30 gigs or so and take the chance.  if, after doing that it won't start up at all i'll likely go in after the fact, just delete the thing and resize the linux partition to reclaim the space.

thoughts ...?

thanks again

---

### Post by oldfred on 2012-10-05
Windows NTFS partitions have in its PBR the start and size of the partition like the info in the partition table. So when resized even by Windows tools, it automatically runs chkdsk to update that info. Sometimes from gparted other information seems to get changed and users have major issues, others have reported using gparted and then with chkdsk Windows is ok. But we normally suggest Windows tools for Windows and Linux tools for Linux just to be on the safe side. 

There are some third party Windows partitioning tools that I have seen others use. Since I have only had XP and gparted works with XP, I have never used anything other than gparted. Some report these will also correctly move some of the data that Windows own tools do not move, so you often can shrink more. But NTFS needs about 30% free space to work really well so do not shrink too much.

EASEUS Partition Master 
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm)
Partition Wizard
[http://www.partitionwizard.com/free-partition-manager.html](http://www.partitionwizard.com/free-partition-manager.html)

---

### Post by mr michaelD on 2012-10-05
> **oldfred said:**
> Windows NTFS partitions have in its PBR the start and size of the partition like the info in the partition table. So when resized even by Windows tools, it automatically runs chkdsk to update that info. Sometimes from gparted other information seems to get changed and users have major issues, others have reported using gparted and then with chkdsk Windows is ok. But we normally suggest Windows tools for Windows and Linux tools for Linux just to be on the safe side. 

i'm in the process of switching from macOS to linux and so this new lap is the only thing i have that speaks win.  and since i haven't cleared the EULA hurdles i'm kind of hosed, no matter what tools i'd like to try


> **oldfred said:**
> But NTFS needs about 30% free space to work really well so do not shrink too much.

i have no idea how much to leave for the existing install as the tools aren't reporting how much is in use.  i think i'll just allocate about 30 gigs to /dev/sda3 [for windows] when i shrink it and hope thats enough.  if its not the worst case is that windows ends up as dumb as a post, right?   shouldn't pose a problem installing / using linux, should it?

thanks again

---

### Post by mr michaelD on 2012-10-05
it looks like all this angst has been academic.  the ubuntu installer partition utility won't let me do any resizing at all; and GParted acts like it will but when i pull up the resize dialog for /dev/sda3 it leaves the 'resize/move' button grayed out.  it tried typing a new size in there but it won't enable.  all it seems to want to let me do is increase the size.

---

### Post by Bucky Ball on 2012-10-05
> **mr michaelD said:**
> 
the only reasons i'm inclined to keep the win7 partitions at all is in the event i need them down the road [i can't imagine what for though] and i'd like to be able to toy with some of the pre-installed apps via WINE once i'm up and running in linux.



Problem. If the apps are already installed in Windows you can't use them through Wine. Wine allows you to *install* Windows programs into Ubuntu, not access already installed apps from another (Win) partition. ;)

In other words, to use the apps you are going to need the installation disk or the .exe file to install it via Wine. Be reminded: Some programs work great in Wine, others ok, others not at all.  

There's that requirement out of the way ...

---

### Post by oldfred on 2012-10-05
The red circle with the exclamation point in your post indicates some issue that gparted thinks you have. Generally if an issue it will not mount a partition to prevent damage that chkdsk in Windows will not fix. You can click on the circle or right click (?) to see what it says, but usually it means run chkdsk from a Windows repairCD or from inside Windows repair console when booting & f8.

---

### Post by mr michaelD on 2012-10-06
thanks for the assistance guys.  i finally went into win7 enough to be able to run chkdisk, defrag, and shrink.  i have to say that everything i have attempted inubuntu has been easier than anything i attempted in win7.  once i completed those steps it would only shrink the partition by about 50%.  so it was using about 35 gigs but insisted on a little north of 300 gigs.  BUT, once i'd done all that, gparted was more than happy to take it on and shrink it down.  i left about 48 gigs for the stupid thing; i'm now up and running in ubuntu on my inspiron and cruising right along.

i have no idea whether or not win7 still works after using gparted to shrink its world and i'm hard-pressed to care.  i'm starting to think the best thing for me to do will be to blitz those other partitions and expand the existing *nix partitions to reclaim the wasted space.

i'll be mindful of what you had to say about WINE.

thanks again,
michaelD

PS .... i'll mark this one resolved

---

### Post by Bucky Ball on 2012-10-07
Nice work. Enjoy the OS and the learning curve. Sounds like you are already doing that ... ;)

---

