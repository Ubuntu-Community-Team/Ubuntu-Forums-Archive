---
title: "problems mounting an external hard drive"
date: 2008-12-11
forum: General Help
---

### Post by Clauricaune on 2008-12-11
Hi

I've just installed Ubuntu on my comp and when I try to connect my external hard drive where I keep all my backup files, I get an error message telling me that it was unable to mount it. It does detect the hard drive, but I can't access it.

What it tells me to do is try to force the mount by using the command 'mount -t ntfs-3g /dev/sdf1 /media/disk -o force' but whenever I do that I get a message saying that only root can do that.

Does anybody know how to solve this problem?

Edit: nevermind, I've solved the problem. i'm a terrible noob at this.

---

### Post by xjcannonx on 2008-12-30
Please mark as solved ;)

---

### Post by fitheangel on 2008-12-30
i have the same problem! how did you do it???

---

### Post by balloooza on 2008-12-30
Just mounting a disk as root (sudo) is not a fix, in fact it is quite dangerous. fitheangel and Clauricaune can you post the results of
```
cat /etc/fstab/
```
You should not be using a disk as root, and it is annoying too have to mount it that way all the time :)

---

### Post by fitheangel on 2008-12-30
sure 
heres what i got

ubuntu@ubuntu:~$ cat /etc/fstab/
cat: /etc/fstab/: Not a directory

and 
ubuntu@ubuntu:~$ /etc/fstab
bash: /etc/fstab: Permission denied
ubuntu@ubuntu:~$

---

### Post by fitheangel on 2008-12-30
not very useful i know!!

---

### Post by balloooza on 2008-12-30
not
cat /etc/fstab/

```
cat /etc/fstab
```
with no  slash

---

### Post by fitheangel on 2008-12-30
oh sorry!!

ubuntu@ubuntu:~$ cat /etc/fstab
aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
ubuntu@ubuntu:~$

---

### Post by balloooza on 2008-12-30
that is wierd, and the misspell was my bad (I posted the slash)

can you post this
```
 ls -l /bin/mount
```

---

### Post by fitheangel on 2008-12-30
ubuntu@ubuntu:~$ ls -l /bin/mount
-rwsr-xr-x 1 root root 92584 2008-09-25 13:08 /bin/mount
ubuntu@ubuntu:~$ 


the bin/mount bit came up in red too!!

:S!!!

---

### Post by xjcannonx on 2008-12-30
Was this HD ever connected to another OS?

---

### Post by balloooza on 2008-12-30
I don't know why the fstab looks like that, what is your setup like, how new is this install, did you just use default options?

---

### Post by fitheangel on 2008-12-30
im running it off a disk that i downloaded yesterday. and i'm just logged in as a live session user as i didnt have a username or a password or anything. I know one of the problems is that windows had not been shut down properly.. if you look at my origional post [http://ubuntuforums.org/showthread.php?t=1025945&highlight=mount+hard+drive](http://ubuntuforums.org/showthread.php?t=1025945&highlight=mount+hard+drive)

i think that covers what i've done and am trying to do

---

### Post by balloooza on 2008-12-30
so are you wanting to mount a windows harddrive with a crashed windows installation on an ubuntu live cd? this is what I gether, are you trying to recover files?

---

### Post by xjcannonx on 2008-12-30
try using ntfs-config to read your internal drive```
sudo apt-get install ntfs-config
```if you can you can then copy over to your ext HD which we also need to get working

---

### Post by fitheangel on 2008-12-30
yup yup thats exactly what i'm trying to do, but ubuntu wont let me use my external hard drive and wont let me access my hard drive either

---

### Post by fitheangel on 2008-12-30
ok i tried it

this is what i got

ubuntu@ubuntu:~$ sudo apt-get install ntfs-config
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ntfs-config

---

### Post by balloooza on 2008-12-30
I was working on a simeler problem on a friends computer, it is a big problem, you might want to try the solution by xjcannonx, once that is installed, then I can help you mount booth dissks

---

### Post by fitheangel on 2008-12-30
i tried what xjcannonx said and i've posted what i got back... do you think that maybe its not possible then?

---

### Post by balloooza on 2008-12-30
Can you open up software sorces (located somwhere in the system > administration, and check all 4 repository boxes

---

### Post by fitheangel on 2008-12-30
ok i've done that and its downloaded some stuff......

---

### Post by balloooza on 2008-12-30
are you connected with ethernet, or wireless, or other. I can help you with a different linux distrobution, with ntfs support built in, and I can help you get it. but first, we should finish up this method, it mightb(should) work.

---

### Post by balloooza on 2008-12-30
now try to install the ntsf-config thing (use the old command)

---

### Post by fitheangel on 2008-12-30
yup i'm connected to wireless... i'm on it now :)

