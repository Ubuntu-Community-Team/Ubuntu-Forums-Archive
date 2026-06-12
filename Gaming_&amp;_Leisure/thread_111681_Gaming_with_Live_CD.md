---
title: "Gaming with Live CD"
date: 2006-01-02
forum: Gaming &amp; Leisure
---

### Post by catalytic on 2006-01-02
;)  Hi, sorry if this has already been asked, and sorry for being a linux noob!!

I just started using the Ubuntu live CD lastnight, I am fed up with windows!! (it updated the other day and killed my net)

I would like to play Enemy Territory, on windows I had nothing but problems and a big lag. I am hoping that it will work better on linux.

My problem is I have no idea how to use Ubuntu for gaming. Is is even possible to install games and run them on the live CD???

I am too scared of loosing all my programs if I get rid of windows. I really don't have the room to install Ubuntu, and if I did I wouldn't even know how or which hardrive to install it to. I'm finding it really hard to get information on how to do these things in Ubuntu. Nothing in the FAQ, nothing in google about running games with the live CD.

I find text files that tell me to use some command in the configuration console or something.... I have no idea what this means.... is this a dos prompt or something I'm looking for like the windows run command?

Thanks

---

### Post by SupaShaD on 2006-01-02
Well let's address first things first:

1.) An Enemy Territory Client (2.6) for Linux is available here:
[http://www.fileplanet.com/124801/120000/fileinfo/Return-to-Castle-Wolfenstein:-Enemy-Territory-Client-v2.60-%5BLinux%5D](http://www.fileplanet.com/124801/120000/fileinfo/Return-to-Castle-Wolfenstein:-Enemy-Territory-Client-v2.60-%5BLinux%5D)

2.) No, you won't be able to download/install stuff while using the live CD.  You could, to a removeable drive or something similar (or even to your actual windows hard drive if you mount it) but it's not recommended until you get a grasp on the general Linux workspace first.

3.) You can always run a dual boot system.  What this means is when you format your computer you'll be creating two partitions (two spaces if you will) on your hard drive.  Install windows on one, and then restart and install Linux on the other.  Linux will allow you to modify your computer so when you start it up you can select whether you want to boot into Windows or Linux.  This allows you to keep your preferred applications that you can't use in Linux and still use them by simply resetting your computer.

You can find a good tutorial on the subject here:
[http://www.littlewhitedog.com/](http://www.littlewhitedog.com/)

4.) The terminal is similar to a dos prompt yes (albeit more powerful and efficient ;)).  You can find it by clicking Applications > Accessories and selecting the Terminal.  The terminal allows the entry of text based commands to control Linux and perform functions.

Hope that helps.
  -SupaShaD

---

### Post by catalytic on 2006-01-02
Thanks, that help heaps!

How much space does Ubuntu take? Can I just put it on my D: and keep windows on the C:, I'm keen to use Ubuntu as my main OS. 

I HATE WINDOWS!!!

Thank you!

---

### Post by SupaShaD on 2006-01-02
I'm not sure exactly how much space Ubuntu takes, but it does fit and perform basic functions on one cd, so it's safe to say if you only had around 1GB you could probably install it.  It's functionality would be limited though.  I think a good amount of space for a Linux partition would be around 3-5GB to allow for driver installs and a small amount of space for any downloads you might choose to make while using it.  Obviously you'd want to increase this amount depending on the amount of time you plan to stay in the Linux environment.  If you plan on trying to make it your sole OS with only Windows as a backup for gaming then you'll want to increase the amount quite a bit to ensure you have room for all the drivers / programs / downloads you do while in Linux.

If you want to use Linux for gaming, as several games come with Linux ready clients or install routines (Enemy Territory, Unreal Tournament 2003/4, Quake III Arena, to name a few) then you'll want to increase that amount significantly as those games take up quite a bit of space.
  -SupaShaD

---

### Post by catalytic on 2006-01-02
:KS AHHH...

I have to make sure that it is installed at the start of the partition right? Ok now to figure out how to do that. I think I can spare 10gig for Linux on my D:

Maybe I am being a little too ambitious.... I have no idea how to install an operating system... but I figure I can't do too much damage as long as I don't touch windows! At least I have the live cd which I can use if I do make a mistake!

---

### Post by SupaShaD on 2006-01-02
Well the thing is you can't just install it on any old partition, you'll have to format whatever partition you install to because Linux uses a different filesystem than windows (which is why it's a bad idea to write to Windows formatted disks in a Linux environment, you run a risk of messing it up).

If you're really interested in getting Linux running as a primary OS and such I recommend first googling for all the information and beginner's tutorials you can find.  Then going out and purchasing a book on Linux and giving that a good read.  I purchased the Linux Bible myself, and while outdated now it's still a good reference on all the commands.  Once you feel comfortable with the knowledge, dive into the Live CD and test out some of your knowledge, see what you can remember, what you know, etc. and read up on the Man pages for any commands you don't understand (from a terminal: man cmdname).

Also, head over to the Little White Dog page I posted earlier and dig through their how-tos to find their dual boot one, you'll be able to glean the information you need to install Linux side by side with Windows with that.

Good luck.
 -SupaShaD

---

