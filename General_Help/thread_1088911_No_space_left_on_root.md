---
title: "No space left on root"
date: 2009-03-06
forum: General Help
---

### Post by cybergrrl on 2009-03-06
Hi :)

This is my first post, I hope I give all the right information:

My '/' partition is full. At first I thought it was the backup that I made with SBackup. I had stored my backup to the wrong directory (/var) but I already deleted the backup files there and it did not help to free space. 

What can I do to free space on the root directory? It's 9,5G big, my /home directory is on a different partition.

I've been through this thread: [http://ubuntuforums.org/showthread.php?t=656632](http://ubuntuforums.org/showthread.php?t=656632) but it doesn't seem to be as simple in my case. It seems that there are no particulary huge files that I could delete, but that the space is mainly just full with lots of "stuff". 
When I enter ```
du --max-depth=1 -xh /
``` as far as I can see,  /usr is the directory which takes most space (3,7G). Inside the usr directory it is /usr/share (2G) and /usr/lib (1,2G) but when I check these folders, there are no more big files, just many small ones.
To make it more complicated, there are some errors when I enter ```
du --max-depth=1 -xh /
``` - which you can see underneath. Sorry, it's in German. It says: cannot read directory. If I interprete it correctly then it says in the last line, that my root directory is 5.1G big, which isn't true according to GParted it should be 9,5!

6,6M	/sbin
549M	/lib
4,0K	/srv
4,0K	/initrd
3,7G	/usr
0	/dev
0	/tmp
0	/proc
91M	/boot
du: kann Verzeichnis „/root/.gconf“ nicht lesen: Permission denied
du: kann Verzeichnis „/root/.gnome2“ nicht lesen: Permission denied
du: kann Verzeichnis „/root/.config“ nicht lesen: Permission denied
du: kann Verzeichnis „/root/.dbus“ nicht lesen: Permission denied
du: kann Verzeichnis „/root/.nautilus/metafiles“ nicht lesen: Permission denied
du: kann Verzeichnis „/root/.gvfs“ nicht lesen: Permission denied
du: kann Verzeichnis „/root/.gnome2_private“ nicht lesen: Permission denied
du: kann Verzeichnis „/root/.synaptic“ nicht lesen: Permission denied
du: kann Verzeichnis „/root/.local/share/Trash“ nicht lesen: Permission denied
du: kann Verzeichnis „/root/.gconfd“ nicht lesen: Permission denied
7,3M	/root
du: kann Verzeichnis „/etc/ssl/private“ nicht lesen: Permission denied
du: kann Verzeichnis „/etc/cups/ssl“ nicht lesen: Permission denied
15M	/etc
4,0K	/mnt
4,0K	/opt
4,0K	/home
0	/sys
du: kann Verzeichnis „/lost+found“ nicht lesen: Permission denied
16K	/lost+found
16K	/Recycled
du: kann Verzeichnis „/var/lib/gdm“ nicht lesen: Permission denied
du: kann Verzeichnis „/var/lib/PolicyKit“ nicht lesen: Permission denied
du: kann Verzeichnis „/var/spool/cups“ nicht lesen: Permission denied
du: kann Verzeichnis „/var/spool/cron/crontabs“ nicht lesen: Permission denied
du: kann Verzeichnis „/var/spool/cron/atjobs“ nicht lesen: Permission denied
du: kann Verzeichnis „/var/spool/cron/atspool“ nicht lesen: Permission denied
du: kann Verzeichnis „/var/cache/ldconfig“ nicht lesen: Permission denied
du: kann Verzeichnis „/var/cache/system-tools-backends/backup“ nicht lesen: Permission denied
742M	/var
5,2M	/bin
24K	/media
5,1G	/

I also tried ```
sudo apt-get clean
``` but it only helped a tiny bit: I now have 0,44 GB space on root.

---

### Post by mªrty on 2009-03-06
have you tried looking at the Disk Usage Analyzer under Programs-->Accessories? That might help you see where all the data is sitting...

---

### Post by Xbehave on 2009-03-06
remove old kernels
games (these take alot of space)
empty out useless stuff in /root

---

### Post by sansa dude on 2009-03-06
definatly try the disk use thing i had 30 gb left on my 80gb hard drive at one point wondering where it all went. it was all in virtual box from when i was trying to set up windows 2000 so i removed that and ive got virtually nothing on there. so try it first

---

### Post by mªrty on 2009-03-06
> **Xbehave said:**
> [remove old kernels]("http://tombuntu.com/index.php/2007/10/17/remove-ubuntu-kernels-you-dont-need/")
empty out useless stuff in /root
[_link to guide_]("http://tombuntu.com/index.php/2007/10/17/remove-ubuntu-kernels-you-dont-need/") on removing old kernels.
how would one empty the /root folder?

---

