---
title: "HUNDREDS of freezing/kernel-panic threads: consolidate &amp; fix?"
date: 2008-12-15
forum: General Help
---

### Post by 2CV67 on 2008-12-15
There are several hundred threads on the Absolute Beginners & General Help forums complaining about Kernel Panics with Hardy & Intrepid, which didn't exist with the same hardware & Gutsy.

Keywords are Kernel Panic, Freeze, Freezing, Locks up, Caps-Lock & Scroll-lock flashing etc.

Almost none of these several hundred threads are marked Solved even though this problem has been around for a year.
The 'Solved' solutions don't work for others.

There are thousands of more-or-less competent users making all kinds of tests & suggestions.
Reminds me of the million monkeys trying to write Shakespear...

Many users have had to give up on Ubuntu because frequent hard lockups make the system worthless.

This is the first time since I joined the Linux community (which I really appreciate) that I have missed some kind of centralized organization which would have recognized this as a serious problem needing allocation of expert resources & re-prioritizing of effort from development luxuries to fixing a sinking ship.

Is there no way to run this up the organization?

Of course I know about Bug Reports, but there are plenty of those already.

Please don't think I am grousing; I am concerned for Ubuntu, but incapable of helping.

---

### Post by sdennie on 2008-12-15
> **2CV67 said:**
> There are several hundred threads on the Absolute Beginners & General Help forums complaining about Kernel Panics with Hardy & Intrepid, which didn't exist with the same hardware & Gutsy.

Keywords are Kernel Panic, Freeze, Freezing, Locks up, Caps-Lock & Scroll-lock flashing etc.


Several hundred may be a slight exaggeration.

> 
This is the first time since I joined the Linux community (which I really appreciate) that I have missed some kind of centralized organization which would have recognized this as a serious problem needing allocation of expert resources & re-prioritizing of effort from development luxuries to fixing a sinking ship.


I think you are assuming that these problems are very widespread.  They are in fact very limited and, while those affected by it are sure to consider it the highest possible priority, having a limited number of users receive kernel panics does not constitute a sinking ship.  While it's very unfortunate that some people are receiving kernel panics, the best course of action is to provide as much information as possible to the people working on the kernel and help them to diagnose the bug(s).

> 
Of course I know about Bug Reports, but there are plenty of those already.

Please don't think I am grousing; I am concerned for Ubuntu, but incapable of helping.

I disagree.  You are very capable of helping by providing information on the bug reports that affect you.  It can take time to fix bugs but, the more information the people doing the fixing have, the more likely they are to be able to fix them.

---

### Post by 2CV67 on 2008-12-15
> **vor said:**
> Several hundred may be a slight exaggeration.

If you run a search for threads with freez* in the title in all open forums here, it returns 250 different threads with activity in the last 3 weeks.

See sample 2 pages out of 10 search results attached.

Obviously, not all of these are kernel panics & some are typical noobie slip-ups, but also obviously it misses threads with only kernel-panic or lock-up or whatever in the title.

I don't think several hundred is any kind of exaggeration.

Did you check?

Please don't read any kind of aggressivity into this post & excuse me for any factual errors.

Thanks!

---

### Post by sdennie on 2008-12-15
I don't doubt that words like "freeze" would appear many, many times in a search but, you seem to be implying that most (or at least many) of these threads are related and describe a common bug that, if fixed, would greatly reduce the number of threads created that match the keyword "freeze".  That doesn't appear to be the case to me.  Yes, some of the threads are related (or the same) and fixing one might fix the other but, I don't think there is a single bug fix that is going to make the word "freeze" become less commonly used on an OS support forum.

As an example, I would imagine that search for "nvidia problems" would turn up hundreds of threads as well.  That doesn't mean that they are all describing a common bug.

---

### Post by Izek on 2008-12-15
vor is right, it's like a cure for cancer.

---

### Post by bodhi.zazen on 2008-12-15
> **2CV67 said:**
> There are several hundred threads on the Absolute Beginners & General Help forums complaining about Kernel Panics with Hardy & Intrepid, which didn't exist with the same hardware & Gutsy.

Keywords are Kernel Panic, Freeze, Freezing, Locks up, Caps-Lock & Scroll-lock flashing etc.

Almost none of these several hundred threads are marked Solved even though this problem has been around for a year.
The 'Solved' solutions don't work for others.

There are thousands of more-or-less competent users making all kinds of tests & suggestions.
Reminds me of the million monkeys trying to write Shakespear...

Many users have had to give up on Ubuntu because frequent hard lockups make the system worthless.

