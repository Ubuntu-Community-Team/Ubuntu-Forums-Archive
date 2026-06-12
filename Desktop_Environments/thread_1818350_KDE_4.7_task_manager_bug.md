---
title: "KDE 4.7 task manager bug?"
date: 2011-08-04
forum: Desktop Environments
---

### Post by james_xxx on 2011-08-04
I recently upgraded two machines running Kubuntu 11.04 to KDE 4.7. On both machines, I am experiencing a problem in which icons in the task manager do not consistently disappear as they should, after the corresponding window is closed. When this happens, opening a new window usually seems to make the orphaned task manager icon go away.

One machine is using an Nvidia ION2 GPU & proprietary drivers, and the other uses an Intel X3150 GPU.

Is anyone else experiencing this?

Any suggestions for possible causes/solutions?

Thanks!

---

### Post by FormatSeize on 2011-08-05
Yes. I am experiencing this, but with much more tremendously horrifying things happening. When I close a window, sometimes it stays open, but the rectangle thingy in the bottom panel disappears. Sometimes the window disappears but the rectangle thingy in the bottom panel stays there. 

If I open more than one application, the rectangle thingies stack on top of each other, so if I want to use multiple applications, I'd better not minimize any of them. When I open a window, it appears, then disappears for a split second, then reappears. That's annoying. It not only happens with windows, but also context sensitive menus and drop down menus. It was driving me up the wall. 

This is without nVidia drivers. Why am I *still *without drivers? Because I can't install them. I go to runlevel 1. The nVidia driver installation tells me that I have to be in runlevel 3. So I try to go to that runlevel, and it takes me to the login screen. How dumb. Then, when I try to go to runlevel 2 to see if it'll let me install there, it just crashes. I've installed these drivers on multiple occasions, so it's not that I'm doing anything that I haven't done before. Unless KDE 4.7 requires some oddball workaround, I'm not understanding what is happening.

---

### Post by james_xxx on 2011-08-05
FormatSeize,

A few initial questions.

Why have you not just used the Nvidia drivers provided in the repositories?

Also, could you give me a few more details as to your system's specs?

---

### Post by YAFU on 2011-08-06
I have the problem you mention. My graphics card is an ATI x1250 using OpenSource drivers and I do not think the problem is related to graphics cards. I think it's a KDE bug.

---

### Post by james_xxx on 2011-08-06
YAFU,

The thing is, most people who upgraded to KDE 4.7 are not experiencing this. I have two machines that are, and one that isn't. So one thing to do at this point, is try to determine whether or not affected machines have certain details in common.

Although I do doubt that the CPU being used has much bearing on anything, I will mention that both of my machines with this problem are using Intel Atom D525 processors. Otherwise, they don't have so much in common.

Could you list some of your machine's details that might be relevant?

---

### Post by PaulW2U on 2011-08-06
I'm also seeing this in my test version of Oneiric Ocelot, a new installation of KDE 4.70 and not upgraded form KDE 4.6x. I'm posting here rather than the in OO forum as it now looks like this bug is KDE related. I'm using an ATI video card, plenty of RAM and generally Kubuntu is really fast.

If I close an application from the file menu or using a keyboard short-cut (Alt-F4) then the icon doesn't remain in the taskbar but if I close it from the 'x' or close button then the icon remains in the taskbar until something else comes along and replaces it.

So how are we all closing our applications, 'x' button, from the file menu or using a keyboard short-cut?

---

### Post by YAFU on 2011-08-06
> **james_xxx said:**
> 

Could you list some of your machine's details that might be relevant?

My machine is a PC, Asus Motherboard, AMD Athlon X2 and integrated ATI X1250.

