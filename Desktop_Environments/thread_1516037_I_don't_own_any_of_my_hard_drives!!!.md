---
title: "I don't own any of my hard drives!!!"
date: 2010-06-23
forum: Desktop Environments
---

### Post by gandalf2000 on 2010-06-23
I had a problem after an update and ended up re-installing Lucid.  Now I don't own any of my hard drives.  In the "Permissions" tab of properties they say "The permissions of "*" could not be determined".  This is becoming a real problem as my the hard drive that has my Home on it is in "disc failure is imminent" mode and I need to copy everything to another drive urgently.  Please help before the Home disc dies.

---

### Post by fela on 2010-06-23
Do this:

[COLOR="Red"]**BE CAREFUL BEYOND THIS POINT. THE ADVICE I GIVE YOU FROM NOW ON CAN POTENTIALLY DESTROY DATA AND DO OTHER DAMAGE SO MAKE SURE YOU KNOW WHAT EACH COMMAND DOES BEFORE EXECUTING IT. I HAVEN'T USED THESE COMMANDS FOR A WHILE AND I COULD HAVE MADE AN ERROR SOMEWHERE.**[/COLOR]

**MAKE SURE THAT YOUR EXTERNAL DRIVE IS AT LEAST AS BIG AS THE DATA IN YOUR HOME FOLDER OF COURSE.**

So, assuming your external drive is /dev/sdb and it has one partition on it (it would by default) (you can check the sdx letter by entering ```
dmesg | tail
``` after plugging in the drive), follow this guide (REMEMBER TO REPLACE b IN sdb WITH THE APPROPRIATE LETTER):

Open up a terminal; enter

```
sudo su
mkdir /mnt/drive
mount /dev/sdb1 /mnt/drive
mkdir /mnt/drive/backup
cp -rafv /home/* /mnt/drive/backup/
chown -R $USER /mnt/drive/backup (replace $USER with your username)
chmod -R 755 /mnt/drive/backup
```

After this is done (and it will take a while with alot of data) the data in all home folders will be backed up and have the right permissions and ownership (read/write/execute for owner; read/execute for group; read/execute for everyone), and the owner will be your username.

---

### Post by varunendra on 2010-06-23
> **fela said:**
> Do this:[COLOR="Red"]**BE CAREFUL BEYOND THIS POINT. THE ADVICE I GIVE YOU FROM NOW ON CAN POTENTIALLY DESTROY DATA AND DO OTHER DAMAGE SO MAKE SURE YOU KNOW WHAT EACH COMMAND DOES BEFORE EXECUTING IT. I HAVEN'T USED THISE COMMANDS FOR A WHILE AND I COULD HAVE MADE AN ERROR SOMEWHERE.**[/COLOR]

:lol: I wouldn't dare to execute them If I were him (OP) after reading such scary warning! :lol:

If he simply creates a new folder in the destination drive, open nautilus with sudo, simply copy-paste all his data to the newly created folder & then changes the folder permissions to be accessible to all, clicking on "Apply Permissions to Enclosed Files", wouldn't it work?

I'm assuming he has to make a fresh install anyway.

---

### Post by nerdy_kid on 2010-06-23
yeah just run gksu nautilus and then you should be able to back up your home drive no problem.  then when its all copied, still using the root nautilus right click all the files you copied go to the permissions tab and select you as the user and apply to subfolders.

---

### Post by gandalf2000 on 2010-06-23
I tried the "copy and paste" thing and it won't let me do that, I guess because I don't own the drives.  Wish it were that easy.  Both of the other drives are USB by the way and I it is one of them that I need to use.  At the moment the computer is in suspend and I am writing this on my EEEpc.  I'll fire up the desktop when I am ready to carry out the above instructions.  Thank you for them varunendra.

---

### Post by varunendra on 2010-06-23
> **gandalf2000 said:**
> I tried the "copy and paste" thing and it won't let me do that, I guess because I don't own the drives.  Wish it were that easy.  Both of the other drives are USB by the way and I it is one of them that I need to use.  At the moment the computer is in suspend and I am writing this on my EEEpc.  I'll fire up the desktop when I am ready to carry out the above instructions.  Thank you for them varunendra.

