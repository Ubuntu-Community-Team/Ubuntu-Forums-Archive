---
title: "Help me!  Linux worse than Windows"
date: 2006-07-06
forum: Desktop Environments
---

### Post by jperez on 2006-07-06
Hey all,

I'm starting to think that Linux is worse than Windows!  Now, I have only used Ubuntu for about a weekm but it's already getting on my nerves.  Fact is, it works great...most of the time, but other times, even if I just open a folder, it will make the HDD stay on and the system becomes slow and unstable.  Also, the occasional lag is not something I like to deal with...anyway, I hope someone has a solution.  Here's my specs:

Dell Inspiron 8100 Laptop
Intel P3m 1Ghz/733 SpeedStep
256MB RAM
Ubuntu - Breezy Badger v5.10 w/ Windows XP Home on first partition

Thanks again!

Jesse~

---

### Post by LordRaiden on 2006-07-06
Please use Ubuntu Dapper Drake as it is the latest stable version. A lot of the problems that you are experiencing might have been resolved. Also, the title of your message does not help me in helping you in any way: it is an opinion and not a description of the problem.

---

### Post by xyz on 2006-07-07
Try this link...within the thread, you'll also find more links to slowness related pbms.
Slow does not necessarily mean Breezy is slow. My limited experience tells this can be a muti-facetted problem which will not be solved by, like LordRaiden said,giving us your opinion.

[http://www.ubuntuforums.org/showthread.php?t=142131&highlight=slow+breezy](http://www.ubuntuforums.org/showthread.php?t=142131&highlight=slow+breezy)

---

### Post by jperez on 2006-07-07
Thanks for the suggestions guys.  Don't get me wrong, I love Linux, but I was starting to think that Linux was worse, but it was just that Hoary and Breezy just didn't work that well on my P3 laptop.  I just finished updating to Dapper Drake and it fixed my problems.  I was a bit hesitant about downloading the ISO for ir since I don't have very much space left on my PC's HDD (PC with Windows XP Pro is used for burning CD's and DVD's while laptop is used for Linux and Windows XP Home) but when I found out I did, I downloaded and tried updatng it.  I ran into problems because it tried looking for **universe** and **multiverse** packages and since it couldn't find anything like that on the CD or online mirrors, it didn't complete until I finally changed everything back to only **main** and **restricted**.  I'm all set.  Sorry if I offended anyone with my thread title.  I love Linux more than Windows, but it was getting on my nerves that it was lagging and taking a huge load on my CPU for doing simple tasks.  Now that it's running normally, I can enjoy it fully.  Thanks guys.

Jesse~

---

### Post by xyz on 2006-07-07
Glad to hear it all worked out for you! Your initial post wasn't all that clear as to what exactly your problem was but no offence taken!
Happy Ubuntu to you!

---

### Post by LordRaiden on 2006-07-07
Universe and Multiverse repositories are only available online I think.

---

### Post by jperez on 2006-07-10
Guys,

I thought my problems were over...they're not.  The touchpad mouse stops responding after a certain amount of usage (random), the system still lags and certain tasks make the HDD, CPU and RAM work hard, to the point where no user actions can be executed and it takes about 30 minutes for the system to recover.

Now, I love Linux because it's very useful, it's a breath of fresh air from Windows and very customizable.  I want it to replace Windows, but the fact is, I might just dump Ubuntu and go back to Windows if my laptop has these types of problems.  I really don't understand why the older PC I installed it on was fine (yet a bit slow) while this just has too many problems.

Can anyone tell me why this is happening?  I am doing something wrong?  Is my laptop's speed not sufficient?  Please guys, just let me know so that I can take care of it and if there is no way of taking care of it, then I'll have no choice but to go back to Windows.  Thanks again guys!

Specs:
Device: **Dell Inspiron 8100 Laptop**
CPU: **1Ghz/733Mhz Intel SpeedStep**
RAM: **256MB RAM**
Video: **32MB (built-in)**
OS: **Ubuntu Dapper Drake v6.06* and Windows XP Home**

*Problems were occuring since Hoary Hedgehog v5.04 release

Jesse~

---

### Post by LordRaiden on 2006-07-10
Again, you aren't saying when it is slow, but that it is slow, and again you are bringing up your opinions.

Some questions I would like you to answer in detail.

1) What are you running when it becomes slow?

2) Do you get any error messages while the computer **starts**?

3) Do you get any error messages while the computer **shuts down**?

4) Did you check your drive for errors using e2fsck?

5) Are you trying to directly write from Windows to Ubuntu and Ubuntu to Windows? (because you should not unless your Windows XP is using a FAT32 filesystem).

---

### Post by jperez on 2006-07-10
> **LordRaiden said:**
> Again, you aren't saying when it is slow, but that it is slow, and again you are bringing up your opinions.

Some questions I would like you to answer in detail.

1) What are you running when it becomes slow?

