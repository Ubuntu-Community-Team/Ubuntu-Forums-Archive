---
title: "Thunderbird Limitations?"
date: 2012-05-06
forum: Desktop Environments
---

### Post by CWM84 on 2012-05-06
[SIZE=3]Hi,

I was just reading about thunderbird and its limitations......

it states:

[/SIZE]**[SIZE=3]Folders and messages[/SIZE]**

 [SIZE=3]IMAP folders have no effective size limit. (Thunderbird 3.1 added a  64-bit offset to the .msf file allowing folders larger than 4GB, if the  file system permits that large a file. [[2]]("http://forums.mozillazine.org/viewtopic.php?p=11291447#p11291447") [[3]]("https://bugzilla.mozilla.org/show_bug.cgi?id=532323"))  However, using very large folders (3GB, 4GB, etc) is not recommended as  compacting will take a long time, unless you have very fast disk.  [/SIZE]
[SIZE=3]Local Folders, including pop accounts, are limited to 4GB, until version 12.  Thunderbird 12 adds support [[4]]("https://bugzilla.mozilla.org/show_bug.cgi?id=402392") for a "[pluggable mail store]("https://wiki.mozilla.org/Thunderbird:Pluggable_Mail_Stores")", and also removes the 4GB local folder size. [/SIZE]
[SIZE=3]Folders are stored as [mbox format]("http://en.wikipedia.org/wiki/Mbox") files in a [profile folder]("http://kb.mozillazine.org/Profile_folder")  on your boot disk by default. So normally you are limited to the amount  of free space on your boot disk. However, you can use the [Profile Manager]("http://kb.mozillazine.org/Profile_Manager") to create a profile wherever you want (including on file shares). It's also possible to  [ store folders outside of the profile]("http://kb.mozillazine.org/Moving_your_mail_storage_location_%28Thunderbird%29"),  on any drive, in any directory.  Pluggable storage previously mentioned  allows for the possibility of storage formats other then Berkley mbox,  and potentially removing the performance impact of compacting folders.  However no storage types other the mbox currently exist. [/SIZE]
[SIZE=3]Desktop search programs such as Google Desktop , Copernic or X1  may not be able to index the contents of a 4GB folder. X1 supposedly  runs into problems at 1GB. [/SIZE]
[SIZE=3]There is no known limit on the number of folders. 
[/SIZE]
[SIZE=3]
[/SIZE]
[SIZE=3]
[/SIZE]
[SIZE=3]so does that mean when my folder his 4 gigs? I have to create a new folder?[/SIZE]
[SIZE=3]
[/SIZE]
[SIZE=3]I am using thunderbird 12 on Xubuntu 12.04.... I use POP 3......
[/SIZE]
[SIZE=3]
[/SIZE]
[SIZE=3]I really dont understand the limitations...[/SIZE]
[SIZE=3]
[/SIZE]
[SIZE=3]Thanks,[/SIZE]
[SIZE=3]Christopher
[/SIZE]

---

### Post by Paddy Landau on 2012-05-07
It means that on Thunderbird 11 and earlier, when you hit 4Gb you have a problem. But from Thunderbird 12, you are OK.

I guess Thunderbird needed a bigger size for (among others) people using IMAP with GMail, which allows 7Gb.

---

### Post by CWM84 on 2012-05-08
> **Paddy Landau said:**
> It means that on Thunderbird 11 and earlier, when you hit 4Gb you have a problem. But from Thunderbird 12, you are OK.
 
I guess Thunderbird needed a bigger size for (among others) people using IMAP with GMail, which allows 7Gb.
 
Ahh thanks!

---

### Post by VanillaMozilla on 2012-05-08
You are "OK", but that's a vague term.  I would really suggest archiving some of that.  It's hard to go wrong with housekeeping.  Large files like that gets to be rather risky, and maybe slow and resource-intensive as well.  I just separate out e-mails by date and move them to a "local folder".  Maybe take a year at a time, for example.

---

### Post by CWM84 on 2012-05-08
> **VanillaMozilla said:**
> You are "OK", but that's a vague term.  I would really suggest archiving some of that.  It's hard to go wrong with housekeeping.  Large files like that gets to be rather risky, and maybe slow and resource-intensive as well.  I just separate out e-mails by date and move them to a "local folder".  Maybe take a year at a time, for example.

like

JAN 2012

FEB 2012