### Post by oldos2er on 2009-03-06
Install the program 'localepurge'. "localepurge is a small script to recover disk space wasted for unneeded locale files and localized man pages. It will be automagically  invoked by  dpkg  upon  completion  of  any apt installation run."

---

### Post by cybergrrl on 2009-03-07
thanx for all the replies! 
@ marty: i used some disk analyser tool, not sure if it is the one u mentioned, but it only told me that root was full, not what is filling it up. that's why i tried via the terminal.
@ xbehave and oldos2er: i could not install or remove applications because i got errors because of the full disk. also synaptic couldnt start because of that.

anyway, unfortunately i cannot try any of the suggested things now because my machine isn't booting anymore. here is what happened:
i didnt have internet access tonite so i couldnt actually do more for ubuntu, so i thought i can as well play some games on my windows partition. but the game froze, the graphics went all weird. and when i tried to restart, it didn't work. the first two times i tried, i got to the boot menu but neither ubuntu nor xp started. instead i got lots of vertical stripes on my screen. they very slowly changed colours until my screen was almost white, then back to almost black. that's all.
i tried to start several more times, but i can't even get to the boot menu anymore, only stripes. 

now i have no idea if it has anything to do with the full root partition or if some hardware is broken or whatever. any suggestions would be much appreciated!

---

### Post by cybergrrl on 2009-03-09
i had a talk with dell service and apparantly my video card is broken - i'll start trying yr suggestions tomorrow when it should be repaired...

---

### Post by cybergrrl on 2009-03-10
i did as you suggested and deleted old kernels and all games along with some other applications i don't use. i was a bit scared thO to install/use localepurge because of the warnings on their site and i'm just a beginner after all...

i've got 950 MB of space now on my 9,5 GB root partition. it doesn't sound much. i was wondering what experts think, is that alright?

i tried to figure out what the rest of the space is used for using gparted and the disk analyser and found something confusing: gparted gives me very different information from the analysing tool. for example disk analyser claims that root is still 100% full. it also claims my xp partition is 100% full, which is not the case according to gparted... also the disk analyser suggests that most of my root partition is filled up by my /home folder, which actually is not even located on the same partition! 
any suggestions?  

apart from that, my ubuntu works again. thanks a lot for all the helpful suggestions!!

---

### Post by pyrofreek_9 on 2009-03-10
In a terminal, try running
```
df -h /
```
That will tell you for sure how much you're using.

---

### Post by cybergrrl on 2009-03-12
the result for df -h /
Dateisystem            Größe Benut  Verf Ben% Eingehängt auf
/dev/sda3             9,4G  8,5G  491M  95% /

