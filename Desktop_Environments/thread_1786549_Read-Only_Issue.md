---
title: "Read-Only Issue"
date: 2011-06-19
forum: Desktop Environments
---

### Post by miserly-martyred on 2011-06-19
I have had some external access problems with an ubuntu install of mine.  After some previous adjustments, upon trying to boot my system I have issues that say I can't boot b/c the filesystem is read-only.

I have already adjusted the digital contents.

I have already edited the " ro " setting switch in /etc/fstab.


Now I'm rather at a loss ...


Anybody know how else to completely remove a "read-only" assignment of an entire ext3 filesystem?

---

### Post by wildmanne39 on 2011-06-20
> **miserly-martyred said:**
> I have had some external access problems with an ubuntu install of mine.  After some previous adjustments, upon trying to boot my system I have issues that say I can't boot b/c the filesystem is read-only.

I have already adjusted the digital contents.

I have already edited the " ro " setting switch in /etc/fstab.


Now I'm rather at a loss ...


Anybody know how else to completely remove a "read-only" assignment of an entire ext3 filesystem?
Hi, you should be able to have write access with this command.
```
sudo chown -R username:username /media/file

```/media/file is the path to your file or drive and the name of the file.

---

### Post by miserly-martyred on 2011-06-20
I see how that would help.  But my entire Ubuntu OS drive is inaccessible. I am accessing the drive, externally, from another OS install.  I don't see how I can do a "chown" command if I cannot boot anything to start out at first.

My Ubuntu install is by itself on it's own HDD and I am using something else to attempt to make that drive "non read-only".  I attempt to boot that Ubuntu install and it tells me that I have some weird errors that I narrowed down to solving with "update-initramfs -c -k all" ... but when I do that, I am denied because of the drive being "read-only".

The entire Ubuntu install only works in "maintenance mode", zero GUI is available ...

---

### Post by nzjethro on 2011-06-20
Can you boot from a Live CD, then chroot to your read-only drive and run wildmanne's suggestion?

---

### Post by miserly-martyred on 2011-06-21
from terminal:

I tried -- { sudo chown -R username:username /dev/sda1 }


It was noted that:  "read error, no such file or directory"


...ugh ... it's bush I say, lol ...


do I need to " cd " my command to run from somewhere very specific?

---

### Post by wildmanne39 on 2011-06-21
> **miserly-martyred said:**
> from terminal:

I tried -- { sudo chown -R username:username /dev/sda1 }


It was noted that:  "read error, no such file or directory"


...ugh ... it's bush I say, lol ...