MARCH 2012

do do you do yours like

2012
|
|---- January
|
|---- Feb

so one whole year is in its own folder... 

the 1st example is seperate folders.. 

the 2nd one is a 2012 folder.. with Month folders nested under the 2012 folder.

---

### Post by Paddy Landau on 2012-05-08
> **VanillaMozilla said:**
>  I would really suggest archiving some of that.
Is that really relevant for IMAP folders? If it goes wrong, you can simply delete your Thunderbird account and recreate it.

I fully understand the need for backups for POP files, of course.

---

### Post by VanillaMozilla on 2012-05-08
Good point.  I don't know.  I'd have to think about that.  I forget how that works.  Does it mirror the remote files?

I don't know, but if you have to store or synchronize any large files like that, I'll bet housekeeping still might help.  And I know from experience it can be a scramble if you suddenly exceed storage limits.  I could be wrong, but it's something to think about.

---

### Post by Paddy Landau on 2012-05-08
> **VanillaMozilla said:**
> I forget how that works.  Does it mirror the remote files?
Yes, it does. You have the option to download a copy to your computer (for speedy access); or to download only when reading the message (to reduce local disk space).

> **VanillaMozilla said:**
> ... if you have to store or synchronize any large files like that, I'll bet housekeeping still might help.
Absolutely. You can compress the files regularly using Thunderbird's built-in facility, and you can install the [ThunderPlunger plugin]("https://addons.mozilla.org/thunderbird/addon/thunderplunger/") to compress the database occasionally.

---

### Post by CWM84 on 2012-05-08
> **Paddy Landau said:**
> Is that really relevant for IMAP folders? If it goes wrong, you can simply delete your Thunderbird account and recreate it.

I fully understand the need for backups for POP files, of course.

I use POP 3... Unfortunately.....

---

### Post by Paddy Landau on 2012-05-08
> **CWM84 said:**
> I use POP 3... Unfortunately.....
Well, back up daily (as I do); compress your folders once a week; and use ThunderPlunger to compress your database every fortnight or so.

---

### Post by CWM84 on 2012-05-08
> **Paddy Landau said:**
> Well, back up daily (as I do); compress your folders once a week; and use ThunderPlunger to compress your database every fortnight or so.

I am still fighting myself on what to use.. Webmail or Thunderbird... when I was on windows we used MSN PREMIUM and its software for windows, anyways better an AOL but they tell me if I quit paying the 9.95 that our accounts all 9 of them will go down to HOTMAIL free accounts which are 5 gigs and thats all they get

I am like I read all over the internet Hotmail has EVER GROWING STORAGE.. which means when I hit that 5 gigs, I will get more storage.. OOO but sir if you keep paying you have unlimited storage and no ads...  And thats not true.. 5 gigs is ALL you get

I dont trust GMAIL for the fact of the missing emails scam...

UGH I have till the 10th to cancel... before they bill me.. Frickin Microsoft....

Thanks for the help!  :guitar:

---

### Post by Paddy Landau on 2012-05-09
> **CWM84 said:**
> I dont trust GMAIL for the fact of the missing emails scam...
I have been using GMail for a couple of years; one account for my emails, and two for non-profit volunteer organisations that I help (and one of them has two other GMail accounts). My father and stepmother have been using GMail for some time. A friend has used GMail's advanced features for several years.

I have never heard of this "missing emails scam", nor have any of us had any problems whatsoever with it.

That's only my experience, of course, but I've been completely satisfied with GMail. I use IMAP with Thunderbird, because I prefer it, but when I'm away from my computer I use GMail's interface, which works fine.

---

### Post by CWM84 on 2012-05-09
> **Paddy Landau said:**
> I have been using GMail for a couple of years; one account for my emails, and two for non-profit volunteer organisations that I help (and one of them has two other GMail accounts). My father and stepmother have been using GMail for some time. A friend has used GMail's advanced features for several years.

I have never heard of this "missing emails scam", nor have any of us had any problems whatsoever with it.

That's only my experience, of course, but I've been completely satisfied with GMail. I use IMAP with Thunderbird, because I prefer it, but when I'm away from my computer I use GMail's interface, which works fine.

Odd.. I kept having contacts coming up missing randomly... odd... I might have to give it a try if Microsoft is going to pull this with the whole putting us back down to nothing and throwing the ads back on , forcing us to stay....  Thanks again!

---

