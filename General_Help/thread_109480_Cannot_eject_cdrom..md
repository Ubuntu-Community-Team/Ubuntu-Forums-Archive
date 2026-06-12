---
title: "Cannot eject cdrom."
date: 2005-12-28
forum: General Help
---

### Post by celluloid on 2005-12-28
Hey guys.
I've a music cd in my cdrom drive, usually I can just right click on the CD icon on my desktop, click eject and out comes the cd. However now when I do this, I get an "Eject Error" stating "eject: unable to eject, last error: invalid argument"
sudo eject and unmount /media/cdrom0 both do not work.

I cannot seem to get this cd out for the life of me, anyone able to help?

---

### Post by grte on 2005-12-28
Well, I don't know a *good* solution for the problem, but I know how you can get the CD out.

There should be a small hole on the face of your drive, somewhere.  It's the force-eject button.  Stick a paper clip in there and you'll be able to get it out.

---

### Post by pharcyde on 2005-12-28
Type df and you should see all devices that are mounted on teh system.  After doing this you should be able to see if/where the cd is mounted.  You could also try seeing what services/programs are loaded that may cause the cdrom to be locked.  You can issue the "killall -9 <appname>" to kill those.  Also have you tried rebooting?

---

### Post by Jammy_Stuff on 2005-12-28
Could try ejecting it from the recovery menu

---

### Post by astoltz on 2005-12-28
You can also try ```
sudo umount -l /dev/hdc
```(assuming the cdrom is at hdc).

---

### Post by caled67 on 2005-12-29
Install lsof (List open files.)

[FONT="Courier New"]# sudo lsof | grep /dev/XXX[/FONT]
(where XXX is your cdrom see /etc/fstab or eject -vvv)

[FONT="Courier New"]# kill XXXX[/FONT]
(the process id -first number- listed by lsof)

I have the "problem" described with mplayer since kernel 2.6.12-10-k7.

---

### Post by FerGeCo on 2006-05-09
caled: this was exactly what i needed .. didnt know lsof existed!
Thanx alot!

---

