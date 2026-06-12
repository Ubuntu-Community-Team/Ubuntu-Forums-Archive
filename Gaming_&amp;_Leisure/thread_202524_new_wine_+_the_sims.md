---
title: "new wine + the sims"
date: 2006-06-23
forum: Gaming &amp; Leisure
---

### Post by slugkilla on 2006-06-23
After Installing the new version of wine, I ran the Sims setup.exe and to my shock, it finally ran. It installed everything up to the point where it needs the 2nd disk. Wine is not so good at changing cds. :( Can't figure this one out. Anybody got ideas?

---

### Post by KingBahamut on 2006-06-23
have you though about using xwine the X GUI package for wine? 

Mounting and unmounting CDs has always been an issue with me, so I usually setup a loopback iso mount -- 

mount file.iso /cdrom -t iso9660 -o loop

Youll need to create an ISO of the CD your using to install but it should feasibly work properly.

---

### Post by slugkilla on 2006-06-23
well I stuck both cds into both my drives and ran setup.exe. It looks like both cds get installed but the program does not realize it! A window pops up and says that he 2nd cd is not installed or something like that. If I click OK then it erases the exe file created in the install directory. Now that is just plain mean. So I have this idea to force quit the program so it can't do this. 

Allright here goes........snap
Yeah that part worked, but the main program to run it only opens up the virtual desktop and does not run :(
one of these days somebody is gonna figure this one out

---

### Post by slugkilla on 2006-06-23
Hey KB,
     I'll try your advice later. Thanks.

---

### Post by slugkilla on 2006-06-23
How do I make an ISO? I can't remember the command.

---

### Post by KingBahamut on 2006-06-23
open up a terminal. 

man mkisofs

---

### Post by tiftmasta on 2006-06-24
[QUOTE=slugkilla]After Installing the new version of wine, I ran the Sims setup.exe and to my shock, it finally ran. It installed everything up to the point where it needs the 2nd disk. Wine is not so good at changing cds. :( Can't figure this one out. Anybody got ideas?[/QUOTE]

If you use:
$ winecfg

then make sure the drive you have set for your cd-rom drive is set to CD-ROM drive instead of hard disk.

Then when it asks for cd 2 you can just type into console:
$ wine eject

I'm now running into the problem where setup doesn't recognize cd 2 as cd 2. We're one step closer, right?

---

### Post by tiftmasta on 2006-06-24
When you insert CD 2-4 are there files on there or is it just a few huge jibberish files?

---

### Post by lotusleaf on 2006-06-24
Just FYI FWIW I recommend providing testing results/experiences with any Windows games/apps to:
the [WINE Application DB](http://appdb.winehq.org/), be they positive or negative.

These pages from the DB may help: [The Sims](http://appdb.winehq.org/appview.php?appId=768) - [The Sims 2](http://appdb.winehq.org/appview.php?appId=1942) - [The Sims: Online](http://appdb.winehq.org/appview.php?appId=3215)

I find even reading the experiences there from other users often helps with various issues and it can help one know what to expect before they attempt to run a particular program.

---

### Post by slugkilla on 2006-06-25
Well my cd drives work now, but the games don't.

---