---

### Post by fitheangel on 2008-12-30
DONE!

I got this:


ubuntu@ubuntu:~$ sudo apt-get install ntfs-config
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ntfs-config
ubuntu@ubuntu:~$ sudo apt-get install ntfs-config
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  ntfs-config
0 upgraded, 1 newly installed, 0 to remove and 223 not upgraded.
Need to get 42.5kB of archives.
After this operation, 442kB of additional disk space will be used.
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/universe ntfs-config 0.5.5-0ubuntu1 [42.5kB]
Fetched 42.5kB in 0s (183kB/s)   
Selecting previously deselected package ntfs-config.
(Reading database ... 102335 files and directories currently installed.)
Unpacking ntfs-config (from .../ntfs-config_0.5.5-0ubuntu1_i386.deb) ...
Processing triggers for man-db ...
Setting up ntfs-config (0.5.5-0ubuntu1) ...
ubuntu@ubuntu:~$

---

### Post by balloooza on 2008-12-30
I guss the other method will not work with wireless (unless you have ethernet available) but don't worry about that now. You are fast at responding, thanks

---

### Post by fitheangel on 2008-12-30
lol i'm just desperate to get this sorted!... so whats the next step?

---

### Post by balloooza on 2008-12-30
it looks like all you have to do is run ntfs-config, then run:
```
sudo nautilus
```
and then click the internal harddrive and see if yoou see windows stuff

---

### Post by fitheangel on 2008-12-30
hmmm may not be as simple as that! (though i really wish it was)

it did both those (though i may be typing them wrong!?) 

ubuntu@ubuntu:~$ ntfs-config

** (ntfs-config:13026): WARNING **: Error : This programm need to be run as root.


ubuntu@ubuntu:~$ sudo nautilus
seahorse nautilus module initialized
Initializing nautilus-share extension
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


** (nautilus:13043): WARNING **: Unable to add monitor: Operation not supported

---

### Post by balloooza on 2008-12-30
as for your first commaand, I forgot to tell you, you need to be root (root is the system administrator ((kinda like your mouse on the allow button in windows)) but it is more developed and safer) so run
```
sudo ntfs-config
```
then when it is done, run
```
sudo nautilus
```
and dont mind the error, then try to mount the hard drive

---

### Post by balloooza on 2008-12-30
I am glad you are sticking with this, but we might want to look into the other method, tell me (if you cannot mount the internal hard drive with that method) if you can connect with ethernet to the internet, or if you have a second computer you could be on the forum with (then you could not use cut and past)

this other method requires a download of 50 MB and either a usb flash drive or a blank cd and a burner, but it is sure to work.

---

### Post by fitheangel on 2008-12-30
ok now its popped up with a box saying

"the following partitions were detected and can be configured"

Then it lists dev/sda1  and the same for sda2 sda3 and sda4
?? it wants me to <click here to set a mount point> 

How on earth do i do that????

eeekkk

---

### Post by fitheangel on 2008-12-30
ok as for the other option using another pc and a cd burner, i can do that, but i think it will have to wait until new years day now :S 
I have the crummyest timing!!!

---

### Post by balloooza on 2008-12-30
sounds like we should go to the other method, I don't want you to loose any files, and we are entering territory i am not fermiliar with.
dose your laptop have a cd burner, and do you have a blank cd-r or cd-rw, or do you have a usb flash drive. do you have annothher computer that you could be on the forum with?
I think this is the best chance to save your files.

---

### Post by balloooza on 2008-12-30
> **fitheangel said:**
> ok as for the other option using another pc and a cd burner, i can do that, but i think it will have to wait until new years day now :S 
I have the crummyest timing!!!

sory I did not get what you were saying, I can still help you.

---

### Post by fitheangel on 2008-12-30
erm... yes to all of the above! lol and i hate to say this but i think i will have to pick up on this on the 1st jan! its v.late now and i've been trying all sorts with my laptop for days now!

Do you think you will be avalible on the 1st to help me do your other idea?

---