This is the first time since I joined the Linux community (which I really appreciate) that I have missed some kind of centralized organization which would have recognized this as a serious problem needing allocation of expert resources & re-prioritizing of effort from development luxuries to fixing a sinking ship.

Is there no way to run this up the organization?

Of course I know about Bug Reports, but there are plenty of those already.

Please don't think I am grousing; I am concerned for Ubuntu, but incapable of helping.

The mechanism for addressing major bugs that affect hundreds or thousand of users is via Bug reports on Launchpad.

What do "Kernel Panic, Freeze, Freezing, Locks up, Caps-Lock & Scroll-lock flashing" have in common ?

A lot of problems in these categories have to do with hardware and can have diverse causes ranging from a bad (CD) burn to trying to run in incompatible hardware. Kernel panics can range from someone trying to compile a custom kernel, problems with encryption, problems with initrd, problems in grub configuration, etc.

These forums are quite active and we have a large number of members. I do not think you can take a listing of threads under such general and diverse topics such as "Kernel Panic, Freeze, Freezing, Locks up, Caps-Lock & Scroll-lock flashing" and make a broad sweeping conclusion that there is a problem with Ubuntu, or bug reports.

Why do not not do a search on one topic, kernel panic. Take the top  50 threads, read them, and tell us what the 1 common problem is. Or did you find it was a range of issues on a range of hardware ? 

How many on those issues were reported to Launchpad ? How many are solved ?

Thanks.

---

### Post by TheMaxxus on 2008-12-15
What might be better is a guide on things to try and logs to gather to make that launchpad report.  

I have done some research into this issue because I am affected by it.  I have to stick with gutsy until I can narrow down the problem.  It seems to me that there are 3 types of freezes that I have commonly seen in pleas for help. 1) Complete hard-lock where the system doesn't respond to any key combination (a+c+bksp, a+sr+reisub, etc..), which is the problem I have.  2) Complete hard-lock but the mouse does move around the screen, still have to hit the reset button on this one.  And 3) Complete hard-lock with the status lights flashing on the keyboard.  None of the 3 types of hard-lock ever produces anything valuable in the syslogs.  I have experienced 2 and 3 before in my various testings to narrow down the problem but only once each. 

I would love to open a launchpad bug, but what would I say?  My system hard-locks?  Not very helpful.  Tonight, I'm going to start ripping hardware (NIC, sound card, video card) out and see if removing them will solve the problem.  But what if it doesn't?  Does that mean its my remaining hardware (motherboard, memory, cpu)?  Or maybe it's a subtle change to the kernel that only affects my chipset?  How am I to know?

---

### Post by oxman on 2008-12-23
I must confess that this one has me stumped. I have been using linux since Red Hat 5.xx.
Never have I been in this type of situation. Never. I have always patiently worked things out. But now my main computer has been completely unusable for many months with ubuntu hardy or intrepid. There it sits...silent. I upgraded from dapper and now I am unable to use the computer. I have searched and searched to no avail and tried multiple solutions to no avail.

I hesitate to go back to dapper only because the software applications that compelled me to upgrade in the first place will not function on dapper.

As seen in my signature my Asus MB might be suspect, my nvidia card might be  suspect and I feel like I am floundering around in the dark. Very frustrating. I have filed a bug report to no avail. 

The several threads I am subscribed to have not had a working solution for me.

I think the "consolidate and fix" idea is a good one. Make alist of the main symptoms and catagorize them so that we can narrow these things down. It is the confusion of multiple problems and responses that makes finding an answer very difficult if not impossible.

I am not ungrateful for the hard work that has been done by the linux community or ubuntu folks specifically... I just can't use my computer and I need to.

---

### Post by 2CV67 on 2008-12-24
Izek said:
"vor is right, it's like a cure for cancer."

I agree.
I don't imagine there is one simple cause & one simple fix for all Linux kernel panics, and even less for general freezes.
But if we waited for all the individual doctors dealing with all the individual cancer patients to cure cancer, we would wait for ever.
The improvements come from higher-level activities (not more noble, but higher up the problem-solving hierarchy) which look for patterns, group similar symptoms, pore over statistics, propose & analyse tests, build databanks, provide funds…
This is what is missing here & what I feel is necessary in this case.

Bodi.zazen said:
"The mechanism for addressing major bugs that affect hundreds or thousand of users is via Bug reports on Launchpad."

