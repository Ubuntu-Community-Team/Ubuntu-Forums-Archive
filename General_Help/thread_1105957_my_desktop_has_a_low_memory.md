---
title: "my desktop has a low memory?"
date: 2009-03-25
forum: General Help
---

### Post by sanozuke02 on 2009-03-25
why is it my computer telling me that it has a low memory even though the desktop has a large space.. i cant download any file because of lack of memory how can i fix it??..


please help me again guys...

salamat<thanks..:(:(:(:(:KS

---

### Post by drs305 on 2009-03-25
You will have to clarify your problem. Is it a *memory* problem or a *disk space* problem.

For memory, this will provide some information:
```
free
```

For disk space usage:
```
df -Th
```

If you post these results or further explain your problem we can help you.

---

### Post by sanozuke02 on 2009-03-25
what i means is when download a file it shows that the disk has no space,, even though that disk has a free more spaces.. is it possible to put more spaces in my memory??  because when i go to my file browser it says that 9.8 mb free bytes.. ..


thanks for helping..

---

### Post by RansomStark on 2009-03-25
Are you running this off a liveCD ?

---

### Post by drs305 on 2009-03-25
Ok, I think you have a disk space problem. Remember there is a difference between disk space and RAM/memory. If you have no room left on your drive, this is a disk *space* issue.

One common problem is people who have lots of items in the Trash bin and forget to empty it. Trash takes up space on your disk until you empty the trash bin.

Another common problem is making a large backup file but putting it on your system partition instead of on a removable drive or another partition.

If you would post the results of "df -Th" we can get an idea of where you are running out of space.

You can also take a look at the guide to removing Trash in my signature line. It will help you find all the Trash on your system and remove it. It also provides some other ways to free up disk space.

---

### Post by coffeecat on 2009-03-25
> **sanozuke02 said:**
> is it possible to put more spaces in my memory??

You really don't want more spaces in your memory. At my age it's becoming a real problem. :( :wink:

But seriously, you haven't answered drs305. It's not clear what the problem is. Go to Applications > Accessories > Terminal. In the terminal, type the two commands drs305 suggests. One at a time. :wink: And post the output. You don't want to be typing all that stuff, so for each output, highlight it with the mouse and do a ctrl-shift-C to copy it. Then paste it into the message field (ctrl-V), but enclose it in [noparse]```

```[/noparse] tags to keep the formatting. Then we can see what the problem is

---

### Post by sanozuke02 on 2009-03-25
Filesystem    Type    Size  Used Avail Use% Mounted on
/host/ubuntu/disks/root.disk
              ext3    3.5G  3.4G     0 100% /
tmpfs        tmpfs    125M     0  125M   0% /lib/init/rw
varrun       tmpfs    125M  240K  125M   1% /var/run
varlock      tmpfs    125M     0  125M   0% /var/lock
udev         tmpfs    125M  2.7M  122M   3% /dev
tmpfs        tmpfs    125M  104K  125M   1% /dev/shm
/dev/sda1     vfat     16G   14G  2.2G  86% /host
lrm          tmpfs    125M  2.0M  123M   2% /lib/modules/2.6.27-11-generic/volatile
overflow     tmpfs    1.0M   48K  976K   5% /tmp
/dev/sda5     vfat    3.8G  207M  3.6G   6% /media/DISK1_VOL2

this is the result of the codes df- Th .... i cant understand this so please help me... i am not also computer programmer..so please help me..:(:(

---

### Post by coffeecat on 2009-03-25
Here's your problem. Your root partition is full.

> **sanozuke02 said:**
> ```
Filesystem    Type    Size  Used Avail Use% Mounted on /host/ubuntu/disks/root.disk
              ext3    3.5G  3.4G     0 100% /
```

(I've stuck it in code tags for you. :wink:)

That's a tiny little partition. A default installation of Ubuntu uses up about 2.2-2.5GB as far as I remember, and it doesn't take much personal data or additional applications to add a gigabyte to that. You'll have to free some space. Empty the trash as drs305 suggested, and/or delete some files.

---

### Post by sanozuke02 on 2009-03-25
my trash is already empty.....

and nothings change...:(:(:(:

any other idea??:(:

---

### Post by sanozuke02 on 2009-03-25
help me please???.. its my first time to use this ubuntu,, and i really like it,,,..


so please help guys??

---

### Post by coffeecat on 2009-03-25
> **sanozuke02 said:**
> any other idea??:(:

Your root partition is full. Unless you delete something, you can't download anything. There is one thing you could do, but please be careful. You're about to do something with administrator privileges. Open a terminal and:

```
sudo apt-get clean
```

You'll be prompted for your password which will not appear on screen as you type it in. This will delete any packages for updates and additional software that you've downloaded since you first installed. You don't need them and this will make some room.

But you really need a larger partition to run Ubuntu from.

---

### Post by Rocket2DMn on 2009-03-25
> **sanozuke02 said:**
> help me please???.. its my first time to use this ubuntu,, and i really like it,,,..


so please help guys??

Hi,
First, welcome to the Ubuntu community, we are glad you are liking Ubuntu.  We understand that you are frustrated with your problem, but please give the community time to respond to your questions.  It is considered bad forum etiquitte to "bump" your posts within short periods of time.  The general rule of thumb on these forums is to wait 24 hours before bumping posts.  You are getting a lot of help from experienced users right now, but they need time to respond.  Thank you for understanding, and good luck.

---

### Post by Praet0rian on 2009-03-25
Hi guys,

I am facing the same problem and read this thread..
As a Ubuntu newbie I cant imagine where I should begin freeing disk space. My trash is already cleaned.

The output of df -TH is
```

Filesystem    Type     Size   Used  Avail Use% Mounted on
/dev/sda3     ext3     4.0G   3.8G   1.3M 100% /
tmpfs        tmpfs     525M      0   525M   0% /lib/init/rw
varrun       tmpfs     525M   111k   525M   1% /var/run
varlock      tmpfs     525M      0   525M   0% /var/lock
udev         tmpfs     525M   2.9M   522M   1% /dev
tmpfs        tmpfs     525M   381k   524M   1% /dev/shm
lrm          tmpfs     525M   2.1M   523M   1% /lib/modules/2.6.27-11-generic/volatile
/dev/sda1     vfat      35G    28G   7.3G  79% /media/windows
/dev/sda2  fuseblk      21G    21G   801M  97% /media/disk

```

As you can see, there are two other partitions mounted. Those are my windows partitions.
Is it because of the small capacity of sda3? Do I have to resize the partition in this case, to expand the capacity of sda3?

Thanks!

---

### Post by drs305 on 2009-03-25
PraetOrian,

I am just about finished with a guide on this problem which I will post in the Tutorials section once it is done (probably a week or two). In the meantime, the guide Trash removal in my signature line offers many of the tips on freeing space, including some not related to Trash.

Your system partition is pretty small and you will probably continue to have problems from time to time. I see you don't really have much space to 'steal', but if you can expand the partition by taking space from another partition I would recommend it.

---

### Post by coffeecat on 2009-03-25
> **Praet0rian said:**
> Is it because of the small capacity of sda3?

Well, yes. I've installed Ubuntu on the 4GB internal flash drive of my Asus Eee, and it runs fine. But that's because I've added hardly any software and I don't save video files on it. Not much point on one of the original Eees. :wink:

You've got the same problem as the OP with the same solution. Either delete something (and/or uninstall some applications) or use a larger root partition. As far as resizing sda3, I don't know. It depends on your actual disk layout. Post the output of:

```
sudo fdisk -l
```... and that will give us a little more information to go on.

---

### Post by Praet0rian on 2009-03-25
thanks alot for your reply!

i've got a really small hdd on my notebook, thought 4GB will be enough,as i installed ubuntu.. :) 

here is the output
```

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x38a138a0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1             562        4754    33680272+   c  W95 FAT32 (LBA)
/dev/sda2   *        4755        7296    20418612    7  HPFS/NTFS
/dev/sda3               1         486     3903763+  83  Linux
/dev/sda4             487         561      602437+  82  Linux swap / Solaris

```

i could try to steal some space from sda1, but i only manage to do that in windows.. i could look for some partitioning hints here in the forums..

thanks for help..

---

### Post by coffeecat on 2009-03-25
> **Praet0rian said:**
> i've got a really small hdd on my notebook

60GB ??!! Pfftt. My Sony laptop came with a 60GB, and at one time I had Windows, Ubuntu, Suse, Fedora, AND a separate data partition, altogether at the same time. And I didn't fill my Linux partitions up. :) Admittedly, I didn't have much room to spare on the Windows C: partition. :wink: But that didn't matter. :lol:

Anyway....

> **Praet0rian said:**
> here is the output
```

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x38a138a0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1             562        4754    33680272+   c  W95 FAT32 (LBA)
/dev/sda2   *        4755        7296    20418612    7  HPFS/NTFS
/dev/sda3               1         486     3903763+  83  Linux
/dev/sda4             487         561      602437+  82  Linux swap / Solaris

```i could try to steal some space from sda1, but i only manage to do that in windows.. i could look for some partitioning hints here in the forums..

Well... you've got a problem - two actually. Your Linux sda3 root partition is not contiguous with your Windows C: partition (sda2) and you'd have to steal from sda1 (as you point out). It's not true to say you can only do that in Windows. Boot up from the live CD and go to System > Administration > Partition Editor and you'll find a nice intuitive GUI partition editor. Theoretically, you should be able to shrink sda1 and then expand sda3 to use the freed space, but resizing partitions can be tricky. There's always the danger that everything goes pear-shaped and you lose everything. And I mean everything - the main partition table as well. So do back up first.

But your second problem: you've got four primary partitions which is as many as you're allowed. Here's something to think about. Unlike Windows, Linux can boot from a logical partition. Instead of a primary partition, you can create an extended partition (which will be numbered sda1,2,3 or 4 just like a primary). Then in the extended you can create a number of logicals (numbered sda5 upwards). THis doesn't help you with the immediate problem, but it's useful to remember if you were ever doing a clean reformat and install of a hard drive. It gives you more flexibility.

---

### Post by cortexedge on 2009-07-16
Hello!

I wanted to start a new thread on the same problem, but came across this one.
So, here is my problem.
I installed Ubuntu alongside Windows( about 10Gb free space)....but now, it says me that I don't have enough space to download updates :(
My trash is full but can't empty it.
This is what I picked up from the terminal:


Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/sda8     ext3    2,3G  2,3G     0 100% /
tmpfs        tmpfs    502M     0  502M   0% /lib/init/rw
varrun       tmpfs    502M   96K  502M   1% /var/run
varlock      tmpfs    502M     0  502M   0% /var/lock
udev         tmpfs    502M  156K  502M   1% /dev
tmpfs        tmpfs    502M  564K  501M   1% /dev/shm
lrm          tmpfs    502M  2,4M  499M   1% /lib/modules/2.6.28-11-generic/volatile
overflow     tmpfs    1,0M   16K 1008K   2% /tmp
griffo@griffo-desktop:~$ 


Mozilla doesn't even activates the "back" button because of the lack of free space :(
Any idea on what I should do?
Thanks in advance!

---

### Post by drs305 on 2009-07-16
cortexedge: Welcome to Ubuntu and the Ubuntu forums. :-)

Try to gain a bit of space by running these commands in terminal (ALT-F2 or Applications, Accessories, Terminal):
```

sudo apt-get clean && sudo apt-get autoclean

```

Then open a browser as root and use SHIFT-DEL to delete the ***Trash*** folders. Since you are running a 'root' browser, make sure you are deleting the correct folders:
```

gksudo nautilus /root/.local/share/  $HOME/.local/share

```

Then take a look at your disk space. There is a guide in my signature line about recovering free space - see the DiskSpace link.

---

### Post by cortexedge on 2009-07-16
[drs305]("http://ubuntuforums.org/member.php?u=223945"), thank you for replying, but your commands didn't worked for me :confused:
I'm currently reading the article from your signature, but some stuff sound really, really chinese like to me :-#....
You see, I don't get it....
I have free space on my disk, but Ubuntu says I don't have.... big dilema :D

---

### Post by drs305 on 2009-07-16
> **cortexedge said:**
> [drs305]("http://ubuntuforums.org/member.php?u=223945"), thank you for replying, but your commands didn't worked for me :confused:
I'm currently reading the article from your signature, but some stuff sound really, really chinese like to me :-#....
You see, I don't get it....
**I have free space on my disk, but Ubuntu says I don't have.... big dilema** :D

From your previous post:
> 
/dev/sda8 ext3 2,3G 2,3G 0 100% /

Notice it says / has 0% free space. It doesn't matter about how much space you have on other partitions in this case. Since system operations are normally performed in /, that is where the free space must be located.

Could you explain a bit about the commands I presented "not working". Did you get error messages, couldn't open a terminal, couldn't find the Trash folders, they ran but didn't free any space, or something else?

Perhaps we could help if you give us the results of:
```

sudo du -h / --max-depth=1 | sort

```
You will get some 'cannot access' messages but eventually some meaningful output will appear.

Also, here is a link to the wiki based on the DiskSpace thread. It has graphics and may be easier to understand:
[https://help.ubuntu.com/community/RecoverLostDiskSpace]("https://help.ubuntu.com/community/RecoverLostDiskSpace")

---

### Post by cortexedge on 2009-07-16
Ran that command and this popped out:


du: cannot access `/proc/3283/task/3283/fd/3': No such file or directory
du: cannot access `/proc/3283/task/3283/fdinfo/3': No such file or directory
du: cannot access `/proc/3283/fd/3': No such file or directory
du: cannot access `/proc/3283/fdinfo/3': No such file or directory
du: cannot access `/home/griffo/.gvfs': Permission denied
0    /proc
0    /sys
121M    /lib
12K    /media
13M    /boot
13M    /etc
16K    /lost+found
16K    /tmp
1,7G    /usr
188M    /var
224M    /home
228K    /root
2,3G    /
4,0K    /mnt
4,0K    /opt
4,0K    /selinux
4,0K    /srv
6,1M    /bin
684K    /dev
8,4M    /sbin


Can't I asign more space from windows' free spce?
By the way, sorry for asking "noob" questions, but I'm really interested in using Ubuntu instead of Windows...

---

### Post by drs305 on 2009-07-16
cortexedge, Your / partition is simply too small. Although you may be able to gain a bit of space from time to time, you are going to have problems with a / partition that is only 2.3 GB. I read your original post before you added the specifics.

Yes, you are going to have to take some space from another partition if you want this installation to succeed. Here is a good link to partitioning. You should probably start a new thread, and include a snapshot of your partitions. *gparted* is a good app to do the partitioning.

[https://help.ubuntu.com/community/HowtoPartition]("https://help.ubuntu.com/community/HowtoPartition")

[http://ubuntuforums.org/showthread.php?t=282018]("http://ubuntuforums.org/showthread.php?t=282018")

---

### Post by cortexedge on 2009-07-16
I didn't create it... :(
I chose to install Ubuntu alongside Windows and this mess came out after everything was done....
I knew I must  have at least 5  Gb of free spce, but considered that Ubuntu is smart enough to ensure it's gonna have some space to move on...:confused:

So, I guess there's nothing to do....
Only a repartition will solve this problem.

---

### Post by cortexedge on 2009-07-16
Ok, thanks!
I will be doing so later, cause I have to sleep...it's 4AM here :D
Bye :)

---

### Post by drs305 on 2009-07-16
> **cortexedge said:**
> I didn't create it... :(
I chose to install Ubuntu alongside Windows and this mess came out after everything was done....
I knew I must  have at least 5  Gb of free spce, but considered that Ubuntu is smart enough to ensure it's gonna have some space to move on...:confused:

So, I guess there's nothing to do....
Only a repartition will solve this problem.

Yes. I would defrag my Windows partition a couple of times, back up your important data, and then create the correct partition sizes with either Windows software or with gparted from the LiveCD. I would then select manual partitioning during a new ubuntu install.

You can also just move your current partitions around but depending on where they are currently located and how large they are this can sometimes take longer than a reinstallation. It depends partly on how much time you have spent setting things up after the installation, which you would have to repeat with a reinstall.

Good luck. Stick with ubuntu a bit longer - I think you will like it.

---

### Post by c0mput3r_n3rD on 2009-07-16
> **coffeecat said:**
> You really don't want more spaces in your memory. At my age it's becoming a real problem. :( :wink:

Haha that's funny man.

And you guys just need to get bigger HDD.  I can't believe how small they all are.  3GB 4GB.  My laptop 7 years ago came with a 40GB and I thought that was small.  My old 1998 IBM 380D (a.k.a. The Brick) has a 2GB HDD, and that's runny Winblows `95.  Do your selves a favour and just invest in a new HDD.  It's well worth it.

---

### Post by cortexedge on 2009-07-17
> **c0mput3r_n3rD said:**
> Haha that's funny man.

And you guys just need to get bigger HDD.  I can't believe how small they all are.  3GB 4GB.  My laptop 7 years ago came with a 40GB and I thought that was small.  My old 1998 IBM 380D (a.k.a. The Brick) has a 2GB HDD, and that's runny Winblows `95.  Do your selves a favour and just invest in a new HDD.  It's well worth it.

Mine is 250Gb but don't know why Ubuntu aloccated only 2.3 Gb for itself:confused:

---

