---
title: "Need help Combining home and My Documents"
date: 2008-02-26
forum: Desktop Environments
---

### Post by eeefresh on 2008-02-26
Now that Ubuntu has full read/write NTFS support, I would like to combine MS's My Documents folder with Ubuntu's home folder on a separate partition.  I already have a separate partition for My Documents, but I don't know how to also make that partition the default home folder in Ubuntu.  Here is my setup:

/dev/sda1 - Windows XP
/dev/sda2 - Ubuntu/root
/dec/sda4 - NTFS storage partition (currently being used as My Documents)

I have backed up both home and My Documents folder on another partition, so I am not concerned about losing any data.

Can anyone tell me how to make sda4 my new home folder?

---

### Post by Sam Lars on 2008-02-26
Is your /etc/fstab, mount /dev/sda4 to the same way you mount the NTFS drive, but mount it to /home.
About Windows, I'm not sure how, but I know that you can change where it puts the home directory.  Probably in user settings.

---

### Post by SOULRiDER on 2008-02-26
You can change it using the usermod command I believe, i STRONGLY suggest you dont do this though.

---

### Post by eeefresh on 2008-02-26
@ Sam Lars - Not sure what that first sentence means, but yes, you can change where My Documents points in XP.  I just had to right click on my documents, and it let's you redirect it to another partition.

@ soulrider - ummm...okay. I don't know what usermod does, but I will take your advice and stay away from it.

---

### Post by Zeroangel on 2008-02-27
I do NOT recommend that you follow Sam Lars' advice. This is because if you mount it as your /home/$USER folder, then from the windows side of things, gnome is gonna create a lot of hidden .settings folders that will be *very* visible when you boot into windows and go to your 'My Documents' folder.

One way to sort of do this is to use symbolic links. The first one is sort of basic.

1) Navigate to where you Windows drive is mounted
2) Go to "Documents and Settings/MyUsername"
A3) Hold the "alt" key and drag/drop the "My Documents" folder to your /home/$USER folder ($USER means whatever your username is)
A4) A menu will pop up saying "move here, copy here, link here" -- Select "link here".
A5) If you like, rename the folder to "Windows Documents" or similar.

And now you will be able to easily access your windows documents. You can do this with many other folders as well.

The other method involves symbolically linking a every subfolder in the My Documents folder (like My Pictures). It integrates things a little better to your Home folder. And this is accomplished by doing the step in A but with the following differences.

B3) Go into the "My Documents" folder on your windows drive
B4) Alt-drag all of your most important folders to your /home/$USER folder
B5) Rename them (the new sym links you created) to fit in better with how you want things named -- For example, I might symlink the My Pictures folder, but just call it "Pictures" or I might create a "Documents" folder on my Windows drive and symlink it to my ubuntu drive so that both installs can share my work-related word or opendocument files.

---

### Post by Sam Lars on 2008-02-27
You could always tell all the .Folders to be hidden in Windows...
You have the NTFS mounted automatically at boot?

---

### Post by eeefresh on 2008-02-27
Yes, all my drives, including the NTFS partition I want to use as home, are mounted on boot.

---

### Post by eeefresh on 2008-02-27
Thanks for the advice, zeroangel, but why do I need to set up symbolic links?  I may do that as a last resort, but I would prefer to just have one shared partition where I can dump all my videos pictures, etc.  Symbolic links will work, but then I would have an extra folder to open from within the home folder.

Psychocats has an older tutorial[ here]("http://www.psychocats.net/ubuntu/separatehome") that is pretty close to what I want to accomplish.  Here's an excerpt with my notes:

**Using the new partition**
Now, back in the terminal, I'm going to mount /dev/hda1 and /dev/hda7:

```
sudo mkdir /old
sudo mount -t ext3 /dev/hda1 /old
sudo mkdir /new
sudo mount -t ext3 /dev/hda7 /new
```

[COLOR="Red"]***I've already done this part, since I have the /dev/hda4 partition set up and it mounts when I boot up...although its NTFS  and not ext3, like in his example.***
[B][/COLOR]
Now we're going to back up the /home directory on the old partition and move it to the new partition:[/B]

cd /old/home
find . -depth -print0 | sudo cpio --null --sparse -pvd /new/
sudo mv /old/home /old/home_backup
sudo mkdir /old/home

Yes, one of those lines looks really complicated--please type it as is--or, if you're unsure of your typing skills, copy and paste it into the terminal. Believe me--the command is necessary.

Next, we're going to specify to use the new home partition as /home:
sudo cp /old/etc/fstab /old/etc/fstab_backup
sudo nano /old/etc/fstab

You'll then be taken to the nano text editor. Add in this line:
/dev/hda7 /home ext3 nodev,nosuid 0 2
[COLOR="Red"][B][I]
If I change that ext3 to NTFS, will it still work?[/I][/B][/COLOR]

---

### Post by Sam Lars on 2008-02-27
Yes, it should.  You can look in the forums for an example NTFS mount line.

---

### Post by eeefresh on 2008-02-27
Well, I was able to get the job done, but not the way I had intended.  I was making some changes based on what I found on [this Web site]("http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/") when somehow I mucked up my system.  It wouldn't let me login after reboot because apparently I had deleted my home folder...whoops!  

Luckily it was a fairly fresh installation, and since I had backed up all my data, I just reinstalled Ubuntu.  However, this time around I made sure to designate sda4 as the home partition during setup.  Now I have to reinstall all my programs, etc., but at least I now have My documents and home on the same shared partition.

Thanks to all who tried to help!

---

### Post by Zeroangel on 2008-02-27
EDIT: Nevermind. Good luck with your reinstall.

---

