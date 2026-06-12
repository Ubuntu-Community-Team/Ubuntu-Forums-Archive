---
title: "Merge the SWAP partition and add it to the /home pratition"
date: 2006-01-20
forum: Desktop Environments
---

### Post by rado_london on 2006-01-20
Hi folks

I have 512 MB RAM and 1024 MB SWAP. I dont need that much SWAP so I am curious how can I make the SWAP partition 300 MB and to add the free space to my /home partition (ext3, 50 GB).
Of course I would like to make this without formatiing the partitions.

Thanks in advance!

---

### Post by southernman on 2006-01-20
Personally, I think it's a bit to much sugar for a dime... but it's not my system! ;)

You can use GParted to do this. If you don't have it installed, just do

sudo apt-get update
sudo apt-get install gparted (I think this is correct anyway)

Or you can do this in synaptic.

---

### Post by vruum on 2006-01-20
I wrote a rather verbose reply, which, I guess, became superfluous before I got around to posting it, but just in the spirit of "never mess with a mounted partition" here goes:
the easiest way to do this would be if you had some kind of live-cd, if you don't it should however still be doable in a "few" easy steps-
1: open up a terminal.
2: you need to make a temporary home, so you can unmount the old one. ```
sudo mkdir /tmp-home
```
3: on next boot, dont mount /home 
```
 sudo gedit /etc/fstab
``` 
find the line that mounts /home, something like: /dev/hda4 /home ext3 0  0
comment that line out(put  # in front of it)do the same to the swap line
4: change home 
     a)backup ```
 sudo cp /etc/passwd /etc/passwd-bak
```
     b)```
 sudo gedit /etc/passwd
```
 find the line starting with your username, on that line change /home/$YOU to   
 /home-tmp, save file.
5: change the ownership of your new home:```
sudo chown -R $YOU /home-tmp
```
6: reboot
now, if all goes well, you should be able to boot up, and log in, if not, reboot, and start up in safe mode and undo the changes. also, if you're using a live cd, this would be where you should start.
7: make sure that your old home is not mounted. ```
sudo umount /home
``` or ```
cat /etc/mtab
```which will print anythithng mounted.
8: install gparted, the partition program```
 sudo apt-get install gparted
```
9: start gparted [code]sudo gparted]
    from gparted, first resize the swap, then resize your old /home, press submit, and roll. once gparted is done, undo  step 3+4. reboot

---

### Post by Quirky on 2006-01-20
Can you resize swap like that? Normally you can only move the end of a partition, not the start.

The way I'd do it (did it, in fact, slightly, I shrunk my root partition after shrinking my windows partition to create a /home partition) would be:
 d/l System Rescue CD
"run_qtparted", 
delete the swap partition, 
resize home, 
make a new swap partition, but a bit smaller. 

That's assuming home and swap are contiguous - i.e home then swap follow on from each other on the drive, home isn't inside an extended partition and swap outside of it, etc. In fact qtparted may tell you to sod off, if it can't be done.

---

### Post by rado_london on 2006-01-20
Guys Thanks for the brilliant help.
At the moment I have really important stuff to download and I dont really want to mess the drives. Well after a few days I will try it and I will post the results.

---

