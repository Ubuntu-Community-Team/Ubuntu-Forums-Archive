---
title: "ubuntu tweak error"
date: 2009-03-08
forum: General Help
---

### Post by 16sinker on 2009-03-08
Good morning everyone. I need some help launching the latest version of Ubuntu Tweak. I have downloaded and installed the app. It appears in applications/system tools, but when I launch it I get: Error. Failed to execute child process "/home/bofus66/.ubuntu-tweak/Contents-i386"(permission denied.) Can anyone help?;)

---

### Post by 16sinker on 2009-03-08
Is there anybody out there?

---

### Post by 16sinker on 2009-03-09
I don"t want to seem anxious, but I really had expected a reply to this query by now. Please inform me if I have posted incorrectly or have not provided enough info. This is not a serious problem, as it doesn't affect anything but the launch of ubuntu tweak via Applications/System Tools.

---

### Post by speedwell68 on 2009-03-09
Which version of Ubuntu Tweak are you running?  What version of Ubuntu are you running?

---

### Post by 16sinker on 2009-03-09
That would be Ubuntu 8.10 and Ubuntu Tweak 4.6.

---

### Post by 16sinker on 2009-03-10
What kind of a "community" forum is this? Am I at fault? Am I posting in the wrong section of the forum? I would really appreciate some help. Thanks.

---

### Post by Peasantoid on 2009-03-10
You seem to be rather desperate, so I just thought I'd jump in.

See, even on a big forum like this, people can't be on all the time. It's like 9:45 PM where I live &#8212; almost everyone has gone to sleep by now.

Anyway. Run the following in a terminal and post the results:
```
stat /home/bofus66/.ubuntu-tweak/Contents-i386
```

---

