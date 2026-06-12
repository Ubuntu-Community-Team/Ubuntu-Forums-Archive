---
title: "New user experiment"
date: 2005-12-19
forum: General Help
---

### Post by Sephatine on 2005-12-19
Hello all,

I'm interested in documenting my experience of migration (both physical, social, and psychological) from a purely windows based enviroment into the world of Linux.  I've been reading a great deal of reviews, overviews, screenshots, debates, and flame wars regarding the different distributions of linux and have landed myself here.

I am a network administrator and programmer that has had very little linux experience.  My experience has been in microsoft networking, .net programming, and fiddliling and gaming on the side. I have in my years installed a distrubtion just to see what the fuss was about, but have never used one for more than a handful of minutes.  I desperately want to find a home among the linux community as I fully embrace the ideals of an opensource community.  

What I'm looking for is a group of people with experience to walk me through this process, point me to documentation that would make sense to the uniniated, and get me to the point of being able to be effective in the linux enviroment.  Specifically I'm going to want to end up programming cross platform applications.. but I can understand if that's a ways off.

Through this process I'll be documenting my thoughts and actions.  In the end perhaps it will be useful to someone else.  In the very least it will be educational for me as I'm determined to make this work.   

I've already downloaded both an i386 cd and the 64 bit dvd version of umbuntu.  I'm running an AMD 64 machine but have some concerns over software compatability with 64 bit operating systems. (my windows experience coming through)  Which version is best for me to install if I'm needing to run a variety of apps and want to develop apps in the future?   Also can someone point me to documentation about how linux itself operates so I can get familiar with the buzz words.  For instance: I understand that a 'package' is basically an installation for software, but understanding that install process within linux is blank for me.

Thanks to whomever decides to pick up on this.

Marc

---

### Post by Zelut on 2005-12-19
Well there is quite a bit there to take in but I'll take a bite.

I have also had off & on experience using Linux, most of those experiences leading me back to Windows.  Earlier this year however I came across Ubuntu and have been 100% since.  It has been the only distribution that has worked well for me.  Since that time I've spent my time contributing to these forums, the [Ubuntu Wiki]("http://wiki.ubuntu.com") and the #ubuntu on IRC.

To find more about linux itself & definitions I would probabaly check out [Linux.org]("http://www.linux.org")

I'm sure you'll find that this forum is very active & very few posts go unanswered.  If you have more specific questions feel free..

---

### Post by ekarni on 2005-12-20
Welcome aboard!  I think you'll find that you can get most any sort of support you need by posting here or just searching through the archives.

Regarding i386 vs. AMD64, I'm also running an AMD64 machine, and started out with the 64 bit distribution.  Unfortunately, there are still some pretty important (to me, anyway) programs like OpenOffice (MS Office equivalent), flash plugin, and Acrobat reader that haven't (yet) been effectively ported to to 64 bit versions.  It's possible to run 32 bit programs using a "chroot" environment, but it's a nuissance to setup and a bit of a lash-up solution.  I switched (reverted?) to the 32 bit distribution when the latest Ubuntu release came out a few months back, and have found it to be much easier to get everything working as desired.  (Not that doing so under 64 bit was terribly hard; it just required some extra steps.)  Speed wise, I didn't notice a difference between the two.  I'm looking forward to going back to Ubuntu64 once this architecture becomes a bit more common and the programs catch up.  Until then, I think 32 bit is the way to go for mainstream users.  

(Catch 22 here:  the developers have no incentive to push the 64 bit versions without 64 bit users; 64 bit users have a disincentive to use 64 bit without working software for it!)

---

