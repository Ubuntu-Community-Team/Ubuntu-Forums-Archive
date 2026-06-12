---
title: "No space left on sda1, please help to clean up"
date: 2009-04-11
forum: General Help
---

### Post by Domas on 2009-04-11
Hi all,

Ok, so I decided to clean up a bit my external hard drive. I trashed some movies (something like 50 gb's) and after that I found that I have no space on my dev/sda1 (root directory /). Now (obviously) I can't do anything. How can I found out where all those files (movies) went? Trash is empty. Thanks for help.

 $ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              12G   12G     0 100% /
tmpfs                 500M     0  500M   0% /lib/init/rw
varrun                500M  100K  500M   1% /var/run
varlock               500M     0  500M   0% /var/lock
udev                  500M  2.8M  498M   1% /dev
tmpfs                 500M   24K  500M   1% /dev/shm
lrm                   500M  2.0M  499M   1% /lib/modules/2.6.27-7-generic/volatile
/dev/sda3              50G   40G  7.1G  85% /media/disk
overflow              1.0M   32K  992K   4% /tmp

---

### Post by gpilkay on 2009-04-11
I did NOT invent or write this, but it is what I myself have saved to disk to use again and again for system cleaning.  You'd be amazed at what can come off.  I do not know if these will work with your external drive, though.

I make no warranty for how this will work with your system, of course, but it is what I've used myself.  Here you go:


Tip #1 - Getting rid of Residual Config packages - In Synaptic Package Manger, there is a built-in feature that gets rid of old Residual Config packages. Residual Config packages are usually dependency packages that are left behind after you uninstall a package from your machine. To use this feature, go to System > Administration > Synaptic Package Manager. On the bottom left hand corner of the window, click the Status button. In the list above the Sections, Status, Search, and Custom buttons, you should see the following text:
Quote:
Installed
Installed (local or obsolete)
Not installed
Residual config 
Click on the "Residual config" text. (If the "Residual config dialogue does not appear, that means you do not have any Residual Config packages on your machine and you can skip down to Tip #2.) Do you see the packages that popped up in the window on the right? Those are the Residual Config packages. To get rid of these pests, click on the box to the left of the package name and select "Mark for Complete Removal". After you have done that for all of the Residual Config packages, look at the top of the Synaptic Package Manger window. Do you see the green check mark with the text "Apply" right under it? Click that button, and you'll flush all those Residual Config packages down the toilet!


Tip #2 - Getting rid of partial packages - This is yet another built-in feature, but this time it is not used in Synaptic Package Manager. It is used in the Terminal. To access the Terminal, go to Applications > Accessories > Terminal. Now, in the Terminal, key in the following command (or you can just copy and paste from here):
Code:
sudo apt-get autoclean
Enter your password when prompted and press Enter. See the package names that appeared in the Terminal? Those were partial packages that have just been deleted. Say goodbye! That's it! This command deletes the not-so-fully-downloaded packages that you acquire when a package that is being downloaded is suddenly cancelled. This is my favorite little trick when it comes to getting rid of junk files.


Tip #4 - Getting rid of "orphaned" packages - For this tip, you need to download the "deborphan" package found in Synaptic Package Manager. "deborphan" finds "orphaned" packages on your system. It determines which packages have no other packages depending on their installation, and shows you a list of these packages. It is most useful when finding libraries, but it can be used on packages in all sections...

To open Synaptic Package Manager, follow the instructions in Tip #1. After opening up Synaptic Package Manager, click the Sections button on the bottom left hand corner of the window, if it is not already clicked. Next, at the top of the Synaptic Package Manager window, click the Search button. In the search window, key in the following text :
Quote:
deborphan 
Did the "deborphan" package popup in the package window? It probably did, unless you do not have the correct Repositories. Now, click on the box next to the "deborphan" package name. Click on Mark for Installation. Now click the Apply button at the top of the window and wait for the downloading and installing of the "deborphan" package to finish. Once that is done, open up the Terminal. Instructions for doing that are located in Tip #2. After you have gotten the Terminal open, key in the following command (or copy and paste from here):
Code:
sudo deborphan | xargs sudo apt-get -y remove --purge
Enter your password when prompted and press Enter. See the package names that appeared in the Terminal? Those were orphaned packages that have just been deleted. Say goodbye! This is my second favorite way of dealing with junk files.

Those are the main ones, the others I've not used myself.  If you search for 'Ubuntu clean-up' or 'system clean-up', you will find more, I'm sure.

---

### Post by kpatz on 2009-04-11
**sudo apt-get clean** will clean out residual from packages as well.

**sudo du -s /*** will list space usage for each directory off the root.  When you see a large one, use **sudo du -s /(dirname)/*** to get usage for the directories underneath it.

How much stuff do you have in your /home folder?

---

### Post by Domas on 2009-04-11
Thanks for the reply ! These tips are good and i am doing that by myself time to time to clean up some space, but in my case I have 12GB of root and it was all the time something like 6Gb free space. Now, after deleting movies from external hd all the 12GB is gone. I can't find the reason why is it full and now I can't do anything, even sudo apt-get autoremove, coz I got: 

Reading package lists... Error!
E: Unable to write mmap - msync (28 No space left on device)
E: The package lists or status file could not be parsed or opened.

Any ideas?

---

### Post by Domas on 2009-04-11
domas@c:~$ sudo du -s /*
6228	/bin
35688	/boot
0	/cdrom
2864	/dev
13384	/etc
du: cannot access `/home/domas/.gvfs': Permission denied
375144	/home
0	/initrd.img
0	/initrd.img.old
299472	/lib
16	/lost+found
41588032	/media
4	/mnt
392584	/opt
du: cannot access `/proc/5861/task/5861/fd/4': No such file or directory
du: cannot access `/proc/5861/task/5861/fdinfo/4': No such file or directory
du: cannot access `/proc/5861/fd/4': No such file or directory
du: cannot access `/proc/5861/fdinfo/4': No such file or directory
0	/proc
7447252	/root
8548	/sbin
4	/srv
0	/sys
616	/tftpboot
32	/tmp
2484116	/usr
335092	/var
0	/vmlinuz
0	/vmlinuz.old
domas@c:~$

---

### Post by drs305 on 2009-04-11
> **Domas said:**
> Thanks for the reply ! These tips are good and i am doing that by myself time to time to clean up some space, but in my case I have 12GB of root and it was all the time something like 6Gb free space. Now, after deleting movies from external hd all the 12GB is gone. I can't find the reason why is it full and now I can't do anything, even sudo apt-get autoremove, coz I got: 

Reading package lists... Error!
E: Unable to write mmap - msync (28 No space left on device)
E: The package lists or status file could not be parsed or opened.

Any ideas?

Domas,

When you deleted all the files they may have ended up in root's trash bin, where they still take up space. If you can get sudo to run, empty your trash and root's trash. Use SHIFT-DELETE to delete the Trash folder, otherwise it will go right back to .... Trash! Be careful using SHIFT-DELETE, especially with sudo, as you can't recover anything you delete.

For Hardy and later:
```

nautilus Trash:/  # SHIFT-DELETE all files in your user's Trash bin.
gksudo nautilus /root/.local/share/Trash  # SHIFT-DELETE the 'files' and 'info' folders

```

---

### Post by Domas on 2009-04-11
drs305 - thank you so much, you saved my day, I have back my 6Gb space and now I can go to work calm :)

---

### Post by iponeverything on 2009-04-11
empty the trash

---

### Post by NFblaze on 2009-04-11
> **drs305 said:**
> Domas,
```

nautilus Trash:/  # SHIFT-DELETE all files in your user's Trash bin.

```

Can you tell me the symbol that you use that automates execution of this line when pasted into the terminal?

---

### Post by drs305 on 2009-04-11
> **NFblaze said:**
> Can you tell me the symbol that you use that automates execution of this line when pasted into the terminal?

I merely copy the following into a terminal and hit ENTER. It automatically opens nautilus with the trash in the "Trash/files" folder in view. It doesn't let me navigate up but will let me delete all the trash. It even has an 'Empty Trash' button.
> 
nautilus Trash:/


You could also use either of these for the user's trash:
```

nautilus /.local/share/Trash
nautilus /.local/share

```

---

### Post by tommcd on 2009-04-11
If you avoid using **gksudo nautilus**, or avoid deleting stuff as root, then you will never have to worry about this.
Use the terminal and the **rm** command to delete stuff.
If you have write access to the files you can just delete them through nautilus as a regular user and they will not go into root's trash.

---

### Post by Sef on 2009-04-12
> Use the terminal and the **rm** command to delete stuff.

Be very careful with that command.  You can delete all the files on your hard disk if you make a mistake.

---

### Post by NFblaze on 2009-04-12
> **drs305 said:**
> I merely copy the following into a terminal and hit ENTER. It automatically opens nautilus with the trash in the "Trash/files" folder....

Thats not particularly what i meant....I meant that when I copied the code in the original post with Ctrl + C from firefox, and then pasted it into the terminal with Ctrl + Shift + V. It automatically executed the code without my need to press enter...and the trash can opened up automatically...which i thought was pretty cool.

I was wondering how you did that but....i guess you didnt explicitly make it do that in your code...

---

### Post by drs305 on 2009-04-12
> **NFblaze said:**
> Thats not particularly what i meant....I meant that when I copied the code in the original post with Ctrl + C from firefox, and then pasted it into the terminal with Ctrl + Shift + V. It automatically executed the code without my need to press enter...and the trash can opened up automatically...which i thought was pretty cool.

I was wondering how you did that but....i guess you didnt explicitly make it do that in your code...

You are correct. Once it's pasted it sometimes automatically runs. I actually find that a bit of a bother at times, since I like to see what I've pasted before I hit the ENTER button. 

Since I like to see what I've pasted before it executes when running something with "sudo" I often start the copy by omitting the "s" in "sudo" so I can see what I've pasted, then add the "s" and *then* ENTER. I'm just paranoid about running things as root.  ;-)

---