I have two kinds of problems related to the task manager. The first is that I had mentioned in the link below:
[https://answers.launchpad.net/ubuntu/+source/kdebase-workspace/+question/167156](https://answers.launchpad.net/ubuntu/+source/kdebase-workspace/+question/167156)

The problem of launchers (Dolphin and Rekonq or Konqueror) is always reproducible on my system and I had always in Kubuntu 11.10 Oneiric Ocelot. In Natty upgrading to KDE 4.7 the problem does not exist. But if you remove the panel and add a new default panel, the problem appears.

The other problem with the task manager just happened to me a couple of times and I do not know under what conditions it occurs. When a window are closed the corresponding task in the task manager panel does not disappear. Also at that time all elements of the taskmanager are frozen and stop responding until I reopen the application.

Regards.

---

### Post by kibble on 2011-08-06
Yea, i am also getting this. I close a program down using the 'X" window button, the app closes but the task bar keeps the name and icon. If i right click the taskbar item and chose close it does nothing, but if i open amarok or kopete, which i have minimized in the systray then close them again it resets all the taskbar items.

I have an AMD phenom II cpu
4 gb or ram
Nvidia gts 250  video, using the recommended drivers from the Kubuntu repostories
Kubuntu 11.04 with upgraded kde 4.7
edit 32 bit kubuntu if that makes a difference

if you need more info let me know

---

### Post by james_xxx on 2011-08-07
PaulW2U,

What you are describing seems to exactly match what I am experiencing.

As in your case, if I close a window with the 'x' button, the associated icon frequently remains in the task bar. However, when closing a window with Alt+F4, this does not happen.

One question: What/Where is the file menu you mention? I am not sure I am familiar with this.

Thanks!

---

### Post by PaulW2U on 2011-08-07
> **james_xxx said:**
> One question: What/Where is the file menu you mention?

The file menu of the application.

I haven't found a bug report for this yet, I'll keep looking and file one if I don't come up with anything.

---

### Post by james_xxx on 2011-08-08
Well, there were two rounds of updates from the KDE backports PPA for Natty today. Not only did the first round fail to fix a thing for me, it broke even more KDE components (plasma-widget-networkmanagement, most notably).

However, I am very happy to say that the second round of updates from this PPA seems to have fixed both the problems some of us have been experiencing with the task manager, and also the network management widget broken by today's earlier updates.

YAY!!!

(Paul, I feel silly for not having realized what you meant by the file menu! Anyways, thanks for your input on all of this.)

NOTE:
Sadly, I have to rescind my claim that the second batch of updates fixed the task manager. It did not. :-(

---

### Post by PaulW2U on 2011-08-09
James, I've now submitted a bug report to KDE. It probably needs some more information added to it so if anyone cares to add some I'd be most grateful.

See [https://bugs.kde.org/show_bug.cgi?id=279769](https://bugs.kde.org/show_bug.cgi?id=279769).

Interestingly I found a reference to a similar bug with KDE 4.2 I think it was. That bug was of course fixed!

---

### Post by viziouz on 2011-08-13
There is already reported bug about that problem. I had this issue with Kubuntu 11.04 after switching to KDE 4.7 from 4.6. I also tried to change my distro to openSUSE 11.4 and then made KDE update to 4.7 and got same issue. It's looks like KDE release bug and it's not fixed neighter in 4.7.2 version. Changing standard taskbar to "smooth taskbar" gave same results and it's not widget bug. Please vote this bug at following link.

[https://bugs.kde.org/show_bug.cgi?id=275469]("https://bugs.kde.org/show_bug.cgi?id=275469")

I'm using 64bit distros and have Intel 4 mobile graphic driver.
Cheers.

---

### Post by PaulW2U on 2011-08-14
> **viziouz said:**
> There is already reported bug about that problem. I had this issue with Kubuntu 11.04 after switching to KDE 4.7 from 4.6. I also tried to change my distro to openSUSE 11.4 and then made KDE update to 4.7 and got same issue. It's looks like KDE release bug and it's not fixed neighter in 4.7.2 version.

viziouz, there is obviously some activity on the KDE bug reporting site so I hope that this bug will be fixed soon. 

It seems that for some people the bug always occurs no matter how an application is closed but for others, like myself, it only occurs when an application is closed using the 'x' button. I think I made a new bug report because there was no mention of how applications were being closed in bug #275469 and the first report implied that this always happened when applications were closed. For me, this is not the case. 

Anyway, I have now marked my bug report as a duplicate of bug #275469.

---

### Post by james_xxx on 2011-09-26
I just installed KDE SC 4.7.1 from the Kubuntu Backports PPA, with the not-too-high hopes that bugs like this one might have been fixed.

At least for me, this problem is as bad as ever.

I'd be curious to know if this update improved anything for anyone else.

So far, I have a major disliking for KDE 4.7, but maybe over time that will change.

(BTW, it does appear that this bug is quickly moving up the ranks in the list of most hated KDE bugs.)

---

### Post by schnelle on 2011-09-26
Please if you can vote for this bug.

[https://bugs.kde.org/show_bug.cgi?id=275469](https://bugs.kde.org/show_bug.cgi?id=275469)

It is very annoying "in your face" bug. I cannot believe that such bug isn't fixed already.

Personally, it annoys me so much that I wont use 4.7 until this is fixed.

---

### Post by jpelorat on 2011-10-22
I've been reading this thread and I have to share my frustration. Since I got KDE 4.7 from the PPA on Kubuntu 11.04 I've been checking almost every day for a fix.... DA** NOTHING has happened...

---

### Post by Sam Azer on 2011-11-16
Ditto! :(

---

### Post by james_xxx on 2011-12-15
I am beginning to wonder if this problem will ever go away.

KDE is increasingly seeming (to me, at least) like a DE that is less than half-baked (and perpetually so).

---

### Post by drmrgd on 2011-12-15
Interesting!  I get this pretty randomly too.  Sometimes I can go a day or more without seeing it, and then sometimes it happens all of the time for days on end.  Since it was so random, had a heck of a time figuring out how exactly to file a bug report on it.  Glad it's being looked into (again!).

---

### Post by schnelle on 2012-02-05
This wasn't KDE bug after all. It was Qt bug and now it is fixed. You can update your Qt from this ppa: [https://launchpad.net/~hrvojes/+archive/qt](https://launchpad.net/~hrvojes/+archive/qt)

```
sudo apt-add-repository ppa:hrvojes/qt
sudo apt-get update
sudo apt-get dist-upgrade
```

---

### Post by james_xxx on 2012-03-12
I just added this PPA, but dist-upgrade does not do anything. 

Is the patch only available to people still using KDE 4.7?

(I'm using Oneiric.)

---

### Post by schnelle on 2012-03-13
> **james_xxx said:**
> I just added this PPA, but dist-upgrade does not do anything. 

Is the patch only available to people still using KDE 4.7?

(I'm using Oneiric.)

Yes, for oneiric qt 4.7.4 is patched.

For precise qt 4.8 is patched.

p.s. If anybody wants qt patched in official repositories, please come to kubuntu-devel irc channel on freenode and ask kubuntu devs to patch it. I am asking them from time to time but it seems that it's not their top priority right now. Bug report is here: [https://bugs.launchpad.net/ubuntu/+source/qt4-x11/+bug/911733](https://bugs.launchpad.net/ubuntu/+source/qt4-x11/+bug/911733)

---

### Post by anEarthCitizen on 2012-04-20
I have this too.

Ubuntu 11.10 (upgraded from 11.04).
KDE 4.7.4

---

### Post by schnelle on 2012-04-21
> **anEarthCitizen said:**
> I have this too.

Ubuntu 11.10 (upgraded from 11.04).
KDE 4.7.4

```
sudo apt-add-repository ppa:hrvojes/qt
sudo apt-get update
sudo apt-get dist-upgrade
```

Reboot and bug is gone ;)

---

### Post by zerubbabel on 2012-08-27
> **schnelle said:**
> ```
sudo apt-add-repository ppa:hrvojes/qt
sudo apt-get update
sudo apt-get dist-upgrade
```

Reboot and bug is gone ;)

Perhaps something has changed since this was posted. When I try to add the repository, I get:

Cannot access PPA ([https://launchpad.net/api/1.0/~hrvojes/+archive/qt](https://launchpad.net/api/1.0/~hrvojes/+archive/qt)) to get PPA information, please check your internet connection.

(My Internet connection is fine.)
I'm running the latest Kubuntu 12.04 (64-bit) with all system updates applied. I still get superimposed icons in the task manager.

---

### Post by schnelle on 2012-08-27
> **zerubbabel said:**
> Perhaps something has changed since this was posted. When I try to add the repository, I get:

Cannot access PPA ([https://launchpad.net/api/1.0/~hrvojes/+archive/qt](https://launchpad.net/api/1.0/~hrvojes/+archive/qt)) to get PPA information, please check your internet connection.

(My Internet connection is fine.)
I'm running the latest Kubuntu 12.04 (64-bit) with all system updates applied. I still get superimposed icons in the task manager.

That ppa is for Kubuntu 11.10 not 12.04. 

In 12.04 this bug is fixed. Check which version of Qt do you have: ```
dolphin --version
```
It should return
```

**Qt: 4.8.1**
KDE Development Platform: 4.8.5 (4.8.5)
Dolphin: 2.0

```
Bug is fixed in Qt 4.8.1 so if you running that version of Qt you shouldn't experience this "ghost taskbar" bug anymore. 
For me it is 100% fixed. I cannot reproduce it anymore.

---

### Post by zerubbabel on 2012-08-27
"dolphin --version" returns:

Qt: 4.8.1
KDE Development Platform: 4.8.4 (4.8.4)
Dolphin: 2.0

But here is a snapshot that shows the Task Manager dysfunction.

---

### Post by drmrgd on 2012-08-27
> **schnelle said:**
> That ppa is for Kubuntu 11.10 not 12.04. 

In 12.04 this bug is fixed. Check which version of Qt do you have: ```
dolphin --version
```It should return
```

**Qt: 4.8.1**
KDE Development Platform: 4.8.5 (4.8.5)
Dolphin: 2.0

```Bug is fixed in Qt 4.8.1 so if you running that version of Qt you shouldn't experience this "ghost taskbar" bug anymore. 
For me it is 100% fixed. I cannot reproduce it anymore.

+1 to this.

I have not had this problem since updating to 12.04.  Based on the poster's description, I'm wondering if it's the same bug or something else.  The elements in the taskbar never got superimposed.  They just failed to disappear after an application was closed.

---

### Post by drmrgd on 2012-08-27
> **zerubbabel said:**
> "dolphin --version" returns:

Qt: 4.8.1
KDE Development Platform: 4.8.4 (4.8.4)
Dolphin: 2.0

But here is a snapshot that shows the Task Manager dysfunction.

Glad you took a screenshot (meant to ask and forgot!).  I don't have a solution for you.  But, I can say that the problem we had was much different that what I'm seeing in that picture.

---

### Post by zerubbabel on 2012-08-27
Why is my KDE 4.8.4 and yours is 4.8.5? Actually, I installed KDE 4.9 from the backports repository and the problem is still there.

(Actually, I may have spoken too soon... KDE 4.9 Seems to be behaving itself so far...)

---

### Post by zerubbabel on 2012-08-27
Cancel that... This screen shot shows that the task manager dysfunction persists in KDE 4.9

---

### Post by PaulW2U on 2012-08-27
> **zerubbabel said:**
> Cancel that... This screen shot shows that the task manager dysfunction persists in KDE 4.9

That is not the bug that we were all seeing when this thread was opened. What you are seeing is something new and a _new_ bug report needs to be opened if one hasn't been already.

I'm also running KDE 4.9 but haven't see that problem here. I'm running the development version of Kubuntu 12.10 by the way.

---

### Post by oldos2er on 2012-08-27
Old thread closed. zerubbabel, if you still need help please start a new thread.

---

