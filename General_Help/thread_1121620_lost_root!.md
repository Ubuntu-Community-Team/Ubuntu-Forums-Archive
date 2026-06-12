---
title: "lost root!"
date: 2009-04-10
forum: General Help
---

### Post by GlennW on 2009-04-10
Help!! I shouldn't feel like a complete noob but this sure proves it. I'm still relatively new to linux and absolutely love it! It is my tool (most of the time - LOL) as opposed to where in MS you're the tool!

Anyway, to the issue at hand. For some reason I needed to change permissions in /home folder. I think I was upgrading something. Whatever - inconsequential. So after restarting X a box came up saying something like /home/.dmrc (can't remember exactly) couldn't be located so therefore the language and session settings wouldn't be saved. No biggie. I then attempted to set things right and used nautilus to access /home and set the permissions the way they should be. But, alas, I've screwed something up! 

I think (I'm so flustered I can't remember) that I opened up properties and set the top option to glenn and then create and delete. The second one down (group I think) I set to root. Then at the bottom, clicked apply to included files or something like that. 

It took a little bit but finally the box closed. I went on with the session as per usual until I had to use the terminal. Then to my surprise it said: I have no name!@glenn-desktop$. Huh?

I had to restart and then the same initial box came up but followed by a second one that said your session lasted less than 10 seconds and will restart. 

I attempted to restart to see if that would help but to no avail. Just the two boxes and now a loop. I managed to login to a terminal and it is still as mentioned above. 

But, now what? How do I get things back to normal? Help!!

---

### Post by fahadsadah on 2009-04-10
Some files in your home directory, such as .ICEauthority, must not have their permissions changed.

Best solution is a reinstall, tbh.

---

### Post by GlennW on 2009-04-10
> **fahadsadah said:**
> Some files in your home directory, such as .ICEauthority, must not have their permissions changed.

Best solution is a reinstall, tbh.

Are you serious? Surely there must be way to regain control and restore order...

---

### Post by GlennW on 2009-04-10
Would it not help to use my live CD and try to establish root? Don't know how but I'm thinking out loud...

---

### Post by bapoumba on 2009-04-10
Did you change the permission of the /home folder as a whole?
Might be tricky to recover..

An intermediate solution is to boot in recovery mode from grub menu, you'll get to a root text session. Add a user:
```
adduser <choose_a_name_here>
adduser <your_new_mane> admin
reboot
```

You will be able to login with this new user and recover/save your important files from the previous user's /home.

---

### Post by GlennW on 2009-04-10
> **bapoumba said:**
> Did you change the permission of the /home folder as a whole?
Might be tricky to recover..

An intermediate solution is to boot in recovery mode from grub menu, you'll get to a root text session. Add a user:
```
adduser <choose_a_name_here>
adduser <your_new_mane> admin
reboot
```

You will be able to login with this new user and recover/save your important files from the previous user's /home.

Don't mean to be obtuse but how do I go about that? I'm currently sitting at the terminal in safe mode, I guess.

Thanks...

---

### Post by bapoumba on 2009-04-10
```
bapoumba@SonyBlue:~$ ls -la .dmrc
-rw------- 1 bapoumba bapoumba 47 2009-04-10 08:43 .dmrc

```
Couls you please post the output to the same command?

---

### Post by GlennW on 2009-04-10
> **bapoumba said:**
> ```
bapoumba@SonyBlue:~$ ls -la .dmrc
-rw------- 1 bapoumba bapoumba 47 2009-04-10 08:43 .dmrc

```
Couls you please post the output to the same command?

Output:

-rw------- 1 1000 glenn 28 2009-4-10 06:59 .dmrc

---

### Post by bapoumba on 2009-04-10
You are not from the live cd, am I correct?
```
bapoumba@SonyBlue:~$ id bapoumba
uid=1000(bapoumba) gid=1000(bapoumba) groups=1000(bapoumba),4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),107(fuse),109(lpadmin),115(admin)

```

---

### Post by frodon on 2009-04-10
I had several time this issue in the past at the dapper drake time, as mentioned before it can be .ICEauthority file permission issue which can be the result of not using sudo instead of gksudo for graphical root apps. To solve this issue quickly just delete the file (backup it if you want) and it will be recreated automatically.

Once this arrived to a friend in an even worst manner, i never understood how but after an ubuntu update all his /home files right were coorupted in some way. I restored the rights with the following commands :
```
sudo chmod -R o+rw /home
sudo chmod -R g+r /home
```Which respectively gives recursively read-write rights to all files for the owner of the files and read rights for members of the owner's group.

---

### Post by GlennW on 2009-04-10
> **bapoumba said:**
> You are not from the live cd, am I correct?
```
bapoumba@SonyBlue:~$ id bapoumba
uid=1000(bapoumba) gid=1000(bapoumba) groups=1000(bapoumba),4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),107(fuse),109(lpadmin),115(admin)

```

Nope!

---

### Post by GlennW on 2009-04-10
> **frodon said:**
> I had several time this issue in the past at the dapper drake time, as mentioned before it can be .ICEauthority file permission issue which can be the result of not using sudo instead of gksudo for graphical root apps. To solve this issue quickly just delete the file (backup it if you want) and it will be recreated automatically.

Once this arrived to a friend in an even worst manner, i never understood how but after an ubuntu update all his /home files right were coorupted in some way. I restored the rights with the following commands :
```
sudo chmod -R o+rw /home
sudo chmod -R g+r /home
```Which respectively gives recursively read-write rights to all files for the owner of the files and read rights for members of the owner's group.

Alright, I did that. There was no change other than asking for my password.

---

### Post by bapoumba on 2009-04-10
What does the id <your_username> return?

---

### Post by GlennW on 2009-04-10
> **bapoumba said:**
> What does the id <your_username> return?

id: glenn: No such user

Man, this does not look good!

---

### Post by GlennW on 2009-04-10
bump...

---

### Post by bapoumba on 2009-04-10
```

bapoumba@SonyBlue:~$ ls -ald /home/*
drwxr-xr-x 55 bapoumba bapoumba  4096 2009-04-10 08:43 /home/bapoumba
drwx------  2 root     root     16384 2008-06-28 23:53 /home/lost+found

```

Please post the output to the command.

Edit: please do not bump, I know you are impatient. I have some time ahead of me, so do others.

---

### Post by GlennW on 2009-04-10
> **bapoumba said:**
> ```

bapoumba@SonyBlue:~$ ls -ald /home/*
drwxr-xr-x 55 bapoumba bapoumba  4096 2009-04-10 08:43 /home/bapoumba
drwx------  2 root     root     16384 2008-06-28 23:53 /home/lost+found

```

Please post the output to the command.

Edit: please do not bump, I know you are impatient. I have some time ahead of me, so do others.

I apologize for the impatience.

Output:

drwxrwxrwx 96 1000 glenn     4096 2009-04-10 09:03 /home/glenn
-rw-r--rw- 1    0 root  512000000 2009-04-09 23:48 /home/mozdisk
-rw-rw-rw- 1 1000 glenn  18215873 2008-09-29 12:41 /home/setup798.exe

---

### Post by bapoumba on 2009-04-10
I am very unsure about what you did to come to this situation ;)
I am also unsure about what to do to recover your previous user, and if ever you can..

