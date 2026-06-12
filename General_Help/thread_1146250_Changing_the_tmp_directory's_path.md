---
title: "Changing the tmp directory's path"
date: 2009-05-02
forum: General Help
---

### Post by JohnnyBoy928 on 2009-05-02
Hello guys and thanks in advance for any help...

I am trying to install a app on ubuntu and when i do it says that the tmpdir does not have enough space. Even with it emptied it maxes out at 1000M when I actually need it to be 1200M.. This is to run a MOHAA server... I already spent 2 whole days trying to get this tmpdir fixed...

I already created a /tmp directory under my home folder and chmod777... I would like to switch it to that directory. I tried 'export TMPDIR=/home/admin/Desktop/tmp' but no luck I also tried mounting the path but again no luck... 

I know the Fstab can do this as well but I also had no luck with this... 

The root partition is 4 gigs with only around 1000M left on it like I said... Also emptied tmp directory already but not enough room... any ideas how to solve this issue???

so what i need is either change partition size without loss of data lol.. or just point the /tmp dir to where there is room... Anything you guys need from me just let me know.. and I appreciate this... Anything I tried changing is now set back to the way it was originally without this problem so I can start from scratch with your help... ty guys... Ubuntu is a nice system for server side for me.. :)

---

### Post by taurus on 2009-05-02
If you only have one /, then the disk space of / is the same as /tmp.  Therefore, you need to remove some files from your machine to create or space.

```
sudo apt-get clean
sudo apt-get autoremove
df -h
```
Did you really create an admin account when you installed Ubuntu?

---

### Post by hyperdude111 on 2009-05-02
what is running, my temp only has "63 items, totalling 40.6 KB"

---

### Post by JohnnyBoy928 on 2009-05-02
> **taurus said:**
> If you only have one /, then the disk space of / is the same as /tmp.  Therefore, you need to remove some files from your machine to create or space.

```
sudo apt-get clean
sudo apt-get autoremove
df -h
```Did you really create an admin account when you installed Ubuntu?


Thank you will try this... 

Yes I created an admin account... why?

---

### Post by JohnnyBoy928 on 2009-05-02
> **hyperdude111 said:**
> what is running, my temp only has "63 items, totalling 40.6 KB"


Yeah my temp has only 24k in a few files as well... but  when they set this server up they only allocated so much for the root system.. I think like 2gigs or something... 

Only my other server with ubuntu I have no issues at all with allocation... works great and of course... I set that one up.. lol kidding... 

This one is running... Hmmm lets see...

IRC SERVER
APACHE
GNOME
FIREFOX
WINE w/ various apps... 

Everything works just fine and no problems.. I just need a tmp dir with more space in it... even if its temporarily..

but will try these and post back... thank you guys... 
I am also trying to install a game server on this system and need alarger then normal size for this...

---

### Post by JohnnyBoy928 on 2009-05-02
okay i did this and it did free 64 megs of space... but not enough to do what I need... This is becuase when this system was handed to me the initial install limited the OS partition to certain amount of space... I just simply need some more... lol 

There is no way of changing this??? 

here is the info
rootfs                5.0G  3.7G  1.1G  79% /
/dev/root             5.0G  3.7G  1.1G  79% /
tmpfs                 998M  120K  998M   1% /var/run
tmpfs                 998M     0  998M   0% /var/lock
/dev/root             5.0G  3.7G  1.1G  79% /dev/.static/dev
udev                  998M   20K  998M   1% /dev
tmpfs                 998M     0  998M   0% /dev/shm
tmpfs                 998M  120K  998M   1% /var/run
tmpfs                 998M     0  998M   0% /var/lock
/dev/sda2             224G  184G   29G  87% /home
tmpfs                 1.6G     0  1.6G   0% /home/admin/Desktop/tmp

the last one I would like to be the official tmp directory... Looks like I am almost there... lol can I edit [COLOR=DarkRed]**fstab **[/COLOR]to accept tmpfs                 1.6G     0  1.6G   0% /home/admin/Desktop/tmp as the tmp directory?

