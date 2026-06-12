---
title: "Installing shadowgrounds.iso on Ubuntu 13.10"
date: 2014-03-18
forum: Gaming &amp; Leisure
---

### Post by Hodevah on 2014-03-18
Hi. I have done a quick search on the gaming sub-forums to see if there are similar problems that have been encountered previously with installing the Linux version of shadowgrounds. But unless I have missed something, I don't believe that I have found anything related. 

My problem is with trying to make a *shadowgrounds.iso* file install the game. Within the shadowgrounds.iso file is another file that is named *shadowgroundsUpdate1.run* file
I have tried these commands several times with similar results and unfortunately, no install of the game has yet been successful beyond these terminal inputs. 

The command inputs I've tried are the following. Here is the full output:


```
frankenstein@frankenstein-desktop:~$ sudo mkdir /media/loop
mkdir: cannot create directory &#8216;/media/loop&#8217;: File exists
frankenstein@frankenstein-desktop:~$ sudo mount -o loop -t iso9660 ~/Downloads/shadowgrounds.iso /media/loop
mount: block device /home/frankenstein/Downloads/shadowgrounds.iso is write-protected, mounting read-only
frankenstein@frankenstein-desktop:~$ cp -R /media/loop/* ~/installer_temp/
frankenstein@frankenstein-desktop:~$ sync
frankenstein@frankenstein-desktop:~$ cd ~/installer_temp
frankenstein@frankenstein-desktop:~/installer_temp$ chmod u+rx ./shadowgroundsUpdate1.run
frankenstein@frankenstein-desktop:~/installer_temp$ ./shadowgroundsUpdate1.run
bash: ./shadowgroundsUpdate1.run: No such file or directory
frankenstein@frankenstein-desktop:~/installer_temp$ umount /media/loop
umount: /media/loop is not in the fstab (and you are not root)
frankenstein@frankenstein-desktop:~/installer_temp$ sudo umount /media/loop
frankenstein@frankenstein-desktop:~/installer_temp$ ./shadowgroundsUpdate1.run
bash: ./shadowgroundsUpdate1.run: No such file or directory
frankenstein@frankenstein-desktop:~/installer_temp$ 
```


The *./shadowgroundsUpdate1.run* file should be within the  installer_temp; however, as I've be come aware on a number of occasions  when attempting these Terminal inputs, I don't see it within the*  /media/loop* directory, *the temp* directory, nor in the* home *directory.  That includes searching within some of the hidden files in all those directories.

Oh, by the way, I have tried it both this way:
```
umount /media/loop
cd ~/installer_temp
```

and this way:

```
cd ~/installer_temp
umount /media/loop
```

as you can see with the below terminal inputs when reversing.

```
frankenstein@frankenstein-desktop:~/installer_temp$ rm -rf ~/installer_temp
frankenstein@frankenstein-desktop:~$ sudo mkdir /media/loop
[sudo] password for frankenstein: 
mkdir: cannot create directory &#8216;/media/loop&#8217;: File exists
frankenstein@frankenstein-desktop:~$ mount -o loop -t iso9660 ~/downloads/shadowgrounds.iso /media/loop
mount: only root can do that
frankenstein@frankenstein-desktop:~$ sudo mount -o loop -t iso9660 ~/downloads/shadowgrounds.iso /media/loop
/home/frankenstein/downloads/shadowgrounds.iso: No such file or directory
frankenstein@frankenstein-desktop:~$ sudo mount -o loop -t iso9660 ~/Downloads/shadowgrounds.iso /media/loop
mount: block device /home/frankenstein/Downloads/shadowgrounds.iso is write-protected, mounting read-only
frankenstein@frankenstein-desktop:~$ cp -R /media/loop/* ~/installer_temp/
frankenstein@frankenstein-desktop:~$ sync
frankenstein@frankenstein-desktop:~$ umount /media/loop
umount: /media/loop is not in the fstab (and you are not root)
frankenstein@frankenstein-desktop:~$ sudo umount /media/loop
frankenstein@frankenstein-desktop:~$ cd ~/installer_temp
frankenstein@frankenstein-desktop:~/installer_temp$ chmod u+rx ./shadowgroundsUpdate1.run
frankenstein@frankenstein-desktop:~/installer_temp$ ./shadowgroundsUpdate1.run
bash: ./shadowgroundsUpdate1.run: No such file or directory
frankenstein@frankenstein-desktop:~/installer_temp$ 
```


as on the 1st occasion on utilizing the inputs given above   there was a  bit of a hiccup (the above inputs are actually the 5th and 6th time I believe). 
Sorry, as I don't recall but it didn't work out that  way.
Hence the reversal of those terminal inputs. Regardless, either way I don't think really matters. Please do correct me if I"m wrong on this last part, though. 

