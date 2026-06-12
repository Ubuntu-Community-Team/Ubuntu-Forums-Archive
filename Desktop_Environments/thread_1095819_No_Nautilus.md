---
title: "No Nautilus"
date: 2009-03-14
forum: Desktop Environments
---

### Post by hacker_at_linux on 2009-03-14
Hey all please help me.

The other day I was playing Alien Arena. after I finished and closed the application I noticed that My nautilus was was slow,
So I went to the [FONT="Garamond"]System Monitor[/FONT] and Killed the process.

Now as usual the nautilus shd have started automatically but it didn't so I restarted the system.

Now a strange thing happened, when I restarted the system there was nothing

My screen is now blank with only the cursor.The cursor moves but there is nothing is it.

Now please tell me how to repair it.

My data is very precious to me

---

### Post by labinnsw on 2009-03-14
One option is: Boot from a live CD. Back up your home directory to another Drive (I use an external USB Hard disk)

Reinstall the System.

Restore your home directory.

The commands I use are listed below.

**TO DO THE BACK UP**

```
sudo su
cd /media/disk
``` # or the location where the file will be stored
```
tar cvpzf backup20090228.tgz /home/username
``` # substitute the path to your home directory for "/home/username"

**TO RESTORE**

```
tar xvpzf /media/disk/backup20090228.tgz -C /home/username
```

---

### Post by hacker_at_linux on 2009-03-14
Man I asked for a solution
I dont this it is 
Formating is no way to restore system

Please give me a good way to do this

I saw an option in Ubuntu server cd to restore broken system 
will that work


Help me fast
Please

---

### Post by hacker_at_linux on 2009-03-14
Hey people please reply fast I am running out of time.


I need to know y this is happening to my system and how can I repair it.



Please man 


I thought that this community was very helpful but sorry to say what I have experienced today.

[CENTER][B]
NO HELP AT ALL[/B][/CENTER]

---

### Post by Yownanymous on 2009-03-14
Try going with the fix that someone has offered. Don't be so ungrateful, people are doing this out of their spare time. Good luck getting such help when Windows goes bad.

---

### Post by hacker_at_linux on 2009-03-14
> **Yownanymous said:**
> Try going with the fix that someone has offered. Don't be so ungrateful, people are doing this out of their spare time. Good luck getting such help when Windows goes bad.

Well man this is not a fix.
I have my full data in there and cannot access it.

And if you r tking about windows , Man there are 1001 communities there helping you professionally not doing in spare time.

I am just concerned about my data.

Please can any one tell me how to repair this problem

---

### Post by oyayitsminh on 2009-03-14
Wow your not going to get any help with that kind of attitude. You should go find some help on your Windows forums then.

---

### Post by iKonaK on 2009-03-14
> Try Alt.+F2 and type [I]nautilus
> [/I]If that dose not work, create a new user and copy your personal files to that one, you can do that by Alt.+F2 and type *users-admin*

** *it would be nice to change your attitude considering we are all volunteers ;)

---

### Post by hacker_at_linux on 2009-03-14
Man can you tell me where to press the ALT F2 because there is no screen.

These is just one boot screen and the I hear the sound of login and them its all blank.

There is nothing.

I think it can only be done form the root shell in the recovery mode. But wht I need to download or install or type in there to do that.

And is repairing from Server cd Safe.


HELP

---

### Post by munishvit on 2009-03-14
> **Yownanymous said:**
> Try going with the fix that someone has offered. Don't be so ungrateful, people are doing this out of their spare time. Good luck getting such help when Windows goes bad.

I appreciate you for this comment...;)

---

### Post by hacker_at_linux on 2009-03-14
But I dont Cuz no help till

If you agree prove and give me some serious steps to repair my system.

---

### Post by iKonaK on 2009-03-14
> **hacker_at_linux said:**
> Man can you tell me where to press the ALT F2 because there is no screen.

These is just one boot screen and the I hear the sound of login and them its all blank.

There is nothing.

I think it can only be done form the root shell in the recovery mode. But wht I need to download or install or type in there to do that.

And is repairing from Server cd Safe.


HELP
First, Alt.+F2 are the keys on your keyboard....
Second, in your first post you didn't specify that you can't see the GDM (login screen)
Try to Ctrl.+Alt.+F1  (or other number from F1 to F6) and type:
```
yourmane
yourpass
sudo su
yourpass (assuming you have admin privileges)
aptitude purge gdm
aptitude install gdm
reboot (and optionally repeat the task and add a new user with the below lines)
useradd yournewuser
passwd yournewuser
(and type the pass)
```*after each line hit enter :)
>if nothing will work you can just reinstall and you don't have to format as you suggested, GNU/Linux just as the awful Microsoft Windows can be installed whit out formating the disk
> in the future consider to make a special partition for /home (the place where you keep you personal files :)

---

### Post by hacker_at_linux on 2009-03-15
Thanks Man I solved it

But not this way I think it was only the nautilus prob

I Installed the new nautilus form Jaunty version.


Thanks all For help

Ill approach you in future if I require help

---

