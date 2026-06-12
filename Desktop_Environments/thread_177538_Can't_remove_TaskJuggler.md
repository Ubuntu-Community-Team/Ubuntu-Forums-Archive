---
title: "Can't remove TaskJuggler"
date: 2006-05-16
forum: Desktop Environments
---

### Post by Paintrick on 2006-05-16
Hey guys, I consider myself a just above beginner Ubuntu/Linux user, and fase this problem:

I can't remove Taskjuggler, not by Synaptec or Apt-get.

I try'd some instructions on other sites where people had the same error with different programs.

here is the output of the terminal:

> 
apt-get remove taskjuggler
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  taskjuggler
0 upgraded, 0 newly installed, 1 to remove and 28 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 4321kB disk space will be freed.
Do you want to continue [Y/n]? Y
dpkg: error processing taskjuggler (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
terminate called after throwing an instance of 'std::logic_error'
  what():  basic_string::_S_construct NULL not valid
Aborted
root@a:/# Errors were encountered while processing:
 taskjuggler



Ok, it says to try to reinstall it.

Here's the output:
> 

apt-get install taskjuggler
Reading package lists... Done
Building dependency tree... Done
taskjuggler is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 28 not upgraded.
1 not fully installed or removed.
Need to get 0B/1179kB of archives.
After unpacking 0B of additional disk space will be used.
Selecting previously deselected package taskjuggler.
(Reading database ... 140591 files and directories currently installed.)
Preparing to replace taskjuggler 2.2.0-1ubuntu1 (using .../taskjuggler_2.2.0-1ubuntu1_i386.deb) ...
Unpacking replacement taskjuggler ...
touch: missing file operand
Try `touch --help' for more information.
dpkg: warning - old post-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
touch: missing file operand
Try `touch --help' for more information.
dpkg: error processing /var/cache/apt/archives/taskjuggler_2.2.0-1ubuntu1_i386.deb (--unpack):
 subprocess new post-removal script returned error exit status 1
touch: missing file operand
Try `touch --help' for more information.
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/taskjuggler_2.2.0-1ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


I also try'd to get the cache erased, and then to fix the packages then i get:

> 

root@a:/# apt-get clean
root@a:/# apt-get -f install
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 28 not upgraded.
1 not fully installed or removed.
Need to get 1179kB of archives.
After unpacking 0B of additional disk space will be used.
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe taskjuggler 2.2.0-1ubuntu1 [1179kB]
Fetched 1179kB in 1s (610kB/s)
(Reading database ... 140591 files and directories currently installed.)
Preparing to replace taskjuggler 2.2.0-1ubuntu1 (using .../taskjuggler_2.2.0-1ubuntu1_i386.deb) ...
Unpacking replacement taskjuggler ...
touch: missing file operand
Try `touch --help' for more information.
dpkg: warning - old post-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
touch: missing file operand
Try `touch --help' for more information.
dpkg: error processing /var/cache/apt/archives/taskjuggler_2.2.0-1ubuntu1_i386.deb (--unpack):
 subprocess new post-removal script returned error exit status 1
touch: missing file operand
Try `touch --help' for more information.
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/taskjuggler_2.2.0-1ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)



So I'm kind of out of options :( 

What can I try?

thx! P

---

### Post by Paintrick on 2006-05-16
I didn't really had time to check more options..

The thing I hate is: I was trying to do an upgrade, yet EVERY time the stupid taskjuggler program comes with the error.

Anyone has a way around or the solution?

thx

---

### Post by Paintrick on 2006-05-17
I had some time today and took a deeper look at the files and functions it uses.

I notished the programs Touch (from coreutils) and Dpkg (the deb package manager)

>  dpkg -C
The following packages are in a mess due to serious problems during
installation.  They must be reinstalled for them (and any packages
that depend on them) to function properly:
 taskjuggler          Project management application


there is something wrong..

So I reinstalled, didn't work. :(

also the touch problem:
> touch: missing file operand

is a problem..

I don't know what to do here.

P

---

### Post by Paintrick on 2006-05-17
Even when I try it manually it doesn't work

