---
title: "How to get data from Fedora?"
date: 2006-07-18
forum: Desktop Environments
---

### Post by nomadic on 2006-07-18
I've been using Fedora core 5 and recently installed Ubuntu 6.06.
I want to get my data (data, music, photos) from Fedora into Ubuntu. I want to access them from Ubuntu rather than burning them to CD/DVD and then loading them back in.
My Fedora partitions are sda5 (root) and sda6 (home).
My Ubuntu /etc/fstab has the following entries for the Fedora partitions
  /dev/sda5  /media/sda5 ext3  defaults  0  2
  /dev/sda6  /media/sda6 ext3  defaults,user  0  2
Both partitions are mounted in Ubuntu.

When I try to access /sda6 (Fedora home) from within Ubuntu it says
  Folder contents could not be displayed.
  You do not have the permissions necessary to view the contents.

It does allow me to access /sda5 ( Fedora root) although some folders e.g grub are blocked to me.(red square with white x in the centre alongside the folder)

By clicking Properties / permissions on /sda5 and /sda6 I can see that Group and Others have read and execute access.

Is my /etc/fstab wrong? Do I need to change the permissions on sda6 (and how?)

I would appreciate help in sorting this out pse?

nomadic

---

### Post by coffeecat on 2006-07-18
You're correct. It's almost certainly a permission problem.

Quite by chance I'm posting from Ubuntu in my Dapper/Fedora 5/SuSE 10.0 multiboot. I had a go dragging and dropping a file from my Fedora home onto my Ubuntu desktop without any problem, and then the penny dropped.

When you set up the first user account in Ubuntu it will have been given the uid 1000 - as per many distros. Your main group will be I can't remember which, but I've changed mine to 'users' (gid=100) for this very reason.

OK - now go into Fedora. You'll find that your first user account has a uid of 500, with a main group of the same name (if I remember correctly), with a gid of 500. Linux stores permissions as uids and gids, not names. There's your problem.

Solution? Make your main group 'users' in Ubuntu and then boot into Fedora. You can't change your uid and gid, so make a new account and assign it with the uid 1000, and assign it to the users group (which I think is also gid=100 in Fedora). Now you'll have to copy all your files into your new account's home. Not quite sure how you do this and get the permissions right, but if you succeed you should then be able to copy from your Ubuntu partition OK.

Afterthought. This may or may not work. Make your main group in the Fedora first created account 'users' (gid=100). Highlight all the files you want to copy/move with ctrl-A, right-click and check permissions and adjust as necessary.

I'll compare your fstab entried with mine in a moment, but I'll get this posted first.

---

### Post by coffeecat on 2006-07-18
OK - a few more thoughts. FWIW here is my fstab:

```
proc            /proc           proc    defaults        0       0
/dev/hda7       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     reiserfs defaults        0       2
/dev/hda2       /media/hda2     ext3    defaults        0       2
/dev/hda6       /media/hda6     ext3    defaults        0       2
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
``` 
hda1 = SuSE. hda2=shared data partition. hda6=Fedora. hda7=Ubuntu. All pretty straightforward and it works, mainly because I have set up all three user accounts in the three distros with uid=1000 and gid=100.

My afterthought in my last post. I'm hoping you can get away with just making the gid the same, but when you right-click for permissions you need to tick the 'write' box for group. That might do it.

And the simplest way of doing it? Beg, buy, borrow or steal an external usb hard drive formatted to fat32. The fat32 filesystem doesn't support owner permissions, so you can copy Fedora > USB drive, and then USB drive > Ubuntu without any problems. Much better than using CD/DVDs when you get read-only files when you copy back onto the hard-drive.

---

### Post by nomadic on 2006-07-18
hi coffeecat
Thanks for the reply.

no joy.
In Fedora I changed my user (UID 500)  to GID *users*.
In Ubuntu I changed my user (UID 1000) to GID *Users*
Back in Ubuntu I tried to access /sda6 data but same problem - you do not have the permissions to .....

I went back into Fedora and on the folders I want I went properties/permissions and changed the file group to *users*
Back into Ubuntu - same problem.

Looks like I may have to do this the hard way.

Nomadic

---

### Post by coffeecat on 2006-07-18
Sorry to hear it. In that case you probably have to have both the uid and gid the same in each distro. Remember, it is the **number**, not the name of the user and group identity that is important. Perhaps you could try making a new user account in Fedora as I suggested first.

Anyway, for the future, this is what I do when making up a multiboot. I've learnt this the hard way. I research what uid and gid the distro sets up for the first created account. If this is not 1000:100, I make a dummy account - 'firstuser' - just to get the thing going, and then create myname:users = 1000:100. This always works just fine.

---

### Post by r6rider on 2006-07-18
have you tried doing something like:

sudo chown -R <your new username>:<your new username>  on the folder?

---

### Post by nomadic on 2006-07-18
I've got it working.
I set up another user in Ubuntu with the same UID and GID as the user in fedora. From that user I can access all the Fedora data.

Since this is a new Ubuntu installation, I have very little data on it so I lose nothing by dropping my original Ubuntu user.

Certainly something to keep in mind when setting up new distros.

Many thanks for your help.

nomadic

---

### Post by r6rider on 2006-07-18
Kind of an unnecessary way of doing it. If you just changed the ownership of the files using chown as I suggested you wouldn't have had any problems. I just switched from fedora core 5 last week and had the exact same problem. man chown

---

