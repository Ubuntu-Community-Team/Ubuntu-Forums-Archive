---
title: "Disable CDROM Eject Button"
date: 2006-09-28
forum: Desktop Environments
---

### Post by SonWon on 2006-09-28
How do I disable the physical eject button on the cdrom?  I still want eject to work on the popup menu.  This is so the CD will be locked in the drive until the user ejects the CD.  Currently with Dapper's default configuration anyone can remove the CD and walk off with it, provided they know how to press the eject button. ;) 

Thank you,
SonWon

---

### Post by CatKiller on 2006-09-28
I believe that the eject button is automatically locked while the drive is in use. As long as you can make sure that something or someone is using the drive at all times, no one will be able to steal the cd without rebooting the computer.

---

### Post by SonWon on 2006-09-29
Thanks for the reply.  Relies on user interaction which will not always work.

Anyone have another idea?

I seem to remember it worked this way with Hoary; I think it was Hoary?

---

### Post by AT-AT on 2006-09-29
For me I can eject the CD while its working, the drive just quits operating, and once the CD stops spinning, out comes the disk. I suggest physically disabling the button, i.e. take the button off the circuit its connected to, and put some wire insulation around the button connect point so random fluctuations dont cause the eject mechanism to trigger. That way telling the computer to eject the drive through a command should be the only way the disk can come out. Be advised Im not an expert on this, so you might not want to fiddle with your drive unless you're completely sure there wont be any adverse side effects.

---

### Post by SonWon on 2006-09-29
Thanks,

This would work but I was hoping for a software solution.

Anymore ideas?

---

### Post by CatKiller on 2006-09-29
> **SonWon said:**
> Thanks for the reply.  Relies on user interaction which will not always work.

Not necessarily. You could have another user logged in, running a cron job of ls /cdrom every minute. That'd keep the cd drive in use. I'm sure that someone can think of a more elegant solution, but you don't have to actually be there using the drive for it to be in use. In fact, I suspect that even if the other user just mounts the cdrom and then is at the cdrom path it  would count as "in use" as far as any other user is concerned.

---

### Post by amo-ej1 on 2006-09-29
on a linux without automounter setup and such you are not able to eject the cd-rom when it is mounted, so when you get rid of all kinds of automounters, mount the cd-rom and disallow non root users to umount it will fix your issue.

(no actually it won't since they will simply  power cycle the machine and eject it then or is your next question how to physically protect the power button ;-) )

---

### Post by SonWon on 2006-09-29
Actually, I like the auto mount but I don't like the auto unmount feature.  I think the auto unmount is trigger by the eject button.  I was thinking all that needed to be done was to disable the auto unmount feature and then the CD would stay locked in place until I unmount via the eject menu choice.  Or I could just setup a script to unmount the drive.  I am a bit of a newb so I may not have used all of the correct terminology.

I am not worried about the power button.  I just don't want a CD to disappear casually.

Thanks,

---

### Post by CatKiller on 2006-10-06
From **man mount**:>        Thus, given a line
              **/dev/cdrom  /cd  iso9660  ro,user,noauto,unhide**
       any user can mount the iso9660 file system found on his CDROM using the
       command
              **mount /dev/cdrom**
       or
              **mount /cd**
       For more details, see **fstab(5)**.  Only the user that mounted a  filesys&#8208;
       tem  can unmount it again.  If any user should be able to unmount, then
       use **users** instead of **user** in the _fstab_ line.  The **owner** option is simi&#8208;
       lar  to the **user** option, with the restriction that the user must be the
       owner of the special file. This may be useful e.g.  for  _/dev/fd_  if  a
       login  script  makes  the console user owner of this device.  The **group**
       option is similar, with the restriction that the user must be member of
       the group of the special file.


So the options are there to make it so that the device gets mounted by root at bootup, and then no one can eject the cd.

Good luck.

---

### Post by SonWon on 2006-10-07
Thanks for the reply.

I think what I am looking for is a way to turn auto umount off but allow auto mount.  I already know I can lock the drive but that isn't the type of action I am looking for.

Maybe I should just open the drive up and disabe the switch?  I know there should be a way to do this with software and this is a laptop which makes it a little harder to get to the switch.

SonWon

---

### Post by CatKiller on 2006-10-07
Crikey. I'd be more worried about them wandering off with the laptop. But yes, if you want the user to be able to be able to mount and unmount the cd, but not have the eject button work, then the most straightforward way does look like physically disconnecting the button. You could probably intercept the signal from the button in the same way that locking the cd because it's in use does, but that's way above my ability. 'Course, whatever you do, someone'll still be able to stick a paperclip in the hole to eject it. Sorry I couldn't find you a better solution.

---

### Post by fisherking on 2006-10-29
I found this: 
[http://forums.gentoo.org/viewtopic-p-1190847.html#1190847](http://forums.gentoo.org/viewtopic-p-1190847.html#1190847)

Helped me since I also had this problem! 
But since I have two drives I shall (if I can ever get the time...) modify it  accordingly. I will also try to (time issues!) write it as a daemon which sence if the drives are locked or not. 
This program unlockes the drive if 'eject' is used!

---

### Post by SonWon on 2006-10-29
Great find, it almost does what I am looking for.

It does lock the CD hardware eject button but does not lock when there is a CD in the drive?

Any ideas how to add that functionality?

Thank you,
SonWon

---