I thought I'd deserve a thanx only if my suggestion helps!! :D

By the way, root can do **[COLOR="Red"]EVERYTHING WITHOUT A QUESTION....[/COLOR]** as far as I've learnt so far. Have you tried opening nautilus with sudo or gksudo before? If yes & it didn't help, then it's perhaps beyond my (ultra-limited) experience.

In such a case, I'd suggest to take a backup image of your data partitions with partimage or clonezilla first, & then try whatever fela has suggested.


EDIT: Just to be more clear- I meant to copy-paste from within nautilus opened with sudo (or gksudo- as nerdy-kid said) command:```
sudu nautilus
```
Do everything I or nerdy-kid said from within the same nautilus window.

---

### Post by nerdy_kid on 2010-06-23
> **varunendra said:**
> I thought I'd deserve a thanx only if my suggestion helps!! :D

By the way, root can do **[COLOR="Red"]EVERYTHING WITHOUT A QUESTION....[/COLOR]** as far as I've learnt so far. Have you tried opening nautilus with sudo or gksudo before? If yes & it didn't help, then it's perhaps beyond my (ultra-limited) experience.

In such a case, I'd suggest to take a backup image of your data partitions with partimage or clonezilla first, & then try whatever fela has suggested.


EDIT: Just to be more clear- I meant to copy-paste from within nautilus opened with sudo (or gksudo- as nerdy-kid said) command:```
sudu nautilus
```
Do everything I or nerdy-kid said from within the same nautilus window.

sudo nautilus messes up $HOME permissions im pretty sure.  You should use gksu instead so
```

gksu nautilus

```

---

### Post by gandalf2000 on 2010-06-24
Ok, I tried to used the first lot of instructions and when I enter this step "[COLOR="black"]***mount /dev/sdb1 /mnt/drive***[/COLOR]" it tells me that I "***must specify fi;e system type***".  So I didn't get very far with that.  Then I tried ***gksu nautilus*** and it said something about needing user share permissions.  Still no go.  Isn't there some way to get all the drives back into my ownership?

---

### Post by varunendra on 2010-06-24
> **gandalf2000 said:**
> "[COLOR=black]***mount /dev/sdb1 /mnt/drive***[/COLOR]" it tells me that I "***must specify fi;e system type***"
You need to know the filesystem type of sda1.  You can check it by the following command:
```
df -T
```
Say, if it is ext4, then the command would go as(after sudo su)```
mount -t ext4 /dev/sdb1 /mnt/drive
```

> **gandalf2000 said:**
> Then I tried ***gksu nautilus*** **and it said something about needing user share permissions**. Isn't there some way to get all the drives back into my ownership?
What did it say?
Did you try sudo nautilus as well? Whatever possible mess-up nerdy-kid warned about, shouldn't matter after setting permissions for all. Besides, once you made a fresh install, copying (instead of moving) the data back to your Home directory should automatically add appropriate permissions to the copied files.

In case of problems, post here the outputs of```
df -a -T
```

and```
sudo fdisk -l
``` with all the drives connected.

**_ONE GOLDEN RULE_:** If nothing works & you feel real emergency, then creating a backup image of your partitions is the golden rule. You can use Clonezilla Live or PingCD or SystemRescueCD for that.

(see [here]("http://goinglinux.com/articles/ClonezillaLive.html") for HOW TO USE Clonezilla)
(or [here]("http://www.dedoimedo.com/computers/free_imaging_software.html") for a tutorial on using both Clonezilla & PartImage)

---

### Post by gandalf2000 on 2010-06-24
I have to apologize to fela.  His instructions worked once followed correctly.  Thank you, fela.  I guess that the reason that the permissions of the hard drives still show "this drive" could not be determined" is because they all have extended partitions on them.  Thanks to all who answered the call.

---

### Post by varunendra on 2010-06-24
It's good to see things work out finally! :)

You should mark the thread as [Solved] now (Thread Tools> Mark Thread as Solved).

---

### Post by fela on 2010-06-24
Great, it's always good to get a problem solved and know that I helped along the way :)

---

