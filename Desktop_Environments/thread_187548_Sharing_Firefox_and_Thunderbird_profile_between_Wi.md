---
title: "Sharing Firefox and Thunderbird profile between Windows and Linux"
date: 2006-06-03
forum: Desktop Environments
---

### Post by srwilson on 2006-06-03
I am starting to get into Linux and I would really like to actually share my Firefox and Thunderbird profiles between both Windows and Linux in my dual boot system.  It's such a pain to maintain two installs of each especially with the 15000 extensions I have.

So far I have been able to store the profiles on a Fat32 partition and get it to work in Windows.  But when I tried to edit the profiles.ini file in Linux (as I did in Windows) to make the profile point to the shared one, it gave me an error when I tried to start the programs.  Something about the program already running but being nonresponsive.  I also saw you can make the profile point to a different location using symbolic links, but it seems that Nautilus won't let me make one into the FAT32 partition.  Any ideas here?

Also, I have done some googling and found that another major obstacle is that the paths in the prefs.js file are absolute and will have to be different for each OS. ](*,) 

Has anybody had any success with this?  Is it even remotely possible?  Or should I just give up now.  :confused:

---

### Post by patrickfromspain on 2006-06-03
I think it's not possible... I'm nearly sure that the way thunderbird and firefox manage profiles is quit different in windows and linux.

Anyway... 15000 extensions? You really use 15000 extensions? Hard to believe ;)

---

### Post by Crowhurst on 2006-06-05
I believe it is possible, i have found some sites which discuss it:

