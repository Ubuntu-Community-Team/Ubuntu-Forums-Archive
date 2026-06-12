---
title: "Grub won't start at startup. &lt;help&gt;"
date: 2004-12-23
forum: Desktop Environments
---

### Post by uggeli on 2004-12-23
Sorry if I post this thread in wrong place but didn't know where else to put this.

Today I made stupid mistake AGAIN! :( I was reading that swap partition should be formatted as linux-swap filesystem but that wasn't available whe I installed my ubuntu so I thought ext3 will do the same if it's mountpoint is /swap. 

Well anyway after I read that it should be formatted as linux-swap I decided to give it a try so my swap partition isn't there without using. I downloaded qtparted (or what it was) via synaptic and then formatted swap partition to linux-swap and there was some error when I did it, I thought it won't be so big deal and I moved on and when restarting my computer grub won't start and so I can't choose eather ubuntu or windows xp. How can I fix this problem? I'm writing this in ubuntu live-cd.

Errormessage was:

GRUB loading, please wait...
Error 15
_


It seems that I have to learn all to the hard way.

Edit. Sorry I was too blind while 'in shock' just noticed that this area is for gnome etc.. Well Maybe moderators will move this to right place and sorry again.. :/

---

### Post by feneks on 2004-12-24
[QUOTE=uggeli] Errormessage was:

GRUB loading, please wait...
Error 15 [/QUOTE]




Error 15 means that the  partition ist defined in a wrong way or grub doesn't exist anymore.

I'm afraid first one appeals to you. I guess following: When you  played with your partitions you -ehm- "killed" the partition table! So GRUB has no usable partitioning anymore and hangs: "Error 15 file not found"   
[QUOTE=uggeli] It seems that I have to learn all to the hard way.[/QUOTE]
YES YOU DO!

I guess you have no backup of partitioning? 8-[

---

### Post by uggeli on 2004-12-24
Well I reinstalled my system and all went well as far until I updated it to hoary again. But that's another story, thistime I didn't do anything stupid unless you count upgrading to hoary that. Will continue in old thread if I found it.

And it might be that linux is not for me but I'm not newbie in windows allthought not guru eather but closer that than newbie and I really want to learn linux allso, it just seems to take some time..

Edit: back in business, just installed newest gdm and after that followed what [Matt](http://ubuntuforums.org/showthread.php?t=8344) has told that he's done. 

Thanks for the answers and I'm trying now learn without hassle.. :)

---