2) Do you get any error messages while the computer **starts**?

3) Do you get any error messages while the computer **shuts down**?

4) Did you check your drive for errors using e2fsck?

5) Are you trying to directly write from Windows to Ubuntu and Ubuntu to Windows? (because you should not unless your Windows XP is using a FAT32 filesystem).

Well, I don't know how I'm bringing up my opinions, but whatever.

1) GAIM or Firefox or a combination of the two and sometimes it will have a huge load when changing Themes, changing backgrounds, updating the system, switching different windows, posting something online and sometimes it won't.

2) No

3) No

4) No, how do I do that?  Remember, I'm still a newbie to Linux.  I don't know how to run every function.

5) No, I network to my PC and there are no problems with that.

Jesse~

---

### Post by xyz on 2006-07-10
Hey...good old Jesse is back...*just kidding*
How about you check this out>
[http://www.linuxquestions.org/questions/showthread.php?t=183197](http://www.linuxquestions.org/questions/showthread.php?t=183197):cool:

---

### Post by xyz on 2006-07-10
Forgot smth> I do not know HOW MUCH of a n00b you are *I sure am!* so I will add this to my previous post>
To get Knoppix Live CD:
[http://www.linuxiso.org/distro.php?distro=44](http://www.linuxiso.org/distro.php?distro=44)
A usuful tool *among other things...to rescue* to keep around even for other pbms than your present one.
Once dowloaded, burn the .iso IMAGE onto a CD which will then be bootable from CD ROM IF your BIOS is set to boot from your CD ROM.
If you cannot understand the above, ask or...better yet, do a SEARCH for "burn .iso", "change BIOS boot sector" right here on the site.
I am sorry if I underestimated your knowledge of the Linux world. I-ve seen folks 10,15 years into Linux...calling themselves n00bs. Always lots to learn.
I haven-t installed Dapper yet *my HD seems dead* but from what I hear Dapper Live is on the same CD as the Install-s.
Good luck, Jesse!

---

### Post by jperez on 2006-07-10
I've only been using Linux for a couple of weeks, that's how much a n00b I am, but I catch on quickly due to my years of experience with computers in general.  Thanks for the link to the ISO image.  That will come in handy.  Now, once I have everything squared away, what should I be looking for once the command is run, or is everything automated?  Now, if everything is fine, then what should I do?

Like I said, I love Linux and want it to replace Windows permanently, but with all these problems **I'm** having (directed at LordRaiden), it seems that Linux just isn't working better then Windows on my laptop and, so far, Windows is looking better **to me** than Linux due to the lag, load and touchpad problems.  In fact, as we speak, I have my Logitech USB Optical mouse plugged in so that I can actually move the cursor around.  My touchpad stopped working 10 minutes after I turned on the laptop.

I just want a Linux OS that is going to be good to me.  Ubuntu is great and I have no other problems with it, except for these three problems.  Oh well, maybe Ubuntu is not for **me**.  If nothing can be done, can you recommend another Linux OS, other than Red Hat?  Thanks again for putting up with me while being such a pest.

Jesse~

---

### Post by xyz on 2006-07-10
Hello Jesse~

Welcome to the Ubuntu Document Storage Facility:
[http://doc.gwos.org/index.php/Main_Page](http://doc.gwos.org/index.php/Main_Page) 

These here links may come in handy:
[http://www.knoppix.net/wiki/Knoppix_FAQ](http://www.knoppix.net/wiki/Knoppix_FAQ)
[http://www.knoppix.net/forum/](http://www.knoppix.net/forum/)

[b]Prior to solving specific pbms, running Ubuntu Live CD off your CD-ROM is often recommended 
to get the overall hang of it.[/b] This would not solve your pbms, but getting the feel of a new
OS never hurts...to try and get into solving upcoming pbms.

Try to boot in "Recovery Mode" (Failsafe equivalent); you should then get a root prompt 
(Administrator); type 'e2fsck' or 'fsck' (NO QUOTES)...at this point, you'll see a bunch 
of options (f.inst. -y)...try them out! See what works AND jot down briefly what it says.
I guess this is a sort of "disk verification" under Windows...like when you can set it to verify
at next boot.
Don't run these commands on a mounted sys...as explained in one of the links I gave you earlier.
Good luck and be patient would be my main advice.;) 
Hang in there!

PS: If you'd like to test other distros (Live CD's) to see whether it suits you and your laptop better, download them/burn the ISO on a CD-RW and boot on 'em!

---

### Post by greengrocer on 2006-07-11
Careful when choosing your themes.  I have noticed that some themes can cause the problems you describe.

Why dont you try and leave Ubuntu on the default theme for a while and see how it goes.

I was having strange problems at one time and certain clues I had at the time pointed to the theme I was using as being the cause of the problem.  I left my machine on the default theme for a few days and noticed that the problem went away.

Following that, I was more careful which themes I used and all is swell now.

---

