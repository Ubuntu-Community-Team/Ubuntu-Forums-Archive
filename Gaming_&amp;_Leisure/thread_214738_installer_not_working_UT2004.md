---
title: "installer not working UT2004"
date: 2006-07-13
forum: Gaming &amp; Leisure
---

### Post by Bmbshl on 2006-07-13
I've worked for 2 days now and I'm baffled by this....I get this message in terminal when I try to run the installer file from CD:

**bash: cd: UT2004_CD1: No such file or directory** 

Then the terminal terminates and my cd drive locks up. (spins constantly)
I know the drive and the cd both work in Windows.  I have a new install on my other partition.  

I have found and istalled/updated SDL and OpenGL....to the best of my knowledge.  (Although I can't seem to find a good test for this.)  I have all of my current video drivers installed.

I'm new to Ubuntu, but not entirely new to Linux...I'm certainly still a novice tho.

Any suggestions?  What have I overlooked?

---

### Post by Perfect Storm on 2006-07-13
Try copy the linux ut2004 installer to your harddisc and run it from there.

eg. to your Desktop

then:
```
cd Desktop
sudo sh <ut2004installer>

```

---

### Post by Bmbshl on 2006-07-13
Great.....that worked just fine.....now can you tell me what went wrong?  I'll know next time what to do when that happens, but I'd like to know the root cause if you can point me to documentation.  I want desperately to learn!

Thanks so much.

---

### Post by Perfect Storm on 2006-07-13
Well it's hard to tell with the information you provided, but my guess is that you didn't browse to you CD-rom player first eg: cd /media/cdrom or the better way to do it eg: sudo sh /media/cdrom/linuxinstaller.sh so it doesn't lock your CD-rom when you want to change CDs.

---

### Post by andlinux21 on 2006-07-13
I placed my CD's contents on my HD and installed it from there without a problem.

---

### Post by vem0m on 2006-07-13
better yet use a dvd version :D

---

### Post by Bmbshl on 2006-07-13
Thats a good guess **AI**, this was the first thing that I've tried installing from CD so I didn't know that I had to do that with the CD drive.    

I finally got it to install, and now I'm having trouble running it..may just uninstall and try again...I just need some time to sit down and start up the ole google search and try to figure out where I went wrong, if I can't figure it out in a couple of days I'll be back, but I want to try and do it on my own first.  Thanks again for the tip **AI**.  

_Another tip I need:_
Do I still have to use the "PlayDisc" or will it run without it?  Can I write the "PlayDisc" files to my HD and run from there?  Thanks

---

### Post by Perfect Storm on 2006-07-14
My guess you properly made the classic newbie error by hit the "start UT2004" button right after installation? ;) :) :KS 
Don't worry, uninstall it.

```
sudo sh /usr/local/games/ut2004/uninstall
cd
sudo rm -rf .ut2004

```

The first line runs the uninstaller script
Second line set you back to your home diretory (just in case)
Third line wipe your .ut2004 folder completly in your home folder.

The problem is when you hit start button right after installation (sudo sh /bla/blabla) you don't have permission to read/write the stuff in .ut2004 (when there's a dot infront of the name, it means it's hidden) due to the fact you install it globally with as sudo (superuser do). So instead after installing it exit the installation and write ut2004 in the terminal.
If this is not the case, you have to copy and paste the output of the terminal to this thread when you running ut2004 through the terminal.

By the way did you set up your graphic card?

---

### Post by Bmbshl on 2006-07-14
It works! Yes, my video card drivers are installed and seem to be working well.
[I]
My mistake:[/I]  I was trying to run it in terminal without the "sh" command.....I just sat down and looked at the file structure until it was obvious what I had done wrong. 

I need a list of all the commands and extentions, I have a RedHat book, but I'm not sure all the Ubuntu code translations are going to be the same.  Do you know of an Ubuntu book?????  (print or online)

This will all slowly come back to me, I started out on UNIX 20 years ago in college.  Windows has atrophied my brain.

Thanks for the wonderful help, **AI**, I'm glad to see that this community is strong and willing to help new users, I promise as soon as I am confident, I will give back to the community.

---

### Post by Adrian_b on 2006-07-14
For all your Bash Command needs:
[http://www.ss64.com/bash/](http://www.ss64.com/bash/)

---

### Post by Bmbshl on 2006-07-14
Hahaha.....it works, but it runs so slow you can't play it.  Time to install new video card that's been in the closet for 6 months.  I also don't have any sound.  The video I get, the sound I don't understand, I had a hard time making it work at all.  *What to do:  update my OpenAL....sound drivers.....?????*  Can you think of any other reason that it might not be working?  (This may drive me crazy before I get it to work correctly.)

**Adrain_b** thanks for the command list....will check it out and commit it to memory!

---

### Post by xeta on 2006-07-14
See if this post helps you.

[http://ubuntuforums.org/showthread.php?t=140486](http://ubuntuforums.org/showthread.php?t=140486)

---

### Post by Bmbshl on 2006-07-14
**xeta** Thanks for the suggestion, but I'm having the same problem as the last post on that thread.....I can't find anything that says:
[I]
#Prefs the users starting preferences[/I]

I'm looking in the ut2004 sh exec. file using *gedit*.  Am I in the right place or is that post refering to another file that I haven't found?  I have opened every "sh" file that I can find, and none of them contain that string or anything similar to it.  Do I need to have the playdisc in the drive?  Do I need to sacrifice a goat to a specific Linux diety?

---