[http://www.ces.clemson.edu/linux/firefox-thunderbird.shtml](http://www.ces.clemson.edu/linux/firefox-thunderbird.shtml)

I have followed their instructions for sharing tb, and have done the same as you - have a fat32 partition for my mails. Windows works fine, Ubuntu TB now sees all the directories, but does not see the mail inside.

Still looking for answers. Will also want to follow the rest of the clemson instructions when i get time to share bookmarks, etc.

It would be great if this were simpler, i think it would help many people maintain dual boot.

Hopefully it will get on the development path for TB someday.

---

### Post by MetalMusicAddict on 2006-06-05
Ive seen things to share bookmarks but Im still working it out. Im trying to share mine over a network so 3 PCs share the same bookmarks. I think Im having write access issues.

---

### Post by DeadEyes on 2006-06-05
It is possible, I share thunderbird between windows and linux.
Try either of these:

1.
Go to .mozilla-thunderbird/
delete the <randomnumber>.default then create a symbolic link to your windows created .default in my case its n8vm9c0p.default finally edit the .mozilla-thunderbird/profile.ini (the linux one)
Path=n8vm9c0p.default

2.
Launch thunderbird with the -profilemanager switch
mozilla-thunderbird -profilemanager
Create a profile and when you choose the folder select the existing windows one

I haven't tried firefox but I would imagine its pretty much the same. The only problem is that some extensions don't play nice on different OSs

When I was setting this up I found a great tutorial, If I can find it again I'll post the link here.

Edit:
[http://www.plaintivemewling.com/?p=20](http://www.plaintivemewling.com/?p=20)

---

### Post by sbooth on 2006-06-07
I've got it working... and will rack my brains to remember how!  I have XP on a laptop in the house, Ubuntu on a desktop in the shed, my Thunderbird profile stored on a samba-shared network drive and accessed by both... heaven knows how I did it but it seems to work.  I've just installed Ubuntu on my laptop (last night) and it's running like a dream... so now I'm faced with sorting Thunderbird on my laptop Ubuntu install... and I'm going to tackle sharing the Firefox profile too.  Ho hum - I suspect I'll have many happy hours of 'losing' everything and finding it again.

I wish I could remember how I did it - because keeping profiles on a server (assuming one *has* a server at home!) seems to be a fabulous way of doing things... I just have to sort out the installations on each PC I use to access the same place.

I'm trying to work out how I did it (so my husband can sort his setup out too) - if I do, I'll post it here!

---

### Post by lolcese on 2006-06-19
I need to do it in a different way, I have all my Thunderbird emails in the linux partition, and I want  to use them in Windows.
Any ideas?
Thank you

---

### Post by marciovinicius on 2006-07-07
> **lolcese said:**
> I need to do it in a different way, I have all my Thunderbird emails in the Linux partition, and I want  to use them in Windows.
Any ideas?
Thank you
I think you gonna need some like this [http://easylinux.info/uploads/explore2fs-1.07.zip](http://easylinux.info/uploads/explore2fs-1.07.zip) or this [http://www.fs-driver.org/index.html](http://www.fs-driver.org/index.html)

Besides you can move your entire profile to a FAT32 Partition...

I think the better and easiest way to share profiles between Windows and Linux is the way that DeadEyes explained (except that the first step can be done via Profile Manager) but...

It doesn't work in my office... My profiles (Firefox and Thunderbird) are in a server (Linux CentOS) and I don't know how to point profile paths in a network... How can I do it? the network simply doesn't appear within Profile Manager...

---

### Post by bazz on 2006-07-07
Not sure if this may help ya. I'v been doing this for a while with mail. I also do it over a network from my network server. Just need to mount the network share and have the correct right.
For example I have a share on my server with my wife&#8217;s email and my email in a folder called email. In that folder is a folder with her profile, and a folder with my profile. The email folder is shared with read rights, and the two profile folders we have full rights (that way we can download and delete email in thunderbird.) 
So at boot I have my linux machines mount the mail share from the server to /mnt/email of my local machine. I just map the share in windows to do the same. So at this point it doesn&#8217;t matter if I&#8217;m using window or Linux, I can just run thunderbird and get my mail and everything will be as if I always use one machine. The other cool thing is I have 8 computers at my house each one set up to do this, so I can get all my mail from any computer.


[http://forum.linspire.com/viewtopic.php?p=368053&highlight=#368053](http://forum.linspire.com/viewtopic.php?p=368053&highlight=#368053)

As for the "program already running but being nonresponsive" I have the same thing happen sometimes. The fix I have to do is manually go to the profile folder open it to make it active, the restart thunderbird.

As for bookmarks you can use the foxmarks extension for firefox.

---

### Post by mondi0924 on 2006-07-07
I have a setup right now where I use one profile for thunderbird , both in windows and linux.

Heres what I did,

1. setup ext2fs in windows , this way you can view the ext3 partition which is your linux partition. - I forgot the exact link to the app . but you can always google for it.

2. create a new profile in winxp thunderbird that points to my linux thunderbird profile.

* If you have an existing setup you can just copy the contents of the old profile into the new one .

* This may or may not work with firefox but I have yet to try it. don't have time right now to dabble with my comp.

* windows only extensions will not work naturally.

* There might be some issues with some messages not correctly showing up if whether they were already read or not. 

Hope it helps

---

### Post by lolcese on 2006-07-10
It worked perfectly, thanks !!!!!

---

### Post by marciovinicius on 2006-07-10
> **bazz said:**
> 
So at boot I have my linux machines mount the mail share from the server to /mnt/email of my local machine. 
Ok, but let me make a stupid question: How can I mount a network folder? (I think right this is my problem... I'm not so accomplished  in Linux.)
Thank you!

---

### Post by bazz on 2006-07-11
> **marciovinicius said:**
> Ok, but let me make a stupid question: How can I mount a network folder? (I think right this is my problem... I'm not so accomplished  in Linux.)
Thank you!

I was using linspire, and used the network share manager. That’s how I was doing it. I just stared using Kubuntu, and looking into a efficient way of doing that. I could just use smb4k, but I don’t like that idea.

Sorry it took a while to get back to you. New to the forum and just getting use to it.

When I find a good way of doing it, I will post. I think Im gonna end up using mount in some way or form.

---

### Post by shimrah on 2006-08-28
You're a good man, bazz. A good man.

I've already set up my thunderbird to share a profile between XP and Ubuntu... but for some reason my firefox bookmarks weren't saving in Ubuntu (they's show up but, on close and restart, anything I'd added would be gone).

Foxmarks is great!

Cheers,
shimrah


> **bazz said:**
> Not sure if this may help ya. I'v been doing this for a while with mail. I also do it over a network from my network server. Just need to mount the network share and have the correct right.
For example I have a share on my server with my wife’s email and my email in a folder called email. In that folder is a folder with her profile, and a folder with my profile. The email folder is shared with read rights, and the two profile folders we have full rights (that way we can download and delete email in thunderbird.) 
So at boot I have my linux machines mount the mail share from the server to /mnt/email of my local machine. I just map the share in windows to do the same. So at this point it doesn’t matter if I’m using window or Linux, I can just run thunderbird and get my mail and everything will be as if I always use one machine. The other cool thing is I have 8 computers at my house each one set up to do this, so I can get all my mail from any computer.


[http://forum.linspire.com/viewtopic.php?p=368053&highlight=#368053](http://forum.linspire.com/viewtopic.php?p=368053&highlight=#368053)

As for the "program already running but being nonresponsive" I have the same thing happen sometimes. The fix I have to do is manually go to the profile folder open it to make it active, the restart thunderbird.

As for bookmarks you can use the foxmarks extension for firefox.

---

### Post by flyvholm on 2006-09-01
Regarding the "Program running, but nonresponsive" issue, here's a link to some info about what can cause this:

[http://kb.mozillazine.org/Profile_in_use](http://kb.mozillazine.org/Profile_in_use)

I ran into this because of a permission problem due to the way my FAT32 partition was mounted. In /etc/fstab I was using default mount options:

/dev/hda4 /shared vfat defaults 0 0
(FF and TB won't launch)

I changed the mount options to the following:

/dev/hda4 /shared vfat rw,user,users,auto,umask=0000 0 0

Rebooted and now FF and TB starts fine using the shared profile.

BTW, here's a link to a how-to posted here in ubuntu forums:
[http://www.ubuntuforums.org/showthread.php?t=203524](http://www.ubuntuforums.org/showthread.php?t=203524)

---

### Post by Cisto on 2006-10-25
I followed another way to share Thunderbird mails beetween Windows and Linux; it is very easy, but you need to have write permissions on the Windows filesystem (vfat or ntfs-3g):

First of all, install Thunderbird via apt-get :D , then:

```
cd /home/username/.mozilla-thunderbird/
```

```
ln -s /media/windows/Documents\ and\ Settings/Username/Dati\ applicazioni/Thunderbird/Profiles/xxxxxxxx.default 
```
where xxxxxxxxxx.default is the default thunderbird profile (i'm using an Italian windows xp, i think "Dati applicazioni" should be "Applications Data" ; /media/windows is my ntfs-3g mount point)

The last thing to do is to edit the profiles.ini file in the /home/username/.mozilla-thunderbird/ directory so that the default profile is the xxxxxxxxx.default symbolic link.

It works perfectly and it's easyer than copying the whole profile and editing the pref.js file changing all the paths!

(Sorry for my poor English).

---

### Post by Cuppa-Chino on 2006-11-07
Hi, managed to work it out for myself - I used ext2fs for windows and made an ext3 parition that I mounted as home in linux and as D: in windows, then I switched all my application data etc to that drive so that windows and linux automatically treat it as the data drive - BUT there is one exception that is not working and I cannot find any clues how sort this out:

* I have set my Thunderbird to download the messages but also leave them on the server until I move or delete them (see picture)

Now when I change operating system both Windows Thunderbird and Linux Thunderbird will end up downloading ALL messages that the respective client had not downloaded - for instance I have been using only Linux for several days and I last used Thunderbird in Windows last Saturday, if I now go into Windows and start Thunderbird it will download all messages anew received since Saturday (despite me having read them in Linux)

How can I fix this? I do not know what the two clients are not sharing at the moment? is there away to reset pref.js (which comes from a windows install) could that be the problem?

---

### Post by bazz on 2007-11-01
I know its been a while, but I have installed Freespires sharemanager on Kubuntu Gusty, and it works awesome! So if anyone wants to give it a go, I installed the deb from here [http://apt2.freespire.org/CNRUbuntu-20071013_01:48:56/pool/main/s/sharemanager/](http://apt2.freespire.org/CNRUbuntu-20071013_01:48:56/pool/main/s/sharemanager/)
Very handy tool!!

---

### Post by oliwally on 2007-11-01
> **flyvholm said:**
> Regarding the "Program running, but nonresponsive" issue, here's a link to some info about what can cause this:

[http://kb.mozillazine.org/Profile_in_use](http://kb.mozillazine.org/Profile_in_use)

I ran into this because of a permission problem due to the way my FAT32 partition was mounted. In /etc/fstab I was using default mount options:

/dev/hda4 /shared vfat defaults 0 0
(FF and TB won't launch)

I changed the mount options to the following:

/dev/hda4 /shared vfat rw,user,users,auto,umask=0000 0 0

Rebooted and now FF and TB starts fine using the shared profile.

BTW, here's a link to a how-to posted here in ubuntu forums:
[http://www.ubuntuforums.org/showthread.php?t=203524](http://www.ubuntuforums.org/showthread.php?t=203524)

You little ripper!! This worked for me. I've been using this setup for about two years, but when upgrading to Kubuntu Gutsy (fresh install) recently, I used the System Settings - Advanced - Disk & Filesystem tool to automatically mount my vfat partition. File sharing was then fine but TB would not launch. I changed the mount options in etc/fstab as suggested, and BINGO! Thanks for posting your solution flyvholm.

---