### Post by MighMoS on 2005-12-20
Two things I've found that's been useful for myself and friends:
[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)
[http://www.ubuntuforums.org/showthread.php?t=73885](http://www.ubuntuforums.org/showthread.php?t=73885)

---

### Post by BathroomNinja on 2005-12-20
I am also a Windows user who finnaly made it happen after years of trying (still love Windows, just don't use it much).  I honestly have found that the best way to learn Ubuntu, is by helping out on the forums here.  I find problems that others have, and I go search for the answer.  I also try to recreate these problems when I'm able to better understand the issue.  

Doing this has helped me learn so much in my short time using Ubuntu.  I highly suggest helping out in the forums as a great tool to becoming more effective in the Ubuntu Linux enviornment.

As to the i386 vs 64, I also have AMD 64, but I took the low road and installed i386 to make life easier.

---

### Post by Sephatine on 2005-12-21
Thanks to all of those who have responded thus far.  If you're at all interested, here is the rundown of what my week has been like.


-Read a large amount of linux tutorials.  [www.linux.org](www.linux.org) had what i was looking for in terms of a crash course.  Still wading through all of the material, but it's given me a decent start.

-Installed ubuntu 5.10 on multiple systems multiple times (starting over again tonight).  This isn't because I've caused the system to have problems, but more that as I begin to become more and more familiar with the system, I'm wanting to try and see how long a 'real' installation and customization takes me.

-Gained a rudamentary understanding of bash.  The shell isn't really that uncommon to me.  I still use DOS commands on occasion so i fine with using the terminal in ubuntu.  I acutally find it a little refreshing.  I do however see where such interaction with intimidate a lay user wanting to try linux. Which leads right into my next item.

-DVD and multimedia playback functioning.  At first I was a little concerned.  Not that I thought that I couldn't get it to work.  I was sure that if people had confiugured it before, and there were tons of plugins and tools available, that it was possible.  My biggest problem was the fact that there were so many avenues of information to pursue, and most of them gave steps and not concepts.  It's great to lay out a step by step for a user on how to get their mplayer to play dvd and wmv formats, it's even better if you can explain the shell commands behind it, or what your gui tool is doing.  Most explainations were either very vague, or used terms I was unfamilar with.

All in all it's been enjoyable.  It's not hard to see the appeal of the power gained by savy people.  I'd consider writing up a basic crash course myself once I get enough understanding to be able to help someone.  I'm just scared it will add yet another avenue for people to look at rather than centralizing information.  I'm guessing the wiki is the place of prefernce for everyone?  If that is the case, why are so many people linking to external sites in their signatures?

~Marc~

---

### Post by BathroomNinja on 2005-12-21
I think people link to external sites because they want to make sure they retain *their* howto in original format.  With a wiki, anyone can edit what you made.  That's just my guess.  But that's also why we have forums.  Lots of people with free time who enjoy helping others and learning more themselves.  Each remembering answers or knowing where to look.  The Linux *community* is the 'central repository' or information.

---

### Post by Madpilot on 2005-12-21
[QUOTE=Sephatine]I'd consider writing up a basic crash course myself once I get enough understanding to be able to help someone.  I'm just scared it will add yet another avenue for people to look at rather than centralizing information.  I'm guessing the wiki is the place of prefernce for everyone?  If that is the case, why are so many people linking to external sites in their signatures?
[/QUOTE]

There's been a bit of a squabble about documentation & wikis in the Ubuntu community, but it seems to be largely smoothed over now.

[https://wiki.ubuntu.com/](https://wiki.ubuntu.com/) is the main official wiki; getting an account there is easy and anyone who wants to improve it is encouraged to!

Some basic guidelines are here: [https://wiki.ubuntu.com/WikiGuide](https://wiki.ubuntu.com/WikiGuide)

Welcome to Ubuntu!

---

### Post by Sephatine on 2006-01-03
It's been a crazy week, but I thought I'd give an update and ask a few more questions.

SO.... I've installed ubuntu about 12 times now.  I initially used the automatix tools to get the system to a functional point, and determine what, if any functionality I'd lost.  I then began doing those same installs manually so that I understood what packages were required to gain what functions.  I'm now back full circle using the automated tools just to save time.  I have a fairly good understanding of what is going on though. The wiki really is a nice tool, once you get past the initial learning curve. To new users I'd think they'd be scared.

To my pleasant surprise, I caught myself annyoned when booting back into windows at the loss of some of the linux/gnome features that I've grown accustomed to. (fast installs, fast cd/dvd copy, document/picture previews, fast interface)  

Now for the questions I still have.

I tried doing an installation where I partitioned out my /home to it's own (FAT32) partition.  I'm not sure how I was supposed to do this though. I tried creating the partitions manually and setting this partition as logical and setting the mount point to /home.  However when I finished the installation and was being prompted to create the first user account, it would loop through that creation screens without giving me an error message.  As soon as I partitioned again and let ubuntu create the partitions automatically, it worked fine again.  What am I doing wrong here? (for future reference) and for now, what can I do to set my /home to a new partition?  (needing to resize my / partition and create a FAT32 partition for this.)

The other question I had is a bit more silly.  I've been slowly introducing opensource softwares to my wife with whom I share the home computer.  I've gotten her off of msn messenger onto jabber, off of MS Office onto OpenOffice.  What keeps her booting back into windows most often though are the stupid little msn/yahoo games.  These are running under shockwave, which I understand is not ported to linux yet, and most seem to use activex to install.  All in all it's a gross combination.  Any chance there are sites out there that are linux compatable that offer these mundane distractions for this populace?  Alternatives?  If I can keep her from booting into windows then I'm sure I can convert anybody (home user).

Thanks in advance for all the help that's been provided thus far.

~Marc~

---

### Post by steve.horsley on 2006-01-03
[QUOTE=Sephatine]It's been a crazy week, but I thought I'd give an update and ask a few more questions.

SO.... I've installed ubuntu about 12 times now.  I initially used the automatix tools to get the system to a functional point, and determine what, if any functionality I'd lost.  I then began doing those same installs manually so that I understood what packages were required to gain what functions.  I'm now back full circle using the automated tools just to save time.  I have a fairly good understanding of what is going on though. The wiki really is a nice tool, once you get past the initial learning curve. To new users I'd think they'd be scared.
[/QUOTE]
With an attitude like that, you should learn very fast.> 
To my pleasant surprise, I caught myself annyoned when booting back into windows at the loss of some of the linux/gnome features that I've grown accustomed to. (fast installs, fast cd/dvd copy, document/picture previews, fast interface)  

That can come upon you surprisingly fast. It doesn't go away.
[/QUOTE]
Now for the questions I still have.

I tried doing an installation where I partitioned out my /home to it's own (FAT32) partition.  I'm not sure how I was supposed to do this though. I tried creating the partitions manually and setting this partition as logical and setting the mount point to /home.  However when I finished the installation and was being prompted to create the first user account, it would loop through that creation screens without giving me an error message.  As soon as I partitioned again and let ubuntu create the partitions automatically, it worked fine again.  What am I doing wrong here? (for future reference) and for now, what can I do to set my /home to a new partition?  (needing to resize my / partition and create a FAT32 partition for this.)
[/QUOTE]
I can only guess that it didn't like the filesystem type. FAT32 cannot hold the file permissions setings properly - maybe the adding a user bit of the installer kept crashing? Try using ext3 or reiserfs for the filesystem.
> 
The other question I had is a bit more silly.  I've been slowly introducing opensource softwares to my wife with whom I share the home computer.  I've gotten her off of msn messenger onto jabber, off of MS Office onto OpenOffice.  What keeps her booting back into windows most often though are the stupid little msn/yahoo games.  These are running under shockwave, which I understand is not ported to linux yet, and most seem to use activex to install.  All in all it's a gross combination.  Any chance there are sites out there that are linux compatable that offer these mundane distractions for this populace?  Alternatives?  If I can keep her from booting into windows then I'm sure I can convert anybody (home user).


Not sure. If by shockwave, you mean Macromedia flash player, that is available for Linux. You can install it into Firefox and run flash games in the browser. If it means something else then I goofed.

Active-X? I don't even want to know.

---

### Post by kperkins on 2006-01-03
Fat32 is not a Linux filesystem (it's DOS or Windows), and even though Linux can read and write to it, I don't think that you can use it for your /home part..  I use ReiserFS for all my partitions (I'm completely Ubuntu--no Windows), although ext3 (with journaling) might be a better choice.  My basic reason for this is that I use a laptop, and prefer not to lose data if my system shuts down through loss of power, or whatever. If Iused it on a desktop, I'd probably use ext3, just because it's (supposedly) faster.

---

### Post by Sephatine on 2006-01-03
Maybe I'm misunderstanding the concept then.  Thanks for the clarification by the way.  SO if I can't use a FAT32 partition as a mounted drive that I store all of my personal files on that is accessible from windows.. oh well.  I just won't boot into windows :P

I'll just make a small partition for passing files back and forth between the two OS just in case.  Are there partitioning tools already built into linux?

~Marc~

---

### Post by qferret on 2006-01-03
[QUOTE=Sephatine]SO if I can't use a FAT32 partition as a mounted drive that I store all of my personal files on that is accessible from windows.. oh well.  I just won't boot into windows :P

I'll just make a small partition for passing files back and forth between the two OS just in case.  Are there partitioning tools already built into linux?

~Marc~[/QUOTE]

You can mount Windows partitions... Not sure what file systems you need for the various partitions though...I use ext3 for the whole OS and have a slave 120GB formatted to fat32 to share out to my wife's laptop.

Partitioning tools. can't remember if their in by default, but check in Synaptic for gparted or qtparted

---

### Post by jrb114 on 2006-01-03
You can read and write to ext3 partitions in Windows. I forget what the tool name is but a quick Google for "ext3 windows" has come up with a variety of candidates. I've used two different ones in the past, both free (although I don't know if they're open source), and I've found them to be perfectly stable. 

[http://www.fs-driver.org/](http://www.fs-driver.org/)

HTH

J

---

### Post by mcduck on 2006-01-04
[QUOTE=Sephatine]Maybe I'm misunderstanding the concept then.  Thanks for the clarification by the way.  SO if I can't use a FAT32 partition as a mounted drive that I store all of my personal files on that is accessible from windows.. oh well.  I just won't boot into windows :P

I'll just make a small partition for passing files back and forth between the two OS just in case.  Are there partitioning tools already built into linux?

~Marc~[/QUOTE]Yes, you can use FAT32 to store things and move them between linux and windows, it's just that your home partition has to be on a linux filesystem, as FAT32 doesn't understand linux file permissions. So it's a good idea to make a separate partition only for moving files. 

I would't suggest using any tool to write to NTFS under linux, or write to EXT2/3 under windows.. They might work, but then again they might break your filesystem completely..

You can install gparted or qparted to do the partitioning, if you don't do it while installing Ubuntu.

---

### Post by Sephatine on 2006-01-05
I'm not sure what the 'proper' procedure was, but I couldn't actually do anything with either gparted or qtparted while utilizing the OS.  I did however find a nice gparted Live CD that did the trick for me.

Once I had my new partition, I used the disk tools to tell that partition to mount as /home.  I foolishly believed that this would move my profile to that machine. (Much like a redirection of My Documents under XP)  I however found that was not the case.  In fact it immedately rendered my account useless.  I fumbled through the failsafe terminal login and was able to get back in, but am not sure how I was 'supposed' to do this procedure.

Anyone care to enlighten?  Also, anyone found a repository of games similar to msn games?

Thanks tons guys,

~Marc~

---

### Post by mcmillan on 2006-01-05
I'm a little unclear, do you have it working and are just wanting to know if there's an easier way to do this, or are you still needing to change your home folder? 

The reason you couldn't change the partitions without the liveCD is that they are mounted, so some kind of liveCD was needed. I'm not sure if this is the best way to go about moving the home information to a new partition, but this would be how I think it could be done. 

Make a new mount point for your new partition, something like /mnt/NewHome

Copy everything from your home folder into this, make sure you include the hidden files that start with a period. A easy way to do this would be ```
cp /home/[name]/* /mnt/NewHome
```

Change your fstab file so that it's telling to mount your new partition as home the line for me is ```
/dev/hdd8       /home           ext3    defaults        0       2

```
(I'm not sure if there would be confusion with your old home partition and how to go about getting rid of it. I suppose it could be possible to delete it, but I don't know if there's a safer solution)

When you restart you should have a new home partition.

For the games there should be a category in synaptic with a lot of games, especially once you enable the multiverse and universe repositories.

---