491 is apparently not enough to upgrade my system to 8.10 :( i think i need at least 1GB.

what i did so far: 
- removed Residual Config packages
- removed partial packages
- sudo apt-get clean and sudo apt-get autoclean
- removed unnecessary locale data using localepurge
- removed orphaned packages using deborphan

the result:
Dateisystem            Größe Benut  Verf Ben% Eingehängt auf
/dev/sda3             9,4G  8,5G  518M  95% /
still only 518MB...

i tried to locate where the majority of my data is stored. As i said, Disk Usage Analyzer confuses me. i add a link to a picture, maybe someone can explain what it means?
[http://img220.imageshack.us/img220/6936/bildschirmfotofestplatt.png](http://img220.imageshack.us/img220/6936/bildschirmfotofestplatt.png)
first of all: my root directory is not 100% full, but only 95%, as the terminal stated. secondly: root can impossibly use 138GB of space because it's only 9,4GB big, as you can see above.
and also: my home folder is not "inside" the root folder actually, it's on its own partition. but maybe that's just the way ubuntu "thinks" and arranges its directories, home always appears under root?

anyway: if i add together everything the disk analyser shows, i hardly get 4,5GB and not 8,5GB (as terminal states). what's wrong? why is my disk full? what's taking all the space which shouldn't even be taken, according to the disk analyzer?

edit: i installed filelight in order to find out more about where the files that take my space are "hidden". only more confusion. it claims (much like disk analyser) that i only use 3,4G of my root partition. (3G of that in the usr folder) i add another link to a screenshot:
[http://img228.imageshack.us/img228/729/bildschirmfotofilelight.png](http://img228.imageshack.us/img228/729/bildschirmfotofilelight.png)

---

### Post by cybergrrl on 2009-03-13
does nobody have any idea? i'm lost here... 
is the size of root just normal? i don't have that much installed on my compupter. i thought 10G would be enough space... is there a way to add space to my root partition now? 

do i have to reinstall the whole system if i wanna use intrepid ibex?! 
please ;(

---

### Post by ushills on 2009-03-13
Try this 

```
du --max-depth=1 / | sort -n -r
```

or try

```
du --max-depth=1 /dev/partition name | sort -n -r
```

This will list the size of folders in order, then go recursively into folders, i.e

```
du --max-depth=1 /home/!!name of largest folder!!! | sort -n -r
```

We can then see what is taking all the room.

However, if your /home is on a separate partition it is really easy to install fresh and retain /home.

Note, your /home seems almost full as well.

---

### Post by cybergrrl on 2009-03-13
thanx a lot :)

1) 
why do you think the home partition is full? it isn't, as far as i know that's not the case:
violet@violet-laptop:~$ df -h /home
Dateisystem            Größe Benut  Verf Ben% Eingehängt auf
/dev/sda6             234G  135G   88G  61% /home

2)
when i enter du: ```
du --max-depth=1 / | sort -n -r
``` i get a virtually endless list of errors like this: ```
du: kann Verzeichnis „/proc/2428/task/2428/fd“ nicht lesen: Permission denied
``` (can't read directory ... permission denied)

however, in the end it gives the information, i guess we're interested in:
```
182689067	/
140832736	/home
37674111	/media
3654044	/usr
299640	/var
174672	/lib
19088	/boot
14764	/etc
7376	/root
6608	/sbin
5256	/bin
644	/tmp
84	/dev
16	/lost+found
8	/Recycled
4	/srv
4	/opt
4	/mnt
4	/initrd
0	/sys
0	/proc
```

at first i thought that must be wrong, since it says that there are almost 36G used for /media. but the / partition is not even 10G big! but when i entered ```
du --max-depth=1 /media | sort -n -r
``` i found out, that the 35G are on sda1, which is my windows partition. 

```
36434405	/media
36434149	/media/sda1
248	/media/sda5
4	/media/cdrom0
```

that means /media is out of the question as the culprit, doesn't it? although i do not understand why the output for that last command only gives information about sda1 and sda5 and the cdrom drive. apparently there are more partitions (like, for example my root partition)

next in size would be /usr. but it only amounts to 3,5G. i did a quick calculation and all the other files together, including /usr only amount to 4G!

3) summary:
if /home has its own partition and /media's 35G are almost completely on my windows partition, it appears that only 4G on root are actually used.
thus, there are 4,5G missing and i have no idea where they are. in order to find out what's on root, i entered: ```
du --max-depth=1 /dev/sda3 | sort -n -r
``` 
i get 
```
0	/dev/sda3
```
what does that mean?? sda3 is empty? that's not supposed to look like this, is it? maybe i entered something incorrectly? but gParted states that sda3 is the partition used for root...

How should i proceed now?

---

### Post by drs305 on 2009-03-13
A while back I wrote a tutorial on finding and deleting trash - which remains on your computer until you empty your trash bins or delete the files. There are at least several different trash bins that need to be emptied. The tutorial also covers a few other ways to find files taking up space. See the link in my signature line. Maybe it covers something you haven't yet tried.

---

### Post by cybergrrl on 2009-03-13
> **drs305 said:**
> A while back I wrote a tutorial on finding and deleting trash - which remains on your computer until you empty your trash bins or delete the files. There are at least several different trash bins that need to be emptied. The tutorial also covers a few other ways to find files taking up space. See the link in my signature line. Maybe it covers something you haven't yet tried.

thanks! i will do that and report here :)

---

### Post by Slim Odds on 2009-03-13
Whenever anyone talks about low disk space, I remind them that the default formatter in Ubuntu allocates 5% of the partition for "reserved" space (root).

With large disk partitions, this can be a **LOT** of space (especially on big home partitions which don't need this space AT ALL).

Use tune2fs to reduce the reserved space (-m option).

---

### Post by cybergrrl on 2009-03-13
> **drs305 said:**
> A while back I wrote a tutorial on finding and deleting trash - which remains on your computer until you empty your trash bins or delete the files. There are at least several different trash bins that need to be emptied. The tutorial also covers a few other ways to find files taking up space. See the link in my signature line. Maybe it covers something you haven't yet tried.


whoo! that did the job, you were right, it was /root/.local/share/Trash! i emptied it as described in the tutorial and voila: 4,3G more space! thnx soo much! thnx to everyone!

mm - how do i mark the thread as solved?

---

### Post by ushills on 2009-03-13
Glad you solved it. typically your roo trash fills up if you use sudo to delete anything i believe.

to mark as solved change the post title by editing your first post the solved option disappeared some time ago.

---

### Post by Slim Odds on 2009-03-13
> **ushills said:**
> Glad you solved it. typically your roo trash fills up if you use sudo to delete anything i believe.

"sudo rm"  would not move anything to the trash.

If you run nautilus using gksudo, then you'll get stuff in the root trash.

---

### Post by Bill Roberts on 2009-03-13
I want to thank those responsible for the thread at [http://ubuntuforums.org/showthread.php?t=656632](http://ubuntuforums.org/showthread.php?t=656632) 

I would post there but it is read only.

I also managed to run a couple of full backups while the external drive was offline and it used 11GB of /

Such a simple issue and such an easy answer and I would never have found it on my own.

---

