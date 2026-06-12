---
title: "Remote Desktop  Issue. A Bug ?"
date: 2007-04-17
forum: Desktop Environments
---

### Post by StueyB on 2007-04-17
HI Everyone.

I have a problem that im not sure if i should file it as a bug.

I always use RDC to remote into my machine at work.

The problem is that I have a dual setup at work. When I log in remotely I can only see the left hand screen and not the right. There seems to be no way to see it. 

If I login under Windows the screen gets stretched to cover both screens.

I'm running XP at work and Ubuntu 6.10 at home, vanilla flavour.

The video card in my laptop at home (ubuntu machine) is  a  ATI Radeon Mobilty 9200.

At work  the video card is a ATI Hypermemory 256 MB card.

Any ideas ?

---

### Post by computerease on 2007-04-17
Could you provide a little more information?
What is the home OS (flavor/version)?
What "RDC" are you using on the home OS?
If you're using dual monitors at work with two graphics cards, video capture for the remote location could be a problem.  In other words, it might be helpful to have more specifics and then someone more knowledgeable than I might jump in here and give help.  
  With Windows there are even potential problems in how dual monitors work together.  I've seen systems with the primary monitor on the left and the secondary on the right and everything works fine.  If they are reversed with the secondary monitor on the left the system will glitch on every reboot (which means all the time).  Could you add some specifics.
In addition there could well be some issues with ATI cards.  See [http://ubuntuforums.org/showthread.php?t=365630](http://ubuntuforums.org/showthread.php?t=365630)

---

### Post by Jhongy on 2007-04-18
I don't think it sounds like a bug...

You only have one viewport when accessing via RDP, so I'm ot sure how it could display two screens of information.

You can probably still right-click on the Windows desktop, and choose properties to disable multi monitors, and set a nice resolution when accessing via RDP.... however, you'll have to change it back every time unless you access remotely as a different user from the user you log in as when physically in front of the computer.

---

