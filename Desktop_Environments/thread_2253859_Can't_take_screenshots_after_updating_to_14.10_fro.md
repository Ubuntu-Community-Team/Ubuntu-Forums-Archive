---
title: "Can't take screenshots after updating to 14.10 from 14.04"
date: 2014-11-23
forum: Desktop Environments
---

### Post by JoaoMachado on 2014-11-23
Only screenshot that works is the first one after logging in. After that, the same image is what is taken every time.

Someone else seems to have this issue: [http://askubuntu.com/questions/549455/cant-take-screenshots-after-updating-to-14-10-from-14-04](http://askubuntu.com/questions/549455/cant-take-screenshots-after-updating-to-14-10-from-14-04)

I use Shutter but it turns out that it seems to be system related because uninstalling it and using Prnt Scrn has the same issue.

System: Dell D630 Laptop with 2.6Ghz, 4gig memory and 250GB SSD. Video: Intel 965GM

Anyone have an idea?

Joao

---

### Post by carl4926 on 2014-11-23
Myself, I don't have this issue

Create and test a new user account and report back

---

### Post by JoaoMachado on 2014-11-23
So I have a second drive on my laptop that I use for automatic backups. I also have a small partition with a second Ubuntu install so that if anything goes wrong with my main drive, I can just boot to my second drive.
 I upgraded ubuntu 14.04 on the second drive to 14.10 and I have the same issue. I am going to try to do a fresh install on the second drive to see if it changes and will report. Here is what I get...
[IMG]http://www.drupub.com/tmp/Ubuntu14-10_Screenshot.png[/IMG]

---

### Post by JoaoMachado on 2014-11-24
Well, it appears to be something in Ubuntu. A fresh install of Ubuntu 14.10 did not help in any way. It turns out that screenshots of the Desktop work perfectly fine. But if an application is open, it just keeps snapping the background of the Desktop.  Very odd! The results are the same regardless which tool I use to take screenshots or what application is open. Sounds like a bug!!

---

### Post by michael-chapman on 2014-11-25
I too am having this issue.  It is definitely the same issue as JoaoMachado  and Ubuntu 14..10 issue.  exactly the same issue sis seen with  Shutter  as well as snapshot.


If I take a snapshot  and the run up shutter and try to take a difference screen shot the image taken with snapshot is the image that shutter offers up to be saved.

*Further I have created  a new admin account  and a new standard  user account and both have the same issue ....*

---

### Post by JoaoMachado on 2014-11-25
One more insight, from the initial login, the very first screen grab WILL work on any window...but afterwards the image of the first screen grab taken will always show up, sometimes only partially other times the entire image.

I had no idea how much I depended on this feature!

I submitted a bug report to Ubuntu using the Gnome-Screenshot-tool with hopes that Ubuntu will fix this issue.

---

### Post by JoaoMachado on 2014-11-26
Well, it gets worst.. trying to record the Desktop using RecordMyDesktop app only captures the previous screen grabs.... Ubuntu 14.10 is just riddled with bugs. Had to update MLT manually from a third party PPA because UBuntu has not pushed the bug fix. Cannot generate videos  with sound.

I think it is best to revert to Ubuntu 14.04...

---

### Post by andrew.46 on 2014-11-27
Perhaps use Gimp or even scrot if you don't mind the commandline...

---

### Post by JoaoMachado on 2015-01-12
> **andrew.46 said:**
> Perhaps use Gimp or even scrot if you don't mind the commandline...

This is what heppens when you use Gimp to capture a screenshot....This is definetly a system wide issue..


[ATTACH=CONFIG]259212[/ATTACH]

---

### Post by JoaoMachado on 2015-01-13
Just verified that this is an ubuntu Desktop issue.. Created new user, same issue. 
Installed Ubuntu Mate Desktop along side Ubuntu Unity, no issue whatsoever!

I have no idea how to track this down!

---

