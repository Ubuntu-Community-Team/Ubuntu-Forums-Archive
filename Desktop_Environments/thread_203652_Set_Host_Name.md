---
title: "Set Host Name"
date: 2006-06-25
forum: Desktop Environments
---

### Post by GuitarHero on 2006-06-25
I deleted my host name by accident and its screwing my system over.  I want to set ot back to ubuntu but Im not sure how.  something with editing /etc/hosts but i dont know what to put there.  I cant copy the contents because i cant get on the internet without my host name to set up networking so im on my windows box right now.  It says # The following lines are desireable for IPv6 capable hosts

then it lists something things that start like fe00::0 ip6-localhost and stuff like that.  What do I do to fix it?

---

### Post by littlespy on 2006-06-25
What you probably want to do is add this back into /etc/hosts

127.0.0.1 ubuntu

also you should add

ubuntu

to your your /etc/hostname file

---

### Post by GuitarHero on 2006-06-25
there is already a line that says
127.0.0.1 localhost ryan-desktop

I would overwrite that with your line, but the save button is greyed out... whats the deal?

It says i dont have permission but it never asked me to log in with the admin password or anything

---

### Post by karlsson88 on 2006-06-25
"sudo gedit /etc/hosts" or use "Nautilus" to open the file with "root permissions"... can it help?

---

### Post by GuitarHero on 2006-06-25
agh no using the terminal with sudo gives me sudo: unable to lookup (none) via gethostbyname()

it says none is my hostname:
ryan@(none):~$


Have I royally screwed over my OS install?

And I tried using nautilus to go to the file and edit it but it never asks for the login, is there a way to provoke it to make me login as root?

---

### Post by karlsson88 on 2006-06-25
i don't know, i did this same problem a few days ago, but i don't fu*ing remeber what i did to fix it! :S i tell you if i found out! :)

---

### Post by jimbob on 2006-06-25
My hostname is SD.

Here is my /etc/hosts file:

  127.0.0.1       localhost
127.0.1.1       SD.cfl.rr.com   SD

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

Here is my /etc/hostname file:

SD

Try replacing all the above SD's with your desired hostname.

Actually there is an environment variable called HOSTNAME which is pervasive throughout the system.  I don't know how to change that without a re-install.
Sorry.
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...
_________________________________
[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by GuitarHero on 2006-06-25
No see I cant replace anything because its not logging me in so i dont have the permissions to replace anything.....

---

### Post by mistab1034 on 2006-06-25
boot up a live cd and mount your drive:
```
mkdir /mnt/harddrive
mount -t ext3 /dev/hdd1 /mnt/harddrive 
``` 
then you can edit your /etc/hostname and /etc/hosts file with all the permissions you need, but they are now located under /mnt/harddrive
```
gedit /mnt/harddrive/etc/hostname
gedit /mnt/harddrive/etc/hosts
```

---

### Post by GuitarHero on 2006-06-25
I did sudo mkdir /mnt/harddrive
Then I did sudo mount -t ext3 /dev/hdd1 /mnt/harddrive 
and it said:
mount: special device /dev/hddl does not exist.



:(

---

### Post by GuitarHero on 2006-06-25
screw it ill just reinstall dapper.  thanks for the help.  Reinstalling will probably take less time than all this troubleshooting and i didnt really have anything on there i needed or cant get back easily.

---

### Post by Ramses de Norre on 2006-06-25
For what it's worth: I always use knoppix as a live cd for this purposes, it is designed for it and extremely easy to use. Mounting any partition is as easy as clicking on the icon for it on the desktop.. So this makes recovering errors like this way easier ;)

---

### Post by mistab1034 on 2006-06-25
Sorry, I don't know why I put hdd1, I should have explained that it might be something different.

To find the Device node of your hard drive perform the following command while booted to your installed system (not the live cd)
```
df
```
this should print a list of your disk usage. Look for the line that has a '/' in the last column, it should look something like this:

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1              20G  7.5G   11G  41% /
```
the corresponding first column is the device node that you want to replace hdd1 with, so in this case to mount the drive in the live cd it would be:
```
mount -t ext3 /dev/hda1 /mnt/harddrive
```

hope this isn't too confusing...

---

### Post by GuitarHero on 2006-06-25
Hey thanks got it to work! Now to get my network working.....

Well thanks!

---