> root@a:/var/cache/apt/archives# dpkg --unpack taskjuggler_2.2.0-1ubuntu1_i386.deb
(Reading database ... 140601 files and directories currently installed.)
Preparing to replace taskjuggler 2.2.0-1ubuntu1 (using taskjuggler_2.2.0-1ubuntu1_i386.deb) ...
Unpacking replacement taskjuggler ...
touch: missing file operand
Try `touch --help' for more information.
dpkg: warning - old post-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
touch: missing file operand
Try `touch --help' for more information.
dpkg: error processing taskjuggler_2.2.0-1ubuntu1_i386.deb (--unpack):
 subprocess new post-removal script returned error exit status 1
touch: missing file operand
Try `touch --help' for more information.
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 taskjuggler_2.2.0-1ubuntu1_i386.deb


---

### Post by Paintrick on 2006-05-23
anyone?

---

### Post by gunksta on 2006-05-24
I'm not in front of my machine right now and windows doesn't have a very good copy of man or info on it but try this.....I hope I don't #$&^ the syntax.

sudo dpkg purge --force-remove-reinstreq taskjuggler

--andy

---

### Post by Paintrick on 2006-05-30
Already thank you!

I gave up hope on the forum and got lost in time by having to much to do.

tonight I will try this and post the result, I already checked the syntax at work (internet) and it seems to be right.

thx again!

---

### Post by Paintrick on 2006-05-30
:(

Output:
> a@a:~$ sudo dpkg --purge --force-remove-reinstreq taskjuggler
dpkg - warning, overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 145843 files and directories currently installed.)
Removing taskjuggler ...
touch: missing file operand
Try `touch --help' for more information.
dpkg: error processing taskjuggler (--purge):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 taskjuggler
paintrick@Paintrick:~$


---

### Post by kamstrup on 2006-05-30
Have you tried "sudo apt-get install -f"?

---

### Post by Toxicity999 on 2006-05-30
That could work but doesn't that just basically run any simple commands needed to clean thinga up...? Such as removing or reinstallign things...and that doesn't seem to be working... if the deb instructions are making it use touch, and that's not going through I would assume it's a problem with the deb right?

---

### Post by dinxter on 2006-05-30
hi there, i've had a look at the post removal script for task juggler and essentially all it does is remove icons and update the icon cache for you, but its broken!. this means your can remove the script without doing any damage, try

"mv  /var/lib/dpkg/info/taskjuggler.postrm  /var/lib/dpkg/info/taskjuggler.postrm-bak"

... which backs up the post removal script, its just good practice!

"dpkg --purge taskjuggler"

... get rid of it

"gtk-update-icon-cache"

.. what the post removal script was trying to do but its knackered

---

### Post by Paintrick on 2006-05-31
Thank you so much!!!

here's what I did:

sudo mv /var/lib/dpkg/info/taskjuggler.postrm /var/lib/dpkg/info/taskjuggler.postrm-bak

it worked.

then:
sudo dpkg --purge --force-remove-reinstreq taskjuggler

it worked! (the other commando only --purge did NOT work)

then:
sudo gtk-update-icon-cache

and now it's fixed, I can update, reinstall remove and install other packages again!

thx!

---

### Post by matj654 on 2006-06-10
I had the same problem, and get rid of it with the same solution. Thank you all!!

---

### Post by Lebowski on 2006-06-17
To solve this issue, I just removed all lines about TaskJuggler in /var/lib/dpkg/status.
I know it's not really the best solution but it's mine.
After that this package does not exist anymore ;)
-- 
The Dude

---

### Post by chestnut1969 on 2006-06-23
Thankyou!!! this has been driving me MAD for days

---

### Post by stengah on 2006-06-26
YEAH thanks a bunch! Rotten package that TJ is...! ](*,)

---

### Post by medy on 2006-08-24
I just love ubuntu community =D>  

thank you 1000x times. finnaly no more errors:rolleyes:

---

### Post by eg-maverick on 2006-10-11
I also want to thank you. I ran into the same problem and the first place I ran for help was here. The Ubuntu community is very helpful. Thank you very much.:) :-D

---

### Post by eg-maverick on 2006-10-11
How do we raise the awareness that this application is badly broken (or at least the deb is) and it makes the system very unhappy? Shouldn't it be taken off the distribution?

---

