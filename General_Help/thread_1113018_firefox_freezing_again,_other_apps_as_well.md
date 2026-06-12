---
title: "firefox freezing again, other apps as well"
date: 2009-04-01
forum: General Help
---

### Post by jensenguy on 2009-04-01
Hello

I recently posted because of firefox crashing on me, and the issue seemed to be corrected when i updated to 3.0.8. Things definetly got better, but im still having crashing issues, but maybe not firefox related.

I now get a random lock up of firefox - not just crashing and dissappearing, but freezing and becoming unusable - all open windows at once. I can shut it down, but only sometimes restart it. Sometimes it will say process still running, and will not allow me to end it until i restart. 

Ive also had Amarok music player freeze on me once, and Ive had ubuntu freeze completely once. Im starting to think I have either a ubuntu software issue, or a hardware issue.

Any tips on how to pinpoint this bug?

---

### Post by jackflap on 2009-04-01
It's more than likely a hardware issue (or perhaps a software issue problematic with a specific piece of hardware). 

Does it happen when you're doing something specific? Like the sound-card in use? 

Have you ever had a Linux install work without the freezing?

Perhaps also try switching out various pieces of hardware, like RAM with other pieces, if you have any extras lying around. It would help diagnose potential hardware issues.

---

### Post by jensenguy on 2009-04-01
This is the first linux install on this computer (or any for me), so cannot compare it to another. My freezes are completely random as far as I can tell. (so far firefox, amarok, and complete OS freeze) I initially had problems mostly with flash pages, but after I upgraded firefox that was fixed.

This is a recently upgraded computer, has not been used for a while, so I cannot say for sure that there are no issues. But when it is working correctly, its very fast and smooth. 

I know one thing that i was wondering, It does have a one-off graphics card - Sis Xabre 400. The graphics look like they should, but I wonder if that has a compatibility issue? I didnt install any special drivers, just whatever came with ubuntu.

---

### Post by markharding557 on 2009-04-01
did it work ok on windows or another distro?

---

### Post by jensenguy on 2009-04-01
When I last used this pc, it was windows 98SE. It worked as good as most windows comps do. I stopped using it when my hard drive crashed. It now has a new 80gb hard drive and a fresh 1gb of memory. But like I said, its been a number of years since ive ran it. 

Is there any ubuntu programs that would assist me in pinning down hardware or software errors?

Another thing - and Im not sure if this is actually effecting the freezing or if I'm just imagining it, but it does seem like it gets worse once the computers been up and running for a few hours.

---

### Post by jensenguy on 2009-04-01
Heres a little more info:

Whenever im in firefox through terminal, it crashes with a segmentation fault. Most of the time it will allow me to restart firefox.

This last time firefox crashed, I attempted to restart, and nothing happened. I went into terminal, typed in firefox and got the following error- 

[I]terminate called after throwing an instance of 'std::bad_alloc'
  what():  std::bad_alloc
Aborted[/I]

At this point no application on ubuntu would load - all giving the same error. Had to reboot, and all was back to normal. 

Please Help!

---

### Post by jackflap on 2009-04-02
This is a tough one. Here are a couple of random ideas to try out:

1) Check that your swap partition is configured and being used. You can use 'free' on the commandline to check. If the total is 0, then that's a problem.

2) Perhaps try installing a previous version of Ubuntu, i.e. if you're on Intrepid, try Hardy. You could even boot the live cd and see if you can get it to crash while on the live cd, and if you can't consider reinstalling.

3) Perhaps try the Jaunty beta, something may have been fixed since Intrepid.

4) Install the CPU temp applet onto your panel (right-click on panel and Add Applet.. i *think* you should be able to find it in the default set). Make sure that your CPU isn't overheating while the computer does anything intensive. I believe anything over 50 degrees celsius is not good.

---

### Post by jensenguy on 2009-04-02
thanks for tips - 

I checked the swap partition and its about 3 gigs. So thats good. According to the BIOS, cpu temp is 44 degrees Celcius at the time of a restart for a crash. It doesnt sound like thats an issue, but hard to say. Im hesitant to install a beta OS, but I might try the live cd boot idea and see if thats any better for me. 

Also I dug up some more crash data for syslog - 

[I]Apr  1 21:31:59 jim-desktop gdm[4814]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 
Apr  1 21:31:59 jim-desktop bonobo-activation-server (jim-7688): could not associate with desktop session: Failed to connect to socket /tmp/dbus-eoB16nGFyY: Connection refused

Apr  1 21:50:52 jim-desktop gdm[4808]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 
Apr  1 21:50:52 jim-desktop kernel: [ 1028.161162] fast-user-switc[5237]: segfault at 0 ip b77daf0b sp 00000000 error 4 in libglib-2.0.so.0.1800.2[b77aa000+b5000][/I]

This was after the computer had been on for a couple hours, the first one just kicked to a black screen and I had to restart it, the second one went to a black screen, then back to the logon screen, but I still had to restart it to make it usable again.

_I thiink Im going to start a new thread since my problem has become more than a firefox issue_

---

