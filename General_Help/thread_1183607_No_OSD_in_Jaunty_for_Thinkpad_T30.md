---
title: "No OSD in Jaunty for Thinkpad T30"
date: 2009-06-10
forum: General Help
---

### Post by emeraldgirl08 on 2009-06-10
Hi. I installed Jaunty and noticed that my on-screen displays were nowhere to be found. I'm wondering if anyone (who has an IBM and/or T30) has a solution for this?

The OSD was there in 8.10 so I'm wondering what has happened to them. Any help?

---

### Post by emeraldgirl08 on 2009-06-23
:popcorn:

Okay I found a fix for the lack of Thinkpad T30 on-screen displays in Ubi 9.04.

a) Go to your synaptic package manager.

b) Key in "Tpb" in the search field (without the "")

c) check it.

d) enable

There. Now you have onscreen displays. You may worry that there is the footnote about having the hotkeys removed. I checked the thinklight, display off, brightness, except the hibernation after install- they all work. I'm a little leery of trying hibernation b/c I don't use it and have read something about problems with it.

If you would like to restore your pre-tpb settings just go back to synaptic package manager and uncheck the "tpb" and recheck the "hotkey-setup."

---

### Post by emeraldgirl08 on 2009-06-23
Hmmm... after I turned my laptop off for a bit and turned back on. The OSD is not working. Synaptic shows that it's still installed but I don't know if there's a location or some kind of GUI interface to tick and start with Ubuntu as I can't find any.

If anyone knows how to have this startup with ubuntu let me know!!! Thanks.

---

### Post by mcdragon on 2009-10-02
I also noticed the OSD disappearing on my T43. The tpb package did enable some sort of OSD but its not the same as it was.

Well, so far better something than nothing.

---

### Post by harryc on 2009-11-01
I'm seeing the same thing on a Thinkpad X60s running Karmic. I installed TPB and saw the OSD for that session. It disappeared after a reboot and hasn't been seen again. Any ideas?

---

### Post by autocrosser on 2009-11-01
Hmmmm--I found that you can "restart" it in your present session with "sudo tpb" & it wiil continue until your next session....for some reason it is not being "started" with your X session like it should.....

Looks like a bug report is in order.

I use ThinkPads (currently a T42P) & am interested in it also.....

More info: there is a bug report & work-around here: [https://bugs.launchpad.net/ubuntu/+source/tpb/+bug/158262](https://bugs.launchpad.net/ubuntu/+source/tpb/+bug/158262)

Important info:> it seems that its group is kmem, that's why I can't read it with my user added to nvram
for now, I added /usr/bin/tpb to sudoers, so it can be run without a password, and added
tpb -d to run at session start

---

### Post by autocrosser on 2009-11-01
OK--my workaround is:

don't muck around with the /etc/sudoers file--just add a startup in your sessions that looks like:
```
gksudo tpb
```and then include any info you need to remind yourself that the command is for the OSD...  after your session start you will get a sudoers window to insert your password--then the OSD will work.

---

### Post by emeraldgirl08 on 2009-11-01
Hmm...interesting developments here :)

If anyone tries this PLEASE let us know how it works! I do really miss the Intrepid OSD though. They were very nicely done and looked like a match for Linux.

I haven't installed Karmic yet...I downloaded over the course of the morning on Saturday and have taken a small tour with the LiveCD. 

It's Fabulous so far BTW. :D

---

### Post by autocrosser on 2009-11-01
It works in Karmic--My T42P really likes 9.10......

---

### Post by harryc on 2009-11-01
Perfect, works great in Karmic. Thanks! :guitar:

---

### Post by autocrosser on 2009-11-01
No problem--I'm just one of the Alpha-testers--on Holiday for a couple of weeks til Lucid starts up......Then I'm back to work--slavin' to get the next release to all of you with as few bugs as I can :D

Look in on us from time to time.....[http://ubuntuforums.org/forumdisplay.php?f=377](http://ubuntuforums.org/forumdisplay.php?f=377)

We were all told to "go forth & fix things until we need to go back to work" ;)

---

### Post by harryc on 2009-11-01
Awesome, I'll check it out. Thanks for what you do. 8-)

---

### Post by autocrosser on 2009-11-01
I like the thrill of seeing 100 updates a day & looking at all the shiny new toys before almost everyone else--its also fun working thru the problems--you get a great chance to see the inner working of Linux & fix what breaks--The testing forum tends to be a world unto it's self--we really support each other & yes we spat at each other from time to time--but we're like an extended family--we all watch each others back & help whenever we can.

It's great fun--all skill levels can join--we'll help you.  Show up & kill bugs :)

---

### Post by Temetka on 2009-11-02
Like others I have installed 9.10 on my X41T and the tpb package. Like others it failed to load after a reboot. Before I read this thread I had already added it as a startup program as a workaround. I just wanted to hop in here and say that said work around does work, at least for me.

---

### Post by mac9416 on 2009-11-02
Hello,

I tried installing the tpb package. This is what I got:

> mac9416@mac9416-laptop:~$ sudo apt-get install tpb
[sudo] password for mac9416: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package tpb
mac9416@mac9416-laptop:~$

I have all the official repos enabled. Any ideas?

Thanks!

**Update:**

Apparently I had a crummy mirror. One apt-get update and I'm back on track.

---

### Post by aextance on 2009-12-07
Hey emeraldgirl, did you ever get this working in Karmic? 

I'm seeing corruption of some notifications - which I guess you might call an OSD?

For more info see this thread:

[http://ubuntuforums.org/showthread.php?p=8422246](http://ubuntuforums.org/showthread.php?p=8422246)

---

### Post by emeraldgirl08 on 2009-12-09
Hi axtance :)

Sorry I got TPB to display only that one time! I don't understand how to go into my settings in Karmic and change stuff. GRUB 2 is strange enough as it is and I've been busy with finals.

I'll check out that thread now.

---