### Post by balloooza on 2008-12-30
I should be, You can just put a message to me on this forum, but for now what you can  do is download
[http://sourceforge.net/project/showfiles.php?group_id=248002&package_id=302801&release_id=648596](http://sourceforge.net/project/showfiles.php?group_id=248002&package_id=302801&release_id=648596)
and select one of the downloads, the first to burn to a cd, or the last to make a bootable usb drive (usb drive is best)
then folow theese
[http://wiki.partedmagic.com/index.php/Creating_the_media](http://wiki.partedmagic.com/index.php/Creating_the_media)
to get the download onto your selected media, then I can walk you through how to start it, and help you with file copying, but once you have made the liveusb or the livecd then it easy how to copy the files, because it is all done through the nautilus type thing.

---

### Post by fitheangel on 2008-12-30
ok i will try thank tommrrow!!

thank you so much for all your help so far and i will contact you in a couple of days!

---

### Post by xjcannonx on 2008-12-30
> **fitheangel said:**
> ok now its popped up with a box saying

"the following partitions were detected and can be configured"

Then it lists dev/sda1  and the same for sda2 sda3 and sda4
?? it wants me to <click here to set a mount point> 

How on earth do i do that????

eeekkk


OK i was gone for a while, nice to see you have made some progress

This is just asking where to set a point to mount your windows partiton, this is good, it will just mount the partition and you should then be able to read write from it...

We got to mount that ext HD now lets find out what it is called, make sure it is hooked up and type```
df -h
```
see if you can see your external drive there...it will be [COLOR="Blue"]/dev/sd(x)[/COLOR] where (x) is whatever the letter for your ext drive is, you may know by the size of it...

if you cant find it in there does the ntfs-config say when it lists the different drives? 

Once you get the drive name for the external then run these commands```
sudo mkdir /media/windows
sudo mount [COLOR="Blue"]externalNameHere[/COLOR] /media/windows -o force
```

Once it is mounted I would then use ntfs-config and run all the way through it...set your mount point for you internal drive to /media/windows and then you should be able to do ```
gksudo nautilus
``` and navigate to your external drive...windows should be mounted to the windows folder, then just create a new folder and copy over the files that you need. Hope this works...anyone else comment if I missed something...

---

### Post by fitheangel on 2008-12-31
I've tried that but....nothing! i really don't understand these commands and ubuntu in general.... so when you say "This is just asking where to set a point to mount your windows partiton, this is good, it will just mount the partition and you should then be able to read write from it..."

What does that mean?? i still can't access my hard drive??

---

### Post by fitheangel on 2008-12-31
I've tried that but....nothing! i really don't understand these commands and ubuntu in general.... so when you say "This is just asking where to set a point to mount your windows partiton, this is good, it will just mount the partition and you should then be able to read write from it..."

What does that mean?? i still can't access my hard drive??

---

### Post by xjcannonx on 2008-12-31
Ok so lets do a little recap, where are we at...

you installed ntfs-config and got it to work to the point where it asked you to set a mount point but you didn't do anything yet right?

The mount point is just basicaly a place to 'hang' the data, like a hanger in a closet(i don't know...i'm bad at comparisons)

Since you are on a live cd and im not 100% sure I think it would be good to place the mount point on the external drive you are trying to use to copy the files from the broken windows hard drive.

We need to be abe to mount the external drive first though...and that is what we are trying to do. To do that you can use these commands to see if you can find out the device id of the external drive```
df -h
sudo fdisk -l
```

I would just look by size to see if you can identify your drive that way...There will be lines at the left like /dev/sda, /dev/sdb1,or whatever. That is the id we need so we can see where the external drive is located and mount it, 
[COLOR="Blue"]
Post those here before continuing[/COLOR]

so in turn we can take that and tell the internal windows hard drive to be mounted at a certain place(in this case on your external drive)

That mount point it will need to be at needs to be created first by the command```
sudo mkdir /media/WhatEverYouWant
```

The mount point will need to be put into ntfs-config so ntfs-config will mount it as read/write on your external drive, 

at the place it asks for the mount point, type this ```
/media/WhatEverYouChoseEarlier
```

OK I know that was a lot but maybe if you go step by step and post if anything unusual happens we can get this right...After this there is only a little bit more...

I'm logging off, i'll checkback tomorrow...Good Luck and remember that google is a friend to and I am by no means an expert :)

---

### Post by balloooza on 2008-12-31
I just did this yesterday, and I have the solution. You do not need to wory about the download, just do this. First we need 
```
sudo mkdir /media/windows
```
```
sudo ntfs-3g /dev/sda1 /media/windows -o force
```

then 
```
sudo mkdir exhrd
```
```
sudo ntfs-3g /dev/sdb1 /media/exhrd -o force
```
then run
```
sudo nautilus /media/windows /media/exhrd
```
this brings up two windows with your tyo dries, and it should look pretty straight forward

---

