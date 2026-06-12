---
title: "Ram not recognized"
date: 2008-12-22
forum: General Help
---

### Post by jaynewstrom on 2008-12-22
Hello,
Here is the deal,
I have windows vista, and installed wubi!
The thing is i was noticing the laptop starting to slow down... so i did a free -m and noticed there was only 2 GB of ram. so says ubuntu and free -m,  I was looking through some forums and found a whole bunch of stuff on it... so i took a look and couldn't find anything,
So i checked the bios.. and it said the correct 3GB and vista also says 3GB! so i am not really sure what is going on :(
Does anyone have any idea?
I just need my extra gig of ram to be recognized!

---

### Post by FXEF on 2008-12-26
Try "cat /proc/meminfo" less quotes at the terminal and see what it list as MemTotal.

---

### Post by jaynewstrom on 2008-12-27
Hmm, Well that makes a little bit more sense!
Here is what i get:
MemTotal:      2830220 kB

So thats about 2.66 GB of ram.. not the full 3GB is their any kernel mods that i need to make or anything like that?

Thanks for your help!

---

### Post by Jammanuser on 2008-12-30
> **jaynewstrom said:**
> Hello,
Here is the deal,
I have windows vista, and installed wubi!
The thing is i was noticing the laptop starting to slow down... so i did a free -m and noticed there was only 2 GB of ram. so says ubuntu and free -m,  I was looking through some forums and found a whole bunch of stuff on it... so i took a look and couldn't find anything,
So i checked the bios.. and it said the correct 3GB and vista also says 3GB! so i am not really sure what is going on :(
Does anyone have any idea?
[COLOR="Red"]I just need my extra gig of ram to be recognized![/COLOR]

If all else fails, then download, install, and use [LVPM]("http://ubuntuforums.org/showthread.php?t=438591") to transfer your Wubi install to a dedicated partition, where you will also have a swap partition which functions as RAM! ;)

Cheers! :popcorn:

-Jam man

:guitar:

---

### Post by leeai on 2008-12-30
Has anyone bought this type of sling shot before that holds the amo in the handle? [http://www.liangdianup.com/sporting_1.htm](http://www.liangdianup.com/sporting_1.htm) 
this company has free shipping to anywhere in the world and they guarantee delivery to Australia. I heard that sling shots 
are ok to sell in Australia as long as you say they are being used to toss bait in the water when you go fishing, any truth 
to thatone?
:)

---

### Post by Coder543 on 2008-12-30
If you have an Ubuntu livecd then you could pop that in
at the menu click memtest (something like that)
see what it says.

---

### Post by jaynewstrom on 2008-12-30
I think i found out what it was,
I think it was just my graphics card sharing the ram :O
So i guess the rest of it was being used by that :/

Thanks for the help all!

---

