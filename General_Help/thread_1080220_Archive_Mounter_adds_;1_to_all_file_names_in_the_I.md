---
title: "Archive Mounter adds ;1 to all file names in the ISO"
date: 2009-02-25
forum: General Help
---

### Post by Esben Kramer on 2009-02-25
Whenever I mount an ISO file, all the files get ;1 after them. This makes it impossible to use. I can't find anything about this bug, so I thought I'd ask here. 

Thanks in advance!

---

### Post by Esben Kramer on 2009-02-25
Alternatively, I can unpack the ISO. It still extends all the file names by ;1. Is there a way I can correct it through the terminal?

---

### Post by pPrdrm on 2009-02-25
Hi Esben Kramer.
The **Archive Mounter** does exactly the same thing in my system. And nothing works. I mean I can see the files, with the "**;1**" added at the end, and that would not bother me If I could use the files mounted this way. When you say that you unpack the ISO how exactly do you do this? I use the **File Roller** to unpack the ISO files and it works perfectly. And no "**;1**" added. I really could use a graphical program to easy mount and unmount ISO files. :sad:

---

### Post by Esben Kramer on 2009-02-25
> **pPrdrm said:**
> Hi Esben Kramer.
The **Archive Mounter** does exactly the same thing in my system. And nothing works. I mean I can see the files, with the "**;1**" added at the end, and that would not bother me If I could use the files mounted this way. When you say that you unpack the ISO how exactly do you do this? I use the **File Roller** to unpack the ISO files and it works perfectly. And no "**;1**" added. I really could use a graphical program to easy mount and unmount ISO files. :sad:

I use the File Roller too, but on my system it adds the ;1 too. Weird... Has anybody heard of this?

---

### Post by holybladder on 2009-04-14
Same problem here. Any advice yet?

---

### Post by unutbu on 2009-04-14
Edit: I was mistaken, please see SteveCGElliott's response below.

PS. Thank you for the information, SteveCGElliott!

---

### Post by SteveCGElliott on 2009-04-19
I have experienced similar problems with Archive Mounter in Fedora 10.
I investigated the original CD from which I got the .iso image.

When the CD is loaded it is recognized and mounted
```
/dev/sr0 on /media/my_CD_label type udf (ro,nosuid,nodev,uhelper=hal,uid=500)

``` and the files list with their full longname glory!


If I umount and mount explicitly as iso
```
sudo mount -t iso9660 /dev/sr0 /media/DVD
```
I get
```
/dev/sr0 on /media/DVD type iso9660 (ro)
``` and the files list with **short** files names.


If I umount and mount explicitly as udf
```
sudo mount -t udf /dev/sr0 /media/DVD
```
I get
```
/dev/sr0 on /media/DVD type udf (ro)
``` and the files now list with long names.


So iso9660 & udf mounts are different for this class of media.

I think Archive Mounter fails to consider the possibility of UDF data on the medium and immediately assumes only iso data is to be used.

Can anyone point me at the location of the Archive Mounter commands that define the iso mount.  Is it possible to change or add to these to support udf?

Steve

PS: I see the same behavior if I loop mount the .iso image
```
sudo mount -t iso9660 -o loop image.iso /media/DVD
sudo mount -t udf -o loop image.iso /media/DVD
```

---

### Post by Endolith on 2009-07-14
What an annoying bug.  How much you wanna bet it's still unfixed a year from now?  [https://bugs.launchpad.net/bugs/299956](https://bugs.launchpad.net/bugs/299956)

---

### Post by derrekito on 2009-07-25
I have this issue as well, any advice?

---

### Post by Trinexx on 2009-11-07
Hate to bump an old topic, but has anybody come up with a solution for this? Using Karmic.

---

### Post by stevepoppers on 2010-02-11
Same problem here. Still no help in sight?

---

### Post by eanbowman on 2010-05-28
*bump*

This bug still exists. It makes this functionality absolutely useless.

It would be nice to fix it. Hmm...

---

### Post by klikevil on 2010-07-12
> **Endolith said:**
> What an annoying bug.  How much you wanna bet it's still unfixed a year from now?  [https://bugs.launchpad.net/bugs/299956](https://bugs.launchpad.net/bugs/299956)




Oh my god you're right it is still unfixed.

---

### Post by klikevil on 2010-07-12
> **stevepoppers said:**
> Same problem here. Still no help in sight?


sorry for the double post but dude did give a solution you just gotta mount from the terminal lol.

[http://ubuntuforums.org/showpost.php?p=7103242&postcount=7](http://ubuntuforums.org/showpost.php?p=7103242&postcount=7)

---

### Post by Endolith on 2010-07-12
> **klikevil said:**
> Oh my god you're right it is still  unfixed.

Well it was a pretty safe bet.  :D  That's the wonderful world of open source...

> **klikevil said:**
> sorry for the double post but dude did give a solution you just gotta mount from the terminal lol.

Don't confuse "solution" with "workaround".

---

### Post by Trinexx on 2010-07-22
This bug is still kicking around? I would say I'm surprised, but... honestly, I'm not even remotely surprised by this.

Wouldn't be Linux unless you had a dozen trivial bugs that annoy the living hell out of you.

---

### Post by Cadeyrn on 2010-10-31
Bah! It's Linux that's without those trivial bugs, or it gives you a way to fix them. WINDOWS is the system with trivial bugs that annoy the living hell out of you. Plus big bugs that mess you up.

Anyway, the problem's still here on Lucid. Just sayin'.

---

### Post by dcstar on 2010-11-01
> **Esben Kramer said:**
> Whenever I mount an ISO file, all the files get ;1 after them. This makes it impossible to use. I can't find anything about this bug, so I thought I'd ask here. 

Thanks in advance!

FWIW, filenames with that sort of suffix are usually "version" identifiers.

Some filesystems allow multiple versions of the same file, with the latest having ";1", then next oldest ";2" etc etc.

It would seem that the Archive Manager is incorrectly identifying the type of filesystem and appending the version suffix where it probably shouldn't.

No help at all to actually solving the problem, but possible some sort of explanation for it.

---

### Post by smeggs on 2011-04-20
I'm getting this problem with ISO's of Baldur's Gate 2. By mounting iso's made via command line using 

```
 

sudo mount -t iso9660 /iso/location /mount/location


```

the problem does not appear. It's only archive manager. I know the conversation has established that but does anyone know of a possible workaround for the software?

---

### Post by abraxas666 on 2011-10-28
problem still there...

actually I have the ;1 problem now with 10.04, with 11.04 and 11.10 Archive Manager and Archive Mounter used to work flawlessly :/


as a workaround I'm using Gmount-iso, but Archive Mounter was (on 11.04) far more integrated
:(

---

### Post by mc4man on 2011-10-28
If you wish to read on this - move down towards the middle to end
[https://bugs.launchpad.net/ubuntu/+source/libarchive/+bug/299956](https://bugs.launchpad.net/ubuntu/+source/libarchive/+bug/299956)

---

### Post by abraxas666 on 2011-10-28
thank you mc4man, I found the suggestion for Gmount-iso there but I missed the link...


Unfortunately I have to stick with the LTS and live with it

---

