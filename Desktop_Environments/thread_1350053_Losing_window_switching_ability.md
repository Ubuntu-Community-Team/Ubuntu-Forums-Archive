---
title: "Losing window switching ability"
date: 2009-12-08
forum: Desktop Environments
---

### Post by apokkalyps on 2009-12-08
So this started happening about a week ago and has escalated to happening more and more to the point where it has happened 4 times today.  I've been asking in IRC and haven't gotten any good advice.

Initially I was using metacity.

What happens is, out of nowhere, not by any event that I can pin down, I simply lose the ability to switch which window is in focus.  I can move the mouse and the computer is working fine otherwise, but I cannot switch windows.  This includes either clicking an unfocused window, or trying to press alt-tab (which does nothing).  Also, it seems like pressing alt+space to get the window settings drop box doesn't work either.  Sometimes I also cannot click different areas even within the same application I am trapped in.

My knowledge of things like window managers is very poor.  I thought it was metacity's problem, so I reinstalled that in synaptic and the problem persisted.  Then I went ahead and enabled compiz, and imported my settings.  A few minutes later compiz did its own version of the problem.  This time my cube zoomed out and stayed that way.  No amount of clicking or key presses would zoom back to the desktop, although I could still rotate the cube around and see people sending me instant messages.  I rebooted, and this time, it booted straight into a zoomed out cube.  I rebooted again, and typed this message into ubuntu forums and when I went to preview the message, the cube zoomed out and stuck that way. :mad:  Now I am on my windows laptop retyping the message as best I can read it through cylindrical cube distortion.

Please help if you have any ideas.  This is a serious problem as it means I have to reboot multiple times a day (like every 10 mintues now) and I can easily lose data.  I will basically have to stop using Ubuntu and only use my windows laptop until I can figure it out, which will be virtually impossible to do on my own given my limited knowledge in this area.  Thanks for any help!

edit: i found that by hitting escape I can zoom back to the desktop from the cube, however then the problem persists exactly like it did with metacity.

---

### Post by earthpigg on 2009-12-09
are any partitions on that computer's hard drive over 90% full?

this command will tell you:
> df -Th

---

### Post by apokkalyps on 2009-12-09
> **earthpigg said:**
> are any partitions on that computer's hard drive over 90% full?

this command will tell you:

:KS Yes actually....my /home partition is 99% full....would that cause my window managment system to fail?
there is still >5 gig free

---

### Post by earthpigg on 2009-12-09
> **apokkalyps said:**
> :KS Yes actually....my /home partition is 99% full....would that cause my window managment system to fail?
there is still >5 gig free

yup, Linux partitions are not designed to be over 95% full, regardless of size. there is no predicting what will start to act up and be broken, but its a guarantee that ***something*** will.

after ~90% performance starts to degrade. 

this is the price we pay for not needing to defrag.

---

### Post by akashiraffee on 2009-12-09
Give this pig a medal.

---

### Post by apokkalyps on 2010-01-05
does this apply to NTFS drives?  external storage? or just the main drive with '/' on it or '/home'?  Other non essential EXT file systems?

---

### Post by SalahTr on 2010-01-05
> **earthpigg said:**
> Linux partitions are not designed to be over 95% full, regardless of size. there is no predicting what will start to act up and be broken, but its a guarantee that something will.
after ~90% performance starts to degrade. 
this is the price we pay for not needing to defrag.
Thanx

---

### Post by earthpigg on 2010-01-06
> **apokkalyps said:**
> does this apply to NTFS drives?  external storage? or just the main drive with '/' on it or '/home'?  Other non essential EXT file systems?

NTFS will become unbearably slow. 20 minutes to boot windows (though other things can certainly cause that...).

/home being to full will probably cause programs to start with default settings and disregard any custom preferences you have (firefox bookmarks, pidgin account info, etc). that's a guess based on my imperfect and incomplete understanding of this stuff. 

external storage and the like will start to fragment and perform slower and slower. dont listen to the fanboys: yes, even ext* fragments.


do yourself a favor, keep it all under 90% if possible. my /home is at 84%... time for me to clean some stuff up, myself.

---