From what I understand, you are currently in safe mode, so backup what is important on removable media, considering you might loose everything.

Also write down the procedure to add a new user from here (this was my post #5): [http://ubuntuforums.org/showpost.php?p=7047244&postcount=5](http://ubuntuforums.org/showpost.php?p=7047244&postcount=5)

From user id in previous posts, I suppose glenn was the first user created.
```
sudo useradd -u 1000 glenn 
```

If it does not spit errors at you, you should also:
```
sudo adduser glenn admin
```

And then post the output to:
```
ls -ald /home/glenn
id glenn
```

You can wait and see if others have suggestions. I do not know why your root has this funky number.

I need to leave shortly, I'll check back here later on. All my best wishes :)

---

### Post by GlennW on 2009-04-10
> **bapoumba said:**
> I am very unsure about what you did to come to this situation ;)
I am also unsure about what to do to recover your previous user, and if ever you can..

From what I understand, you are currently in safe mode, so backup what is important on removable media, considering you might loose everything.

Also write down the procedure to add a new user from here (this was my post #5): [http://ubuntuforums.org/showpost.php?p=7047244&postcount=5](http://ubuntuforums.org/showpost.php?p=7047244&postcount=5)

From user id in previous posts, I suppose glenn was the first user created.
```
sudo useradd -u 1000 glenn 
```

[INDENT][COLOR="Red"][sudo] password for glenn:
useradd: user glenn exists[/COLOR][/INDENT]

If it does not spit errors at you, you should also:
```
sudo adduser glenn admin
```

[INDENT][COLOR="Red"]sudo adduser glenn admin
The user 'glenn' is already a member of 'admin'.[/COLOR][/INDENT]

And then post the output to:
```
ls -ald /home/glenn
id glenn
```

[INDENT][COLOR="Red"]ls -ald /home/glenn
drwxrwxrwx 96 1000 glenn 4096 2009-04-10 09:03 /home/glenn[/COLOR][/INDENT]
You can wait and see if others have suggestions. I do not know why your root has this funky number.

I need to leave shortly, I'll check back here later on. All my best wishes :)

Thanks for your help.

---

### Post by GlennW on 2009-04-10
@bapoumba. I wouldn't worry too much about it. I had backed everything up Wednesday (two days ago) so there's little to be lost. I've never had to re-install and thought that I'd post to the forum and see if there was something to undo my carelessness/stupidity. Now it's the hassle of downloading the lastest intrepid and making another disk. 

Thanks again. 
Happy Easter.

---

### Post by GlennW on 2009-04-10
@bapoumba.

On a whim I entered this in the terminal:

sudo nautilus and gave my password when asked. 

I can access my files via nautilus. Is this something that can be used to change permissions and fix this snafu?

---

### Post by bapoumba on 2009-04-10
I'm not sure as you have probably recursively changed the permissions to /home as a whole.

Anyway, you can go back to frodon's post and see how he fixed /home permissions.
If you prefer to go with nautilus, please go to > file system > home. Highlight glenn and right click > properties > permissions. Here is mine.

---

### Post by GlennW on 2009-04-10
> **bapoumba said:**
> I'm not sure as you have probably recursively changed the permissions to /home as a whole.

Anyway, you can go back to frodon's post and see how he fixed /home permissions.
If you prefer to go with nautilus, please go to > file system > home. Highlight glenn and right click > properties > permissions. Here is mine.

Well, I made mine look just like yours to no avail. I also ran frodon's as well with no luck. I guess I'm hooped...

I'll reinstall later today.

Thanks for the effort and the time.

Cheers!

---

### Post by bapoumba on 2009-04-10
No problem, I would have liked to understand what happened and help you better :)

---