do I need to " cd " my command to run from somewhere very specific?
Hi, you have to chroot into your partition from the live cd, I could not find a link for chroot like I wanted too, but I think this should get your partition mounted.
```
sudo mount /dev/sdXX /mnt  (example 'sudo mount /dev/sda11 /mnt' ,don't miss the spaces.)
```You have to use your partitions information in place of /dev/sdxx. Then enter these commands
```
sudo mount --bind /dev /mnt/dev
```
```
sudo mount --bind /proc /mnt/proc 
```
```
sudo mount --bind /sys /mnt/sys
``` Then you can enter those commands from my last post, if you do not know the partition you need to mount for sure post the information from this script so we can see where everything is located:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans

Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read. And we can look at tell you what partition you need. I found this link with a little better instructions for chroot then I gave you.
[http://ubuntuforums.org/showthread.php?t=1156240](http://ubuntuforums.org/showthread.php?t=1156240)

---

### Post by miserly-martyred on 2011-06-22
so I tried the list of code commands you just gave

they have all succeeded

and I am now inside of the Live CD like you suggested with all of those commands entered.

Just that now ... you suggested I run this:

```
sudo chown -R username:username /media/file
```

in that part, I am confused as to this:

```
... /media/file
```

there at the end, the device I am binding to /mnt, is /dev/sdb1 ... you said to make the end of that code equal out to either the drive or file that I am looking for to change the permissions on it.

I don't know whether to put this:

```
sudo chown -R username:username /dev/sdb1
```

or what I should put ... b/c I need the entire drive to be adjusted.

I would also like to know how to safely remove/unmount/unbind this drive/filesystem when done.  (other than just, right click "unmount", except if that's all)

---

### Post by miserly-martyred on 2011-06-22
In the post I made, right above this ... I did indeed look up that location.

Just to avoid confusion, I properly determined this with a full scan from gParted.

I was wrong before, and for sure, I personally recognize that the partition I am after really is as follows:

```
/dev/sdb1
```


Hope the new fact info helps, since I was wrong the first time :)

---

### Post by nzjethro on 2011-06-22
Yes, that will change the ownership of the whole drive. I imagine that's what you are after?

To unmount safely, use

```
sudo umount /drives/you/mounted
```

Note, that is ***umount*** not u***n***mount.

---

### Post by miserly-martyred on 2011-06-22
so what with the doom and gloom of school, I have to head to bed in a bit.

but I tried exactly what you suggested:

```
sudo chown -R username:username /dev/sdb1
```

and it told me that:

```
I am using an invalid user, or no such user found.
```


also, 

```
sudo umount /dev/sdb1
```

yields this:

```
umount: /mnt: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
```

even after multiple attempts and changes...

:( :( :(

---

### Post by nzjethro on 2011-06-22
Doom and gloom of school - tell me about it. I have a microeconomics final on Friday!

> I am using an invalid user, or no such user found.

This may be a silly question, but did you substitute your username for "username" in the above commands? Coming up with "no such user" implies that you are, for whatever reason, using a wrong username. Double-check to see whether everything is spelled right.

As for this:
> umount: /mnt: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))

This means you have processes running that are accessing sdb1.

Try running
```
lsof | grep /mnt
```

This will give you a list of processes using /mnt (=sdb1), then run

```
sudo killall *<processes>*
```

---

### Post by miserly-martyred on 2011-06-23
let's say my username was archangelmichael


I did exactly this:

```
sudo chown -R archangelmichael:archangelmichael /dev/sdb1
```


so .... 


My guess is some weird conflict I have created by binding those directories + / or mounting the drive to " /mnt " ... but then having me tell it to mount " /dev/sdb1 " in the chain of commands ...

Does the binding make it different when I am thinking I should do this?:

```
sudo chown -R archangelmichael:archangelmichael " /mnt/ ... "
```

---

### Post by miserly-martyred on 2011-06-23
@ [nzjethro]("http://ubuntuforums.org/member.php?u=1306925")


By the way, many thanks for your assistance + expertise with this issue of mine.

Very helpful even while your stuck amidst difficult academics :-|

---

### Post by nzjethro on 2011-06-23
> **miserly-martyred said:**
> 

Does the binding make it different when I am thinking I should do this?:

```
sudo chown -R archangelmichael:archangelmichael " /mnt/ ... "
```

D'oh! That was a rookie mistake on my part. I'd definitely try unmounting the device you'd mounted (i.e. /mnt/). Sheesh, it must have been late and study time for me not to pick that up. ;)

And no worries, this makes a nice study break, and gives me something to take my mind off it all for 5 minutes. I've been helped along a lot on these forums, so it's nice to be able to help other people out too, add to the Ubuntu community. :D

---

### Post by wildmanne39 on 2011-06-23
> **miserly-martyred said:**
> @ [nzjethro]("http://ubuntuforums.org/member.php?u=1306925")


By the way, many thanks for your assistance + expertise with this issue of mine.

Very helpful even while your stuck amidst difficult academics :-|Hi, in my post with the chroot command I gave you a link I found it about an hour after I posted I could not find it the one I was looking for and it has good instructions, also tells how to unmount the partitions that is why I did not include it in the instructions. the /media/file is your drive, and it will be in this syntax not as sda or sdb. Open file manager on the left side click to mount the drive you are wanting to change permission too, then hover your mouse over the drive on the left of the file manager and it will show where it is mounted, it will be /media/whatever your file name is.That is how you have to enter the drive information.

---

### Post by miserly-martyred on 2011-06-23
@ [wildmanne39]("http://ubuntuforums.org/member.php?u=508533")

thanks to you as well, really ... this stuff is rather beyond me.

I'm def gonna check out the link and make sure that things are correctly mounted/unmounted before running all these commands ...

---

### Post by miserly-martyred on 2011-06-23
So I have tried the command about ' chroot '  -- with all the user errors I am getting and:

I substituted ' /mnt ' ... instead of using ' /dev/sdb1 '

It still denied me because of a ' no such user ' error.


Then I tried the official ubuntu.com guide to managing one's "encrypted private directory"

there's a whole document that I read about accessing my ' .Private ' and trying to manually recover the files.

I used the shortcut item from the ubuntu LiveCD that said to run this:

```
/usr/bin/ecryptfs-mount-private
```... that failed by saying this:

```
"error - encrypted private directory not setup properly"
```I can even run the command in the official website guide about all of the ' .ecryptfs '  type stuff that accesses my system to recover my mount pass number or whatever ( I say 'number' cuz the code to recover is not my login password, it's the alphanumeric weird phrase thing)

doing the above thing I just now mentioned I get this:

```
" ecryptfs error [-5] "

check system log for more details.
```I don't even know how the hell to find that log, lol...

this chaos seems endless and the solution seems far away.

Is there a way to force the OS to let me "command line-based" ... do updates and then a txt-based distro upgrade to use new sys files and correct the problem?

the issue with that, that I see is the Ubuntu install I have constantly telling me that it has

```
general error mounting filesystems
```I can't get this non-read only to save my life, ugh


Of note as well ... after binding and mounting, etc. of my /dev/sdb1 partition, when I exited the LiveCD it seems as though there was no cleanly performed umount, even though I went through all the commands (yes umount, not unmount).  Is there a remedy for an unclean umount, or is it not that terrible?

---

