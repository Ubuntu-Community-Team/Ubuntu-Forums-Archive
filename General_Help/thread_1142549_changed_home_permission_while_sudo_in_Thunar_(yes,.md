---
title: "changed home permission while sudo in Thunar (yes, it was stupid)"
date: 2009-04-29
forum: General Help
---

### Post by rlb.contact on 2009-04-29
Run Xubuntu 8.10, but doubt it makes a difference.


I know it was stupid, but it was the easy way to go. 

Scenario:

I have three users under home file

home/user1
home/user2
home/user3

User1 is the only sudo approved user.

I want to secure all of the home folders from each other. User3 is particularly nosy. User2 is me for everyday life. I keep User1 for sudo tasks.

the whole chroot command line seems a bit convulted. 
I logged in as User1.

As User1 I started up Thunar with Sudo and changed the persmission on User2 and User3 with no problems. I decided to change permission on User1 as well. I completed the process, and all of my toolbars disappeared. I was forced to shut down via the power button.

Went to boot up and all I got to was a command line for the name of my computer and request for a user and password. I tried logging in as all possible users with no luck. I need to undo damage to home directories.

Went to LiveCD. Can not find the actual directories on the hard drive. it shows an icon for the directory, but it only allows you to explore within the structure of the LiveCD. No matter where I looked, I couldn't find it. Catfish couldn't help either.

Went to Live Ubuntu. Same problem. It's as if the hard drive never existed and everything was run from RAM.

Questions:
1) How do I get to actual files on the harddrive?
Assumption:
I will only have the command line to work with.
2)Once there, how do I change the permissions with chroot or whatever.

Please help,
Thanks
Lee
:(

---

### Post by 3Miro on 2009-04-29
From the LiveCD go to Places and you should see your HD.

BTW why changinf permissions with chroot. You need to make separate groups for all users and then for all user1 and user2 files that should be hidden, change the other permission to zero (read on user/group/other).

---

### Post by rlb.contact on 2009-04-29
Default is home/yourusername. Whenever you add a user, it automatically allows other users to dig around unless your files are stored on your desktop. I could find a way to change the permissions using the addnextuser file. However, I couldn't find info on how to do it on current files. People were mentioning nautilus (which Xubuntu does not have.)

I'll definitely root around LiveCD and see what I can do.  Thanks
Lee

---

### Post by kanikilu on 2009-04-29
I'm a little confused as to what you did, but if you just want users to not have access to other users files, I think you just want to do something like:

```
sudo chmod 700 /home/username
```

This will remove all permissions from "group" and "other" so that only the "owner" and root/sudo can access the home directory. You don't need to do it recursively (chmod -R)...

Just make sure that ownership on the directories are set properly, otherwise you'll get an error and that user probably won't be able to log in.

Also, you shouldn't necessarily have to do this with the Live CD. When you boot up the computer, press ESC to get to the GRUB menu, choose the recovery mode option, and when presented with a menu, choose to drop to a root shell. This should allow you to do any necessary chmod, chown, etc. This will be text-only, though, so be prepared to do a little typing.

From your description in your first post, it's hard to say what you did, but, I think the following should at least get you pointed in the right direction:

*Note don't type the lines beginning with "//" they are just my comments, also since you are in a root shell, sudo is not necessary.
```
// chown all home directories to the appropriate user
chown user1:user1 /home/user1
chown user2:user2 /home/user2
chown user3:user3 /home/user3

// chmod all home directories so only the owner has permission to access
chmod 700 /home/user1
chmod 700 /home/user2
chmod 700 /home/user3
```

Again, this might not fix everything, since I don't know what you did in the first place (if you have a link to a thread or guide you followed, that would help give us more information to go off of), but it should at least get you started...

---

### Post by rlb.contact on 2009-04-30
Kanikilu,

Well, I'm new to this forum stuff. I started off with the first listing/post as a thread. That's where this all started.

I wanted to prevent other users from snooping around in other's home directories. So I went around and tried to change the permissions in each directory. It went well until I got to the directory (user1) I was working in. I lost my tool bars and had to force a shutdown.

When I tried to reboot the OS forced me into a shell of some sorts. I tried to log in (with any of my users names and passwords) and it would not accept them.

Does this help?

---

### Post by rlb.contact on 2009-04-30
Oh, it is a single OS on the drive. Xubuntu only. the Xubuntu Live (8.10) simply doesn't see the harddrive anywhere. It sees the USB drives (with their ext3 and NTFS formats) and allows access. 

The Live CD, as well as CD rescue, does not recognize the hard drive. It's as if it never existed.

---

### Post by kanikilu on 2009-04-30
I think this will be easier to fix in recovery mode, as you won't have to mess around with mounting the drive, chroot, or anything like that...

Can you get into recovery mode? If so, if you are weary of changing anything, just post the output of the following command, and we can take a look at the ownership/permissions:
```
ls -la /home
```

---

### Post by bodhi.zazen on 2009-04-30
> **rlb.contact said:**
> Run Xubuntu 8.10, but doubt it makes a difference.

</clip>



First, don't panic, this is actually very easy to solve.

STOP - Calm down :)

