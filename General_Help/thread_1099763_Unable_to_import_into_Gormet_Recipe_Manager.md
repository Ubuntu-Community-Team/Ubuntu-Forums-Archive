---
title: "Unable to import into Gormet Recipe Manager"
date: 2009-03-18
forum: General Help
---

### Post by 2hot6ft2 on 2009-03-18
I am having a problem when trying to import recipe files into Gourmet Recipe Manager (GRM for short) like the title says. When I open GRM and click on File then Import file it opens a browse window (shown in the attached pic). This is where the problem is, it wont let me go anywhere from there or even select a file at that point. I have moved the recipes I want to import into my home folder so they are right there but I can't get them to even be selectable.

Double clicking on them just closes the browse window and doesn't import them. The recipes are valid and did import on the desktop pc, this is my laptop.

I had this kind of issue last year when I tried putting home on its own partition and ended up re-installing with everything on one partition which solved the problem. About 2 months ago I put home on its own partition again and everything has worked fine until now. Old home is gone now.

So the question is how to fix this so it will work properly?

Now for the system info:
Ubuntu Ultimate Edition 2.0 32 bit same as Ubuntu 8.10 Intrepid Ibex 32 bit.
HP G60-125NR laptop, 3 GB RAM, 250 GB HD, AMD Turion X2, NVIDIA GO 8200M

Here is my fdisk -l
> Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfd03d783

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4462    35840983+   7  HPFS/NTFS
/dev/sda2            4463       30401   208355017+   5  Extended
/dev/sda5            4463        8109    29294496   83  Linux
/dev/sda6            8110       27205   153388588+   7  HPFS/NTFS
/dev/sda7           30153       30401     2000061   82  Linux swap / Solaris
/dev/sda8           28104       30152    16458561   83  Linux
/dev/sda9           27206       28103     7213153+  83  Linux

Partitions:
/dev/sda5 = ubuntu
/dev/sda8 = ubuntu home
/dev/sda7 = linux swap
/dev/sda9 = nothing right now it's for bt4 later

Gparted pic attached for a graphical view.

Strange, but it let me browse to the desktop to upload the pics.
I have even tried starting GRM using gksu with no change.

I have tried finding the solution using the search with no luck, must not be using the right search terms since I know I've seen this type of issue before.

Any help would be appreciated so thanks in advance.

---

### Post by 2hot6ft2 on 2009-03-18
bump...doesn't anyone know how to fix this?

---

### Post by 2hot6ft2 on 2009-03-23
bump. still looking for how to fix this.:confused:

---

### Post by balloons on 2009-04-08
I had trouble until I downloaded the new version from the gourmet website .14.7, and deleted my ~/.gourmet file. Then I started the program. It worked wonderfully.

---

### Post by 2hot6ft2 on 2009-04-08
Thanks guitara. That did the trick. I still can't browse to any but now I can import them from my home folder.

---

### Post by smitty_srs on 2009-04-25
> **guitara said:**
> I had trouble until I downloaded the new version from the gourmet website .14.7, and deleted my ~/.gourmet file. Then I started the program. It worked wonderfully.

I'm having the same issue using .14.7.  Where is the gourmet file you talked about located?  Thanks.

---

### Post by smitty_srs on 2009-04-25
> **smitty_srs said:**
> I'm having the same issue using .14.7.  Where is the gourmet file you talked about located?  Thanks.

I figured it out.  Apparently, the version of Python (2.6 ?) that gets installed with xubuntu 9.04 doesn't work to well with GRM .14.7.  This fixed it for me:

```
sudo apt-get install python2.5

python2.5 /usr/bin/gourmet
```

I give credit to Arkarin on SourceForge. [[COLOR="RoyalBlue"]LINK[/COLOR]]("http://sourceforge.net/forum/forum.php?thread_id=3094249&forum_id=371768")

---

