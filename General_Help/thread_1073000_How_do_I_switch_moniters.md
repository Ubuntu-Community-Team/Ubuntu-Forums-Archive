---
title: "How do I switch moniters?"
date: 2009-02-17
forum: General Help
---

### Post by gluxon on 2009-02-17
Okay so I have 2 moniters.

One of them is cracked near the bottom. So all I can use is the top.

The other one is the one that I want ubuntu working on.

So I've got one partly (MOSTLY) broken and one that works fine.

The one that's not broken is a VGA (Whatever that stands for). But the computer doesn't support VGA. However, the moniter that's broken has a VGA plug. (I know, it's weird). So I booted up ubuntu but... I need to know how to switch over the moniter from the broken one to the working one. So ubuntu shows up on the working one.

I've seen my friend do it on Windows XP, if he can do it in that, there must be a way to do it in ubuntu 8.10

Please help, this thing is a pain in the neck! :P

Thanks.

P.S. It was hard getting here with only 1/4 of the moniter working!!! And... nice Popcorn smiley :popcorn:

---

### Post by gluxon on 2009-02-18
bump

---

### Post by inadaze on 2009-02-18
Not sure I completely understand your issue.

Did you have two screens attached to the same computer (dual monitor setup) and you want to switch the primary for the secondary?  If so then you should be able to do that by looking under System --> Preferences or System --> Administration for something to control your screen setup.  I have an application called NVIDIA X Server Settings in  System --> Administration that will allow me to switch the two monitors.

If you have two monitors and you want to switch one for the other (meaning that you have one broken monitor attached to your computer and another sitting in your basement that works) then just physically remove and replace one for the other.  If the connections are not the same (ex: your working monitor is VGA and your computer only has a connection for something else) than visit your local computer store and see if you can buy an adapter to change it from VGA to whatever is on the back of the computer.  

If I have completely misunderstood please give me us more info and maybe we can help.

cheers
Jay

---

### Post by gluxon on 2009-02-19
YES!!!

Okay, how do I configure NVIDIA X Server to do that?

---

### Post by inadaze on 2009-02-20
Again, I am not sure I understand fully your issue.  If you have a dual screen setup, then the simplest thing to do would be to physically change the wire setup on the back of your computer.  You probably have a wire that splits the monitor signal into two - and each monitor is connected to this splitter.  If so, just swap the the cords (put each wire in the opposite connection).

Otherwise, in the NVIDIA X Server Settings, you should have a section called "X Server Display Configuration".  Here you should see a graphical representation of your two monitors = Lets say Monitor A and Monitor B.  Click and hold on the square representing the Monitor A and drag it to the opposite side of Monitor B.  You should see it move (and even resize if you are not careful).  once each monitor is on the opposite side, press apply.  You're screens will go black for a second and refresh with your new settings.  You will be prompted to accept the changes or it will go back to the way it was before in case you made a mistake and can't see anything.

Hope this helps
Jay

---

