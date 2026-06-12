---
title: "[SOLVED] Weather applet not updating"
date: 2008-04-27
forum: Desktop Environments
---

### Post by timzak on 2008-04-27
Is the gnome weather applet tied in to the Ubuntu servers?  Seems like most of the past two days the weather has been unable to update when normally it has never had this problem before.

---

### Post by jongkind on 2008-04-27
It's working fine for me. It's likely related to the location of the weather station that you choose. Can you select a different location to see whether that one is updating?

---

### Post by timzak on 2008-04-27
Well, I've been using the same weather location since Feisty and it's always updated on command until I installed Hardy.  Now it seems to hang and fail to connect most of the time.  Since this is a clean install, I just assumed the only issue was overloaded servers...

---

### Post by timzak on 2008-04-29
Seems to be back to normal now.  Although I can't figure out how to adjust the update interval in the weather that's tied into the clock applet.  Anyone know if this is adjustable like it is in the standalone weather applet?

---

### Post by Duranxl on 2008-08-13
Why does the help file mention "update weather" buttons when there is no such thing?

---

### Post by Fred_C on 2008-10-28
My weather applet seems to break every time there is a kernel upgrade. It's there, but it stops updating, and if I manually try to update it, it hangs. Is there any fix for this?

---

### Post by xak on 2009-01-06
I experience this issue from time to time.  This thread is marked as solved.  What is the solution?

---

### Post by xak on 2009-07-16
> **xak said:**
> I experience this issue from time to time.  This thread is marked as solved.  What is the solution?

Still happening to me frequently.  Anyone??? :confused:

---

### Post by timzak on 2009-07-17
Sorry, I don't have a solution for you.  When I reported this I was on Hardy Heron.  It just started working again, so I don't know why or how.  Have you reported this in Launchpad?

---

### Post by shinjan on 2010-05-18
I am also facing this problem since I have started using lucid...
neither the applet tied with the clock, nor the separate one is getting updated...

---

### Post by mike-g2 on 2010-06-16
I solved this issue in Lucid by changing the preferences to another location, updating (which worked) and then switched it back to my preferred location.  I have no idea why this works, but it does. 

Mike

---

### Post by xorrbit on 2011-03-24
I am also having this problem, in 10.4 LTS. Topic name is false as this remains a problem for many.

I made a script that kills the weather applet, which I run whenever I notice it's messed up. Gnome then pops up with a message that the applet is killed and would I like to relauch it which I hit OK on. I tried to figure out how to relaunch without getting the popup but couldn't find it in a few minutes. In any event here's the script:

```
kill `pidof gweather-applet-2`
```

---

### Post by cosmolee on 2011-05-06
I don't know either why this thread is marked "solved".  It doesn't offer any solution.

But a solution exists at this thread - at least for the NYC area:

[http://ubuntuforums.org/showthread.php?t=1648601](http://ubuntuforums.org/showthread.php?t=1648601)

This issue is not solved because no updates have fixed the problem.  I've had to manually make the changes in the "Locations.xml" file.

How does one change the status of a thread to "UNSOLVED"?

HTH.

---

### Post by archeryguru2000 on 2011-08-17
> **mike-g2 said:**
> I solved this issue in Lucid by changing the preferences to another location, updating (which worked) and then switched it back to my preferred location.  I have no idea why this works, but it does. 

Mike

This solution also worked for me.  I have two workstations, both running a weather applet (gnome panel, however desktop is 11.04 and laptop is 10.04), and one was updating just fine (10.04) while the other (11.04) was stuck on a previous date.  I simply changed locations in the preference settings, updated, and then changed back to my current location.  I'm not sure what that affects... maybe this updates/creates some config file that needed some persuasion.  Either way, this is a solution that worked for me and hopefully can help somebody else.

~~archery~~

---

