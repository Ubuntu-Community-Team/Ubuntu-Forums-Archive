---
title: "frustrated to no end"
date: 2005-11-13
forum: Desktop Environments
---

### Post by Agent66 on 2005-11-13
I'll try and keep my anger to a minimum, but seeing as this is the second time I've had to write this, even though I tried posting htis in the installation problem thread, only to have it come back saying it was in the wrong forum. SO fine.

In a nut shell - I have XP running on a Maxtor 80GB hard drive, I wanted to try out Linux on a second hard drive which is a Fujitsu 4GB I guess drive. I started with the Suse 10 which couldn't detect any network configuration, which lead me to ubuntu. The installation went fine, until it asked if I wanted the Grub loader on the master drive. Like an idiot, I said yes, hoping I would have the option of using either XP or unbuntu.

Again, things seemed fine until the load screen, which promptly froze. Again, like an idiot, I restarted my computer and this is when the real fun comes in. I can not only not access Linux, but I can't get into XP either. There is a grub error 21 that freezes at POST. I ahve tried booting XP from various XP cds, nothing. In fact, my computer is frozen on a black screen as I type this on my roommate's laptop.

And don't get me started on LInux - not only can I not get into it, but booting from the cd only takes me to installation and even then, it says nothing about deleting the grub loader from my master drive, which I'm sure is where the problem started. The only recourse is to one, completely install Linux on the master drive, which I refuse to do as I want to keep XP and at this point, seems a much more stable and user friendly OS than Linux, two - remove BOTH hard drives and test them on another computer, which I probably will have to do.

I'm frustrated and annoyed. I spent the last two days contemplating on which Linux distribution I wanted to use and even suggested to my roommate to try and use Linux. Nolw, I wish I had stuck to XP. I certainly haven't had installation problems with Windows, but with Linux I wish I hadn't taken the time. I'm sure there are those who are probably thinking I'm an idoit and that I have done somehting to my computer - if you're out there, please tell me how to fix this. If anything, I just want to go back to XP and really forget that I had thoughts of trying Linux.

I hate to sound whiny and beggy, but I really want my computer back the way it was. HELP!

---

### Post by Agent66 on 2005-11-13
okay, well I think I found the solution to at least the grub 21 error, I switched my drives so that the second drive is auto and the master is under manual/user and LBA (what does this stand for?)

And like that, ubuntu loaded.

CUrrently, I believe it is going through the final installation.

Now, the question becomes, do I do the same when I want to get into XP? Siwtch the main drive to be auto and the second as the manual/user?

Sorry for my very testy previous response. I get downright mean when I'm frustrated. ;) ANyway, I still would like some feedback though. I'm a green thumb with this and I'd like to not discover things while systemactically destroying my OS.

Thanks!

---

### Post by foolsh on 2005-11-13
i've tried to install ubuntu on a second harddrive and the same thing happened to me to fix the problem insert your xp installation cd "if your have one, some computers only have a restore partion on the harddrive, so borrow one from a friend if you can" and after xp installation starts and asks if you want to install a new copy of xp or repair the existing one of corse try to repair it.If an automatic repair fails, then choose the repair console and after loging in to your xp installation type "mbr" no quotes, this should repair the xp boot record.
as for dual booting xp and ubuntu i had to resize my xp partition on the first harddrive "ubuntu has a option to do this durin the install proccess" 5GB should be more than enough to see what ubuntu has to offer and install it there it works just fine "even by installing the grub loader to the MBR" 
best of luck to you friend

---

### Post by dbott67 on 2005-11-13
[QUOTE=Agent66]okay, well I think I found the solution to at least the grub 21 error, I switched my drives so that the second drive is auto and the master is under manual/user and LBA (what does this stand for?)[/QUOTE]
You should be able to keep the harddrives in their original configuration and still switch between operating systems.  Normally, Grub installs to the MBR of the primary disk and will have an entry for each OS (Ubuntu & XP).  I have installed Ubuntu on a number of computers with XP and kept them as dual-boots.

LBA is logical block addressing.  Full details here [http://en.wikipedia.org/wiki/Logical_block_addressing](http://en.wikipedia.org/wiki/Logical_block_addressing)

[QUOTE=Agent66]Now, the question becomes, do I do the same when I want to get into XP? Siwtch the main drive to be auto and the second as the manual/user?[/QUOTE]
You shouldn't have to.  As mentioned, if Grub is installed correctly, it will load up first and let you choose.

[QUOTE=Agent66]Sorry for my very testy previous response. I get downright mean when I'm frustrated. ;) ANyway, I still would like some feedback though. I'm a green thumb with this and I'd like to not discover things while systemactically destroying my OS.

Thanks![/QUOTE]
The best way to learn is to ask questions and also to try to answer questions.  Many of the answers to questions are already here... it's just a question of finding them.  Search, read, ask, participate.  Take a look at my signature for links to the best spots to find answers about Ubuntu.

-Dave

---

### Post by Juzz on 2005-11-13
Grub does hide the menu per default in the later install ISOs, so after your BIOS is done with all of it's stuff you should be able to press "Esc" to get the boot menu and at the bottom XP should appear ;)

---