The problem that I'm facing is that there doesn't seem to be the ~/installer_temp$ directory and hence I think this might be the cause of my troubles. 

Please suggest to me alternate terminal inputs to get the game installed if there is a better one available. Secondly.

---

### Post by oldrocker99 on 2014-03-18
I may be off base here, but have you tried extracting the .ISO with Acetone (the FOSS version of the much-pirated Windows Alcohol program)? It'll extract every file on the .ISO to a folder.

---

### Post by Hodevah on 2014-03-19
I haven't done that but what I've done instead is mount the .iso file on Ubuntu's virtual disk mount and it basically comes out as the same thing. I can even copy/paste that same shadowUpdate1.run file to the home directory and attempt to execute it there. 
Still no go. 
And the file is set as *'set file as executable'* under the Properties heading.

---

### Post by Hodevah on 2014-03-21
Bump.  Hi. Is there anyone that might have an answer to my initial interest in having this resolved?

---

### Post by Hodevah on 2014-03-24
bump again, please. Still looking for help on this issue

---

### Post by R33D3M33R on 2014-03-26
What is the size and md5 checksum (run "md5sum shadowgroundsUpdate1.run" in the console) of the file?

---

### Post by Hodevah on 2014-03-29
> **R33D3M33R said:**
> What is the size and md5 checksum (run "md5sum shadowgroundsUpdate1.run" in the console) of the file?  ```
frankenstein@frankenstein-desktop:/media/frankenstein/T_Drive_Alternate_Storage_B/Gaming$ md5sum shadowgroundsUpdate1.run 7c9913f754168742973edfeb66ba8f1c  shadowgroundsUpdate1.run.
```  ```
 817.5 MB (817,462,983 bytes)
```

---

### Post by R33D3M33R on 2014-03-30
The checksum is ok. Can you change directory to /media/frankenstein/T_Drive_Alternate_Storage_B/Gaming and run the installer by: ./shadowgroundsUpdate1.run
Still problems?

---

### Post by Hodevah on 2014-03-31
Hi. And thanks for helping out again. 
First, this is where it is going to get a bit confusing for me if I try to run it on the external hard-drive. 

Should I begin a

```
sudo mkdir /media/loop
```

at that destination on the external hard-drive?
Kind of like I did in my first post above in the home directory whereby I started of with that command and follow those same command structure as listed? Because won't that mount a virtual drive of sorts on the external hard-drive?

Edit: I did try doing that. Here is the output:

```
frankenstein@frankenstein-desktop:/media/frankenstein/T_Drive_Alternate_Storage_B/Gaming$ sudo mkdir /media/loop
frankenstein@frankenstein-desktop:/media/frankenstein/T_Drive_Alternate_Storage_B/Gaming$ sudo mount -o loop -t iso9660 ~/media/frankenstein/T_Drive_Alternate_Storage_B/Gaming/shadowgrounds.iso /media/loop
/home/frankenstein/media/frankenstein/T_Drive_Alternate_Storage_B/Gaming/shadowgrounds.iso: No such file or directory
frankenstein@frankenstein-desktop:/media/frankenstein/T_Drive_Alternate_Storage_B/Gaming$ sudo mount -o loop -t iso9660 /media/frankenstein/T_Drive_Alternate_Storage_B/Gaming/shadowgrounds.iso /media/loop
mount: block device /media/frankenstein/T_Drive_Alternate_Storage_B/Gaming/shadowgrounds.iso is write-protected, mounting read-only
frankenstein@frankenstein-desktop:/media/frankenstein/T_Drive_Alternate_Storage_B/Gaming$ cp -R /media/loop/* ~/installer_temp/
cp: cannot create regular file &#8216;/home/frankenstein/installer_temp/&#8217;: Not a directory
frankenstein@frankenstein-desktop:/media/frankenstein/T_Drive_Alternate_Storage_B/Gaming$ cp -R /media/loop/* ~/installer_temp/
cp: cannot create regular file &#8216;/home/frankenstein/installer_temp/&#8217;: Not a directory
```

I have also  done this:

```
frankenstein@frankenstein-desktop:/media/frankenstein/T_Drive_Alternate_Storage_B/Gaming$ chmod u+rx ./shadowgroundsUpdate1.run
```
No go. 

I must be doing something wrong. Please let me know. You mentioned to run the .run file. But how exactly would I be executing the .run file?
Thanks kindly in advance again for your help.

---

### Post by R33D3M33R on 2014-04-02
I don't understand why are you insisting on mounting the iso if you have the .run file in the same folder. Just run it and that is it (If you were able to run md5sum on the file, then it's possible to execute it).

---

