---
title: "Windows was mounted, but now can't access"
date: 2005-06-08
forum: Desktop Environments
---

### Post by twoseids on 2005-06-08
Hi all,

New user, love Ubuntu and Ubuntu Forums!  My friend set me up, and mounted my Windows partition so I could read from my Windows files, etc.

However, now I can't access them at all.  When I try to open the Windows folder from an application, I get the error message:  [COLOR=Red]Access to home/user/windows was denied[/COLOR].  When I go to Places --> Computer, I can SEE the Windows folder.  However, when I double-click on it, nothing happens.  When I right-click on it, the folder disappears!  If I left-click to undo my right-click menu, the Windows folder reappears again.

Another thing.  I have three little symbols attached to the Windows folder icon.  One is a blue box with a white arrow going up and left.  The other is a gold box with a white lock (permissions, I guess).  The third is a red box with a white X.

Any ideas as to how I can "unlock" this Windows partition?

---

### Post by Peter Alien on 2005-06-08
How was the Windows partition mounted ?

Check the permissions of the folder where Windows was mounted, who has access to it ?

---

### Post by twoseids on 2005-06-08
How do I find that out?  (Sorry, seems like a basic question, but I don't know)

---

### Post by xao on 2005-06-08
when you mount the drive, use the -o umask=0222 option. so on my system it would look like:

sudo mount /dev/hda1 /mnt/hda1/ -t ntfs -o umask=0222


that should clear some of that problem up....

---

### Post by Alexander Kirillov on 2005-06-08
[QUOTE=twoseids]How do I find that out?  (Sorry, seems like a basic question, but I don't know)[/QUOTE]
 1. Start an editor (gedit)
2. Open file /etc/fstab in the editor
3. Post the contents of this file here.

---

### Post by MrMojoRising on 2005-06-08
look at your 'fstab'......fire up a terminal and type:

```
sudo gedit /etc/fstab
```

This is the file that automatically mounts drives at startup.
To mount my Windows drive i have a line that looks like this.

/dev/hda1       /mnt/win        ntfs    ro,users,gid=users,umask=0002  0       0


this mounts my windows HD to the folder /mnt/win/  and the stuff after that is what permissions it has (for my setup this gives Read Only permission to any user that uses the computer)
 
You should have a line that looks something like this if your friend set it up the right way. But I think he handled the permissions wrong. 

So do what Alexander Kirillov said and paste your /etc/fstab file here so we can see what your friend did and help you out.
 ;-)

---

### Post by twoseids on 2005-06-08
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda6       /               reiserfs defaults        0       1
/dev/hda5       /boot           ext3    defaults        0       2
/dev/hda7       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda2	/mnt/windows	ntfs	defaults	0	0

---

### Post by xao on 2005-06-08
[QUOTE=twoseids]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda6       /               reiserfs defaults        0       1
/dev/hda5       /boot           ext3    defaults        0       2
/dev/hda7       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda2	/mnt/windows	ntfs	defaults	0	0[/QUOTE]


try changing the last line to 
/dev/hda2	/mnt/windows	ntfs	umask=0222	0	0


and then run the command:

sudo mount -a


see if that works (worked for me)

---

### Post by twoseids on 2005-06-08
[QUOTE=xao]try changing the last line to 
/dev/hda2	/mnt/windows	ntfs	umask=0222	0	0


and then run the command:

sudo mount -a


see if that works (worked for me)[/QUOTE]


Nope, same thing still happening.  Does it matter if I restart the computer?  Or would that be an instant change?

---

### Post by xao on 2005-06-08
No, you should not have to restart your computer.

I can only think of 2 things at the moment (the margarita im drinking is kicking in), some of these are not meant to insult your intelligence, but are only to make sure that all bases are covered.

try sudo mount /dev/hda(whatever the parition is)   /mnt/windows -t ntfs -o umask=0222
and see if that does anything....


I only ask this b/c this is something I am guilty of, but does /mnt/windows actually exist?

don't worry,. we will get to the bottom of this. I finally got my mounting problems resolved the other day, but i dont have many important files on my windows partition.

---

### Post by TeeJay on 2005-06-08
Try  sudo mount /dev/hda1 home/user/windows/ -t ntfs -o umask=0222

---

### Post by MrMojoRising on 2005-06-09
Ok, this will solve it......disregard any thing your friend told you to do....and follow this:

Open up a terminal and follow these steps...

1. sudo mkdir /mnt/windows
2. sudo gedit /etc/fstab
  
  -that line that reads "/dev/hda2 /mnt/windows ntfs defaults 0 0" erase it and replace it with :

**Copy And Paste This Just To Be Sure**
/dev/hda2       /mnt/windows        ntfs    ro,users,gid=users,umask=0002  0       0                                                                                            

3. Save fstab and exit gedit
4. reboot (Probably not neccesary but do it anyway)
5. while booting up you should see a line that reads mounting /dev/hda2 /mnt/windows...blah blah blah........and there should be an [OK] after it.
6. open up a terminal
7. cd /mnt/windows
8. ls
9. Voila!

---

### Post by bored2k on 2005-06-09
1. reboot is never necessary.  sudo mount -a will suffice.
2. The "ubuntu way" is to mount everything in /media/, not /mnt/

---

### Post by twoseids on 2005-06-09
Hey, it worked!  I used MrMojoRising's method, but I followed bored2k's advice and replaced /mnt with /media.  At first I was having permission issues still, but I rebooted and THAT is what did the trick!

So now I have a Windows folder under my Desktop and under /media (both of which work), and an empty Windows folder under /mnt.  I'm guessing I don't need to mess with it - or should I delete that or something?

Anyway, thanks again to everyone - Ubuntu Forums is batting a thousand!

---

### Post by bored2k on 2005-06-09
[QUOTE=twoseids]Hey, it worked!  I used MrMojoRising's method, but I followed bored2k's advice and replaced /mnt with /media.  At first I was having permission issues still, but I rebooted and THAT is what did the trick!

So now I have a Windows folder under my Desktop and under /media (both of which work), and an empty Windows folder under /mnt.  I'm guessing I don't need to mess with it - or should I delete that or something?

Anyway, thanks again to everyone - Ubuntu Forums is batting a thousand![/QUOTE]
 You can delete the /mnt one now.

---

### Post by twoseids on 2005-06-09
[QUOTE=bored2k]You can delete the /mnt one now.[/QUOTE]
 I had to look up how to do that, but I found it.  This is fun!  Thanks yet again bored2k!

---

