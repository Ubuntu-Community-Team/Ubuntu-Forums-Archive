---
title: "How to wipe ubuntu partition?"
date: 2009-04-21
forum: General Help
---

### Post by Bearded-flower on 2009-04-21
I have currently dual booting with  easy peasy and XP i am sick to death with easy peasy it has messed me around so much and it is notthing but a F***ING PAIN IN THE A**E!!!
i want to completley wipe it and install bog-standard jaunty.
How can i achieve this?

---

### Post by oOarthurOo on 2009-04-21
dban

---

### Post by Bearded-flower on 2009-04-21
Could you elaborate on that please?

---

### Post by Jimmynemo2 on 2009-04-21
Howdy,

in terminal, type sudo gparted

if its not installed, type 

sudo apt-get install gparted

gparted can wipe any type of partition and with relative ease.  just make sure you do wipe the partition you intend to, as you can fubar your drive if you get rid of the wrong thing.

Hope this helps, and definitely ask more questions if you aren't sure this is what you want and what you are doing.

---

### Post by Bearded-flower on 2009-04-21
So thats not going to wipe the XP partition unless i click on it?

---

### Post by Jimmynemo2 on 2009-04-21
Correct. You got it.

---

### Post by Bearded-flower on 2009-04-21
Thanks.
*sigh* god damn NBR!!!

---

### Post by oOarthurOo on 2009-04-21
Elaboration: [http://www.dban.org/](http://www.dban.org/)

You would download the iso, burn it to a disc, reboot, and watch your hard-drive disappear. If you just want to flatten it then choose the fastest method, all zeroes.

---

### Post by Bearded-flower on 2009-04-21
yeah but the thing is i need to keep the XP partition

---

### Post by Jimmynemo2 on 2009-04-21
Yeah Dban I am pretty sure wipes total drive right? I dont know that it can do single partitions, though I could be wrong.

---

### Post by Bearded-flower on 2009-04-21
OK i got gban crankin' and it came up with this screen.
what one do i wipe??????
I know XP is installed on the OS_INSTALL bit

So gparted wont affect the GRUB boot thing that winoz need?

---

### Post by Jimmynemo2 on 2009-04-21
wow, thats a ton of partitions, crazy thats how they come. 

I would remove all partitions that arent the XP partition, then extend the xp partition to fill the space after it, and install ubuntu on the other side of the drive.

BUT, not sure if once you remove those partitions you'll be able to boot into xp till you get ubuntu installed and it installs grub for boot loading, so once you do the next step, be ready to roll.

Also, it may tell you it cant remove partitions when in the OS, and if so, boot into the ubuntu live cd and deal with it from there.

---

### Post by Ericyzfr1 on 2009-04-21
Tried Gparted LiveCD?

---

### Post by Jimmynemo2 on 2009-04-21
Gparted live cd / ubuntu live cd with gparted in it...

Doesnt matter to me, your call. I was just avoiding having him download another cd since if he's getting ready to install ubuntu he's got it sitting there anyway (I hope)

---

### Post by Bearded-flower on 2009-04-21
UUUUM how can i tell which ones are XP???

---

### Post by Jimmynemo2 on 2009-04-21
sda2  looks to be it. The other ntfs partition is likely a recovery partition for XP.

If you want to make sure, boot into XP, use XP's partition manager to see what size and format your XP partition is- and more than likely its NTFS and around the size of sda2.

---

### Post by Bearded-flower on 2009-04-21
XP has a partition manager?

---

### Post by Bearded-flower on 2009-04-21
DAMN, i have to go to work is there anyway i would be able to get you to do a step-by-step guide?
Im kinda new to all of this

---

### Post by Jimmynemo2 on 2009-04-21
Yup, right click my computer, click manage, then on left pane click disc management. Not as full featured as gparted, but it shows the same drive labels you see when you are in the my computer screen, so you'll be able to  verify wich is wich.

It wont let you extend the drive to fill the space, but it will let you delete partitions at least.

---

### Post by Bearded-flower on 2009-04-21
So can i just delete ubuntu from there?

---

### Post by Jimmynemo2 on 2009-04-21
Sure could. Fire at will.

---

### Post by Jimmynemo2 on 2009-04-21
Although you suffer a -10 geek points for using windows tools to do what gparted would have done. 

Oh yeah, and while in windows you get a +7 risk of encountering a wandering monster.

:)

---

### Post by Bearded-flower on 2009-04-21
would it b easier to gparted or to wipe it from winows???

---

### Post by Jimmynemo2 on 2009-04-21
Really the same either way. wichever you feel more comfortable doing it with.

---

### Post by Bearded-flower on 2009-04-21
XD thanks man im gunna leave it for a few days untill jaunty comes out (after all i still need ubuntu to make a livecd) and ill research it some more.
so is it really as easy as to log into winblows right click my computeer and away we go?

---

### Post by Jimmynemo2 on 2009-04-21
Yup, just follow the instructions above, and post if you need a hand, but you should be just fine.

---

### Post by Bearded-flower on 2009-04-21
Awsome thanks. ill do it the windows way just because it feels a little safer i mean u cant destrow windows if ur logged into it right, right!!!
I wish jaunty would hurry up and release so i can get this filth of my hard drive.
OH GRR i need a portabel hard drive to back all my s**t on

---

### Post by Jimmynemo2 on 2009-04-21
Well have fun, glad we could help. And you definitely have the right idea- cant remove the windows partition while in it, so its a good way to feel safe you wont hose your XP install.

Im looking forward to launch day too. Love the beta, and am waiting till launch day till I install it on my wife's computer. So thursday cant come soon enough.

---

### Post by Bearded-flower on 2009-04-22
Ok iv beeen thinking about what would be the bestim going to wipe my entire harddrive including XP partirion and install jaunty.
how should i go about this and is there any precautions i should take first?

---

### Post by Ms_Angel_D on 2009-04-22
Back all your stuff up then insert a Jaunty CD and boot from it and during install, select Guided Use entire hard drive.

---

### Post by Bearded-flower on 2009-04-22
Ok so after i have backed everything up i can just wipe the hard drive?
No repartitioning or anything?

---

### Post by Ms_Angel_D on 2009-04-22
> **Bearded-flower said:**
> Ok so after i have backed everything up i can just wipe the hard drive?
No repartitioning or anything?

If your wanting to install Jaunty Only then yes that's correct.

---

### Post by Bearded-flower on 2009-04-22
Cant i just use the live cd to erase it or is that option just hiding it?

---

### Post by Jimmynemo2 on 2009-04-22
Sorta, no need to do it within the live CD, just once you click to install it, it'll be one of the pages that comes up during the install.

If you want to do it before hand, you can use gparted to do it before, but really thats no faster or better (no good reason to not just let ubuntu do it during install.

The screen during install looks like this:

[IMG]http://1.bp.blogspot.com/_MfwRx_4ERx8/Sa6_M2URLeI/AAAAAAAAAxA/rEcbk5uSrhA/s400/ubuntu-partition-8-all.jpg[/IMG]

That site also has a full walkthrough on the isntall process, feel free to check it out:

[http://www.nyutech.com/2009/03/easy-guide-to-getting-started-with.html](http://www.nyutech.com/2009/03/easy-guide-to-getting-started-with.html)

Hope this helps.

---

### Post by Bearded-flower on 2009-04-22
Ok, brilliant thank you so much.
ill do all this on friday

---