### Post by 16sinker on 2009-03-10
deb [http://ppa.launchpad.net/tualatrix/ubuntu](http://ppa.launchpad.net/tualatrix/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/tualatrix/ubuntu](http://ppa.launchpad.net/tualatrix/ubuntu) intrepid main  
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid restricted universe multiverse main
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-backports restricted universe multiverse main
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-proposed restricted universe multiverse main
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-security restricted universe multiverse main
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-updates restricted main multiverse universe

---

### Post by Peasantoid on 2009-03-10
Eh, what?

---

### Post by 16sinker on 2009-03-10
Sorry, wrong output. This is the output of stat /home/bofus66/ .ubuntu-tweak/Contents-i386.
bofus66@ubuntudell:~$ stat /home/bofus66/.ubuntu-tweak/Contents-i386
  File: `/home/bofus66/.ubuntu-tweak/Contents-i386'
  Size: 27072694  	Blocks: 52944      IO Block: 4096   regular file
Device: 801h/2049d	Inode: 959118      Links: 1
Access: (0400/-r--------)  Uid: ( 1000/ bofus66)   Gid: ( 1000/ bofus66)
Access: 2009-02-19 20:21:53.000000000 -0600
Modify: 2009-02-19 17:04:33.000000000 -0600
Change: 2009-02-19 17:04:33.000000000 -0600
bofus66@ubuntudell:~sorry to keep you up.

---

### Post by Peasantoid on 2009-03-10
Ahh, I thought it would be something like that. See where it says "-r--------"? That means you don't have permission to execute Contents-i386. Run the following command and you should be fine:
```
chmod +x /home/bofus66/.ubuntu-tweak/Contents-i386
```
(This sets the "execute bit", the little piece of data that tells Ubuntu whether you're allowed to run the file.)

---

### Post by 16sinker on 2009-03-10
I ran your command in terminal and I no longer get the error, but the app. won't open. I did apt-get update and apt-get dist-upgrade to no effect

---

### Post by Peasantoid on 2009-03-10
Huh, that's weird. Try running it from Terminal?
```
/home/bofus66/.ubuntu-tweak/Contents-i386
```

---

### Post by 16sinker on 2009-03-10
Whow!!! Your command /home /bofus66/.ubuntu-tweak/Contents-i386 just ran 116,378 lines of code. However, Ubuntu Tweak still won't open. This has taken 20 to 30 minutes and I don,t expect you to reply as it is late, even in Kentucky. I do hope you will reply ASAP. i appreciate your help and hope to hear from you tomorrow. Thank you Peasantoid.

---

### Post by Peasantoid on 2009-03-11
Heh, don't mention it.

I suppose you can try doing a clean reinstall:
```
sudo apt-get purge ubuntu-tweak
sudo apt-get clean
sudo apt-get install ubuntu-tweak
```

---

### Post by 16sinker on 2009-03-11
this is the output of sudo apt-get install ubuntu-tweak

bofus66@ubuntudell:~$ sudo apt-get install ubuntu-tweak
[sudo] password for bofus66: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  ubuntu-tweak
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 1058kB of archives.
After this operation, 4092kB of additional disk space will be used.
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main ubuntu-tweak 0.4.6-1~intrepid1 [1058kB]
Fetched 1058kB in 5s (182kB/s)        
Selecting previously deselected package ubuntu-tweak.
(Reading database ... 168194 files and directories currently installed.)
Unpacking ubuntu-tweak (from .../ubuntu-tweak_0.4.6-1~intrepid1_all.deb) ...
Setting up ubuntu-tweak (0.4.6-1~intrepid1) ...
bofus66@ubuntudell:~$ 

I tried to launch from System Tools but it wouldn't open.

---

### Post by whitethorn on 2009-03-11
I don't really know if this will work, but you might give it a try.  First we're going to move the ubuntu-tweak folder in your homefolder.  Then try to start ubuntu-tweak again.  Usually the .folders contain the settings you've changed as you user when you use a program. so

mv ~/.ubuntu-tweak ~/.ubuntu-tweak-bak

Then try to start the program.  See if that works.  If not then you can move the folder back by using

mv ~/.ubuntu-tweak-bak ~/.ubuntu-tweak

---

### Post by 16sinker on 2009-03-11
After both commands I now get the error:failed to execute child process. It's weird that I don't have the Ubuntu Tweak icon in system, just the launcher icon. That's the little springy platform.

---

### Post by 16sinker on 2009-03-11
May be that I need help with launching the app because in main menu and applications/sys. tools I have only the launcher icon and not the green Ubuntu Tweak icon. ?????

---

### Post by 16sinker on 2009-03-11
stat /home/bofus66/.ubuntu-tweak/Contents-i386 now returns "no such file or directory."

---

### Post by Peasantoid on 2009-03-11
Are you *sure* that's what you're supposed to be executing? Can you type "ubuntu-tweak" in Terminal to launch the application?

---

### Post by Peasantoid on 2009-03-11
Are you *sure* that's what you're supposed to be executing? Can you type "ubuntu-tweak" in Terminal to launch the application?

[edit] Gah, sorry, my connection died and I double-posted by accident.

---

### Post by 16sinker on 2009-03-11
If you mean execute ubuntu-tweak in the terminal without the prefis "sudo" the answer is no.

---

### Post by 16sinker on 2009-03-11
The output of the command "ubuntu-tweak" is "command not found."

---

### Post by Peasantoid on 2009-03-12
That's odd...the version I just installed is located at /usr/bin/ubuntu-tweak. (I used the downloadable .deb file.)

---

### Post by 16sinker on 2009-03-12
At this point I've done an apt-get purge ubuntu-tweak and an apt=get clean. Perhaps I'll download the.deb and will report back later as I have to go to work.

---

### Post by 16sinker on 2009-03-12
Good news I think. I got the .deb file , installed it. It now resides in /usr/bin/ubuntu-tweak and I am able to launch in terminal with the command ubuntu-tweak, however I get a warning in terminal as it launches the app. The warning follows:
bofus66@ubuntudell:~$ ubuntu-tweak
/usr/lib/python2.5/site-packages/apt/__init__.py:18: FutureWarning: apt API not stable yet
  warnings.warn("apt API not stable yet", FutureWarning)
Reading package lists: Done
Reading state information: Done
Reading state information: Done
Reading state information: Done
What do you think about this?

---

### Post by Peasantoid on 2009-03-12
Yeah, I get that one too. I think you can safely ignore it. Someone probably just decided to err on the side of caution.

---

### Post by 16sinker on 2009-03-12
Well that's good news. I thank you for helping me with this problem Peasantoid. I'll call this solved! and end this thread.

---