I even cleared out the space. I am shy about 200 megs still... .. The actual drive space went up to a gig, but the error keeps happening cause there is only 1000M for tmp directory... LOL  

*****************************
There is not enough free diskspace in your TMPDIR
You need about: 1200 MB
Try: export TMPDIR=/where/you/have/space
*****************************

I have done this with no success... I use
export TMPDIR=/home/admin/Desktop/tmp but no luck... again guys THANK YOU... Ubuntu is pretty amazing I believe... 

> **taurus said:**
> If you only have one /, then the disk space of / is the same as /tmp.  Therefore, you need to remove some files from your machine to create or space.

```
sudo apt-get clean
sudo apt-get autoremove
df -h
```Did you really create an admin account when you installed Ubuntu?

---

### Post by dcstar on 2009-05-02
> **JohnnyBoy928 said:**
> okay i did this and it did free 64 megs of space... but not enough to do what I need... This is becuase when this system was handed to me the initial install limited the OS partition to certain amount of space... I just simply need some more... lol 

There is no way of changing this??? 
..........
tmpfs                 1.6G     0  1.6G   0% /home/admin/Desktop/tmp

the last one I would like to be the official tmp directory... Looks like I am almost there... lol can I edit [COLOR=DarkRed]**fstab **[/COLOR]to accept tmpfs                 1.6G     0  1.6G   0% /home/admin/Desktop/tmp as the tmp directory?

.........

Mount the tmpfs as /tmp instead of /home/admin/Desktop/tmp

---

### Post by JohnnyBoy928 on 2009-05-03
> **dcstar said:**
> Mount the tmpfs as /tmp instead of /home/admin/Desktop/tmp

It already is at the /tmp dir and I want to change it to the '/home/admin/Desktop/tmp' where there is ample space for it... 

All I would like to do is set this path as the tmpdir with at least 5 gigs of space to it. or just leave it open to a space restriction...
'/home/admin/Desktop/tmp '

Is there a command for that or a fstab line to add... maybe both? lol just something to make '/home/admin/Desktop/tmp' the actual temp directory and ignore the other one that is /tmp

I already mounted tmpfs and that is why that showed up above... but I am lost with what to do next I guess with that to make it the actual tmp dir. 

before ubuntu I was at basic linux commands knowledge for my server needs... Now with ubuntu and new server side things I am doing I have had to make the quantam leap..lol but enjoyed everymoment so far with what I have learned with ubuntu and more command prompt features... been pretty neat... 

I appreciate everyone's reply's... This is a great OS for what I am doing. Much Thanks to Dev team!!!

---

### Post by JohnnyBoy928 on 2009-05-03
also now when I try to install a module in the synatic-pack I get this error

##WARNING /tmp orbit-root has wrong permissions... lol

Man what did I do? lol

---

### Post by JohnnyBoy928 on 2009-05-03
Well I got the orbit-root fixed...
I don't want to touch anything else till I hear from you guys.. So I will wait patiently.. lol

Thank You

:popcorn:

---

### Post by JohnnyBoy928 on 2009-05-04
> **dcstar said:**
> Mount the tmpfs as /tmp instead of /home/admin/Desktop/tmp

NOW!!! I understand what ya meant... lol Just direct that to /tmp and tell it to be 2gigs big... 

Thank you! Thank You! Thank You!

WORKED GREAT so for someone in the future... here's what to do in layman's terms. 

TO CHANGE /tmp DIRECTORY'S ALLOCATED SIZE!!!

1. Have to gedit or nano '/etc/fstab' - might have to change permissions on file (CHANGE BACK PERMISSIONS WHEN DONE FOR SECURITY REASONS)

2. Add this line below to the 'fstab' file 
    tmpfs      /tmp   tmpfs  size=2024M,mode=0777         0 0
(change 'size=2024M' to whatever size you want to allocate the /tmp directory - if one already exist then change file size)
 
3. Save File and Reboot system....

Sounds about right?
No need to mount the /tmp directory since it is already done if you have a normal /tmp directory with default setup of ubuntu....

THANKS GUYS... MUCH RESPECT!!!! - Problem Solved...

---