I assume you know about permissions and how to change them from the command line? If not, you use the command chown and chmod.

See :

[FilePermissions - Community Ubuntu Documentation]("https://help.ubuntu.com/community/FilePermissions") 

As has been suggested boot to recovery mode. You will be logged in as root.

If you wish to use X, simply enter the command:

```
startx
```

From the command line:

```
chown user1.user1 ~user1
chmod 770 ~user1
```

And reboot.

If you still have problems, we need to apply those settings recursively, with the -R, but we will then need to fix a few files.

See : [http://ubuntuforums.org/showthread.php?t=976610](http://ubuntuforums.org/showthread.php?t=976610)

:twisted:

---

### Post by rlb.contact on 2009-05-02
OK, it unfortunately did not work :(
I followed Bodhi's directions with the same results that I had before I tried to chown, chmod

I went ahead and did what Kanikilu said for more information, but nothing beyond that. Here is the command I gave at the root prompt:

ls -la /home

and I got the following:

total 20
drwxr-xr-x    5   root   root   4096   Apr 3  00:44 .
drwxr-x---   20   root   root   4096   Mar 24 05:15 ..
drwxrwx---   44   user1  user1  4096   Apr 29 06:42 user1
drwxr-x---   28   user2  user2  4096   Apr 27 04:48 user2
drwxr-x---   26   user3  user3  4096   Apr 28 06:32 user3

Any ideas?

Lee

BTW, why does the unicode text format used in the forums give equal spacing for all characters? Why should an "x" be larger than a "-" ? All of this was written in mousepad. It makes things a bit difficult to read, but I guess you could always cut and paste into another text editor

---

### Post by bodhi.zazen on 2009-05-02
what is the output of 

```
ls -la /home/user1
```

And what error message or problem are you getting when you boot ?

---

### Post by rlb.contact on 2009-05-02
A lot of stuff comes up. I'm not sure if all of it is actually viewable. In the old days of DOS, there was the /p option (pause if the screen was full before, then hit space, repeats behavior until it reaches the prompt. It might be the same here.

There is at least a screen's worth of info. A lot of it deals with my programs. It might be more useful if you could tell me what I should look for specifically, and if there is any special way of doing this.

I cannot use StartX. I can get to the interface, but none of my pointing devices (usb mouse, laptop pointing device) works so cut and paste isn't really an option.

Thanks for all of you help,
Lee

---

### Post by bodhi.zazen on 2009-05-05
> **rlb.contact said:**
> A lot of stuff comes up. I'm not sure if all of it is actually viewable. In the old days of DOS, there was the /p option (pause if the screen was full before, then hit space, repeats behavior until it reaches the prompt. It might be the same here.

There is at least a screen's worth of info. A lot of it deals with my programs. It might be more useful if you could tell me what I should look for specifically, and if there is any special way of doing this.

I cannot use StartX. I can get to the interface, but none of my pointing devices (usb mouse, laptop pointing device) works so cut and paste isn't really an option.

Thanks for all of you help,
Lee

What happens when you startx ? It could be a typo

```
startx
```

small s and small x

error message ?

---

### Post by CatKiller on 2009-05-05
> **rlb.contact said:**
> A lot of stuff comes up. I'm not sure if all of it is actually viewable. In the old days of DOS, there was the /p option (pause if the screen was full before, then hit space, repeats behavior until it reaches the prompt. It might be the same here.

There is at least a screen's worth of info. A lot of it deals with my programs. It might be more useful if you could tell me what I should look for specifically, and if there is any special way of doing this.

You can view output of a command a page at a time by piping it into less, like so:

```
ls -la /home/user1 | less
```

You can also redirect the output to a text file, like so:

```
ls -la /home/user1 > sometextfile
```

---

### Post by rlb.contact on 2009-05-06
thanks for the pipe stuff. I didn't know how to do it.

Someone posted a solution that I cannot find. I logged in once, the solution was there, and the next time it was gone. Sort of like a nameless gunslinger riding through town.

Remember, the problem was:

BOOT IN RECOVERY MODE SHELL

VISIBLE
sda1

NOT VISIBLE
USB drive

BOOT IN LiveCD

VISIBLE
USB drives

NOT VISIBLE
sda1
(cannot mount as sda is not found in fstab or mtab)

Wish I could remember how it was done, but it ended in Thunar. I copied all Home directories to USB drive. That was that. I am wiping the partitions and starting over with 8.10  I'll let some of the bugs work out of Xubuntu 9.04

To whoever you are, thank you!

Everyone else, thank you too!

---