I agree.
This is a beautiful system, which I applaud & use.
I have raised a bug report on my own case (unfortunately with a now-inappropriate title, which I regret but can't change: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/308300](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/308300)) but I think this has been swept under the carpet & is unlikely to produce any positive input to the community, even though I am able to turn my kernel panics on & off at will with backports modules.
The purpose of this thread is not to fix my particular problem, but to call for higher-level action.

Bodi.zazen also said:
"A lot of problems in these categories have to do with hardware and can have diverse causes ranging from a bad (CD) burn to trying to run in incompatible hardware. Kernel panics can range from someone trying to compile a custom kernel, problems with encryption, problems with initrd, problems in grub configuration, etc."

That is certainly true.
I think the advanced users who are having panics after compiling custom kernels etc are probably not too much of a problem, & can help each other in forums.
What I see in many threads, is "ordinary" users doing nothing special and finding themselves with Linux which fails completely to the point where it can no longer be used.
And finding no help after a year.
In spite of forums, bug reports, Google etc.
Particularly users whose Ubuntu was OK in Dapper or Gutsy & is useless in Hardy or Intrepid.
It seems very probable that some new content details in recent kernels are less robust than previous versions & I would have thought (but am incompetent to assert) that tracking down & correcting these probably few items could make Ubuntu viable again for a lot of people.


Bodi.zazen also said:
'What do "Kernel Panic, Freeze, Freezing, Locks up, Caps-Lock & Scroll-lock flashing" have in common ?'

Ah! I wish I knew! (apart from dissatisfied users & the ultimate admission of defeat of the O.S.)
If I was a software expert instead of a mechanical engineer, I could probably start to sketch out a 'tree' of possible root causes, which would probably have only 3 or 4 basic-level causes, each with several possible sub-causes etc etc to end up with hundreds of potential triggers.
If somebody could provide such an analysis, then maybe many good-hearted users (including me) could start to check off their yes/no's or run appropriate searches or logs or ???

An OS which can have repeated total failures without leaving any useable trace in logs seems oddly fragile.

---

### Post by imtheguido on 2008-12-24
I had this exact same issue with mine, and after 3 days and a total of 10 hours of sleep I was finally able to fix it by removing my old wireless card simply on a "hunch" from a wide spread idea of problems with wireless cards causing this to happen. I got incredibly lucky. I've had Linux maybe 2 weeks now. Awesome system. ubuntu 8.10. Wonderful, love everything about it. But I know jack squat about the system or how to understand the way it works.

I have no idea how to file a bug report, and unless I was given some sort of exact directions, I probably wouldn't be able to figure it out myself. Hell, I had to have someone take me through step by step directions on how to install my first program. I have to look up every command I want to use to get what I want done. I spend hours a day on forums and searching the web to see if what I want to do is even possible.

My point is, there are LOTS and LOTS of people out there who have absolutely NO idea what they are doing or getting themselves into when they install a linux based system, and many dont have the patience or the gusto to go through and solve any problems they run into themselves because they are used to funded companies making it work perfectly out of the box, and then walk them through every step. If I hadn't gone with that "hunch" or it wouldn't have worked, I would have left ubuntu, hell I almost did because I couldn't figure out how to get the base "from install" system video drivers back after trying to update to the newest radeon drivers. Something like this, many times I am sure you DONT hear about because they have no idea what they are doing, and give up on the best OS they have ever come across, because they don't know where to go about help and have no idea what they are doing in the first place.

2 cents done. *nod*

---

### Post by bodhi.zazen on 2008-12-24
> **imtheguido said:**
> I had this exact same issue with mine, and after 3 days and a total of 10 hours of sleep I was finally able to fix it by removing my old wireless card simply on a "hunch" from a wide spread idea of problems with wireless cards causing this to happen. I got incredibly lucky. I've had Linux maybe 2 weeks now. Awesome system. ubuntu 8.10. Wonderful, love everything about it. But I know jack squat about the system or how to understand the way it works.

I have no idea how to file a bug report, and unless I was given some sort of exact directions, I probably wouldn't be able to figure it out myself. Hell, I had to have someone take me through step by step directions on how to install my first program. I have to look up every command I want to use to get what I want done. I spend hours a day on forums and searching the web to see if what I want to do is even possible.

My point is, there are LOTS and LOTS of people out there who have absolutely NO idea what they are doing or getting themselves into when they install a linux based system, and many dont have the patience or the gusto to go through and solve any problems they run into themselves because they are used to funded companies making it work perfectly out of the box, and then walk them through every step. If I hadn't gone with that "hunch" or it wouldn't have worked, I would have left ubuntu, hell I almost did because I couldn't figure out how to get the base "from install" system video drivers back after trying to update to the newest radeon drivers. Something like this, many times I am sure you DONT hear about because they have no idea what they are doing, and give up on the best OS they have ever come across, because they don't know where to go about help and have no idea what they are doing in the first place.

2 cents done. *nod*

I understand what you are saying, and more important so does Microsoft.

You can now purchase computers with Ubuntu pre-installed.

Just for comparison, try buying a system form say Dell with Ubuntu pre-installed. 

First - Everything will work out of the box, just like Windows.

Second, try downloading and installing Windows.

Now compare apples to apples and oranges to oranges.

Pre-installed systems "just work", Installing an OS for yourself takes some effort.

IMO the "solution" is to break Microsoft's monopoly and allow choice when purchasing a computer. This also includes requiring hard ware manufacturers to provide Linux drivers for their hardware (and not just windows drivers).

In the mean time, this is what the Ubuntu forums are for, we have many experts who will help you. Please keep in mind we are volunteers here, so be sure to thank the ones who helped you and give back to the community if you can.

---

### Post by oxman on 2008-12-24
> **bodhi.zazen said:**
> 
You can now purchase computers with Ubuntu pre-installed.

Pre-installed systems "just work", Installing an OS for yourself takes some effort.

If I may interject into the dialog???
I have no problem installing the OS for myself. As mentioned earlier I have been doing this stuff the hard way since 1996 in spite of not being a pro. I enjoy learning and mastering my system. The issues with Hardy have completely blindsided me. I have been combing the forums for months to no avail. I'm not new to this and I am willing to work on it. BUT why such an awful screw up all of a sudden; no warnings, no heads up, just radical changes to the OS that make my system unusable with no apparent solution in sight.
Then to have so many complaints on the forums that finding a solution makes you feel like you are wallowing in a sea of confusion.
Hence,2CV67 has suggested consolidating and sorting. Not even launchpad does that. 
> **bodhi.zazen said:**
> 
In the mean time, this is what the Ubuntu forums are for, we have many experts who will help you. Please keep in mind we are volunteers here, so be sure to thank the ones who helped you and give back to the community if you can.
Am I being redundant? If you are asking me to be patient and grateful, no problem. But I have been trying to use my system since May of 2008 without success. To complicate matters, I am on dialup in the middle of Umpqua National Forest. Eternal download times to experiment with solutions that may or may not work and haven't to date. It seems that the less fortunate are being left in the dust the same way microsoft leaves us. The culprit in this case though is exponential developments of the OS that are having ill effects on MANY computers with few orderly answers for us who would seek them. What do you suggest OTHER than the above quote?

---

### Post by bodhi.zazen on 2008-12-24
> **oxman said:**
> What do you suggest OTHER than the above quote?

I suggest you start a thread asking for help. Be sure to include as many details as you can including your hardware (cpu, hard drive, etc) and some description of the problem you are having, error messages, and what you have tried to fix the problem. The more details the better.

An alternate to that is always Google and / or launchpad.

Simply stating that Ubuntu is somehow broken on this thread does very little to solve your problem. In a similar vein, how does it help you if I tell you Ubuntu works for me or that I think Ubuntu works for most people.

---

### Post by DrMilo on 2009-01-04
What is disappointing for me about this issue is that it would seem that Ubuntu (Hardy) can get into a situation where there's no 'escape hatch'. If I could force a log out with Control-Alt-Backspace, or something like that, I wouldn't be half as concerned. It seems to me that there must be a very fundamental flaw here. An OS should always be listening for a command like that, no matter what. If it's hardware that could be specifically identified I'd just go buy it but I'm not into playing hardware swap without any direction to go in. 

Once I plugged in a USB stick and got the freeze, so maybe it's USB somehow. But where does that leave me? I can't stop using USB devices and I doubt that anyone else can either. At any rate I have used that same stick for months and the lock up only happened that one time. Putting a video on pause in VLC seems  also to have something to do with it but that's hardly specific, especially when, again, it doesn't happen consistently. 

What I do know is that it's Hardy somehow, this never happened with Dapper. And I hear that Intrepid does it too, so I'm reluctant to go through a major upgrade unless that I know that it will make a difference.

I love Ubuntu and it would take a much bigger concern than this to get me to stop using it but if it's true that this same problem carries over to a succeeding distro then Ubuntu has a flaw that will inhibit its adoption. It must be fixed. Plenty of people want Linux to fail.

Keep up the good work true believers!

---

### Post by 2CV67 on 2009-01-05
Of course, I am extremely grateful to all the wonderful volunteer helpers on this & similar forums - quite one of the most gratifying aspects of Ubuntu!
Also to all the dedicated bug-solvers!
Thanks & Happy New Year to you all!

Nonetheless, I still feel, after watching new threads on this subject start every day, after keeping updated on the many related threads I am subscribed to, after going through the Bug-Report procedure & tracing various related bug-reports, that there are a lot of users not finding any solution for their kernel-panic problems.

I was going to ask if there was a recognized procedure for analyzing kernel-panics, especially the only-too-repeatable ones a lot of us are getting.
Some logical way of drilling down to root cause, or of carefully eliminating possible causes?
Some way of collecting useful log information?
Some way of sorting a mass of reported panics into a more-limited & more handleable number of typical cases?
Some way of separating messy threads into several threads each dealing with one type of panic - hopefully to the [SOLVED] stage?

Before posting this, I did some more Googling & came up with the following links (same info on 2 sites) which look like a good start, but are a bit over my head technically.
[http://rhcelinuxguide.wordpress.com/2006/06/01/linux-kernel-panic-prevent-cardiac-arrest/](http://rhcelinuxguide.wordpress.com/2006/06/01/linux-kernel-panic-prevent-cardiac-arrest/)
[http://www.dialogic.com/support/helpweb/dxall/tnotes/new/iw1207.htm](http://www.dialogic.com/support/helpweb/dxall/tnotes/new/iw1207.htm)

I will try to work through them for my case.
Maybe they can help others?

If anybody can comment/expand/clarify these procedures or provide something better, then thanks in advance!

---

### Post by bodhi.zazen on 2009-01-05
As has been explained many times on this thread your term "kernel panic" is very, very generic and can be caused by a number of problems ranging from a bad burn on a CD to the ati/nvidia drivers to wireless drivers. Because of the large number of potential causes there are a large number of potential solutions. There is no single problem or single solution.

Most of these problems are hard ware related. No operating system runs on all hardware and in order to "solve" these problems we need a lot more detailed information.

---

### Post by 2CV67 on 2009-01-05
> **bodhi.zazen said:**
> As has been explained many times on this thread your term "kernel panic" is very, very generic and can be caused by a number of problems ranging from a bad burn on a CD to the ati/nvidia drivers to wireless drivers. Because of the large number of potential causes there are a large number of potential solutions. There is no single problem or single solution.

Most of these problems are hard ware related. No operating system runs on all hardware and in order to "solve" these problems we need a lot more detailed information.

You seem to suggest I invented or misuse the term "kernel panic".

According to Wikipedia (& there are tons of other definitions)> A kernel panic is an action taken by an operating system upon detecting an internal fatal error from which it cannot safely recover; the term is largely specific to Unix and Unix-like systems.

The kernel routines that handle panics (in AT&T-derived and BSD Unix source code, a routine known as panic()) are generally designed to output an error message to the console, dump an image of kernel memory to disk for post-mortem debugging and then either wait for the system to be manually rebooted, or initiate an automatic reboot. The information provided is of highly technical nature and aims to assist a system administrator or software developer in diagnosing the problem.

From the link in my last post
> There are two main kinds of kernel panics:
1) Hard Panic (also known as Aieee! )
2) Soft Panic (also known as Oops )

Since hard panics and soft panics are different in nature, this document discusses how to deal with each separately.

How to Troubleshoot a Hard Kernel Panic

Symptoms:
1) Machine is completely locked up and unusable
2) Num Lock / Caps Lock / Scroll Lock keys usually blink
3) If in console mode, dump is displayed on monitor (including the phrase “Aieee!”)
4) Similar to Windows® Blue Screen of Death

etc etc

I am mainly talking about Hard Kernel Panics.

I very fully understand that there is not one single cause or one single solution.

Luckily, I have an acceptable workaround for my own particular kernel panic problem (for the moment) and this thread is not meant to fix that.

What I was hoping to achieve with this thread was to help all the other sufferers who are apparently not finding solutions.
I hoped that by concentrating expert attention, we could end up with some available diagnostic tools or methods and that sufferers could either find existing solutions or at least join groups with similar symptoms to work towards new solutions.

Currently, I am frustrated because...
> The kernel routines that handle panics...are generally designed to output an error message to the console, dump an image of kernel memory to disk for post-mortem debugging... 
...this key part of the panic handling routine seems to be missing.

Either it does not work (my feeling, but I could be wrong) or it is not being used by, or recommended to, all the sufferers in the threads.

Anyway, I think I have used up about all the spare energy I have for this subject, so will leave you all to it.

Hope I have not wasted too much time or upset too many good volunteers!

---

