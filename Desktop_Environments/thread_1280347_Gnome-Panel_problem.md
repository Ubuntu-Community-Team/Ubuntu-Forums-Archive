---
title: "Gnome-Panel problem?"
date: 2009-10-01
forum: Desktop Environments
---

### Post by zggame on 2009-10-01
I am using the latest 9.0.4 with gnome on a compaq cq60-420us laptop (pentium dual-core T4200/4G/250G).  The display is 1366x768.  So it makes sense to put panels on the side instead of top/bottom.  But it since become not very stable.  It freezes maybe once every other day.  Everything else works except the panel freezes.  I tried to disable all the appearance visual effect.  And this helps little.  But I cannot make it happen consistently. 

One thing surely does not work is the time gadget.  Once the panel becomes left/right. The time stops.  

Overall, the 9.0.4 seems not as stable as before, I have experience quite some total froze-up that needs power-off.  

And often one window (firefox/gedit/...)  freezes and does not accept any key or mouse-click. All other windows work.  The only thing in this window works are the resize/maximize/minimize buttons.  And the window comes back to life after I have  clicked one of them. :(

---

### Post by bobblu on 2009-10-02
I've found a solution to my problem and if anyone else has the same problem.

I ran the command in a terminal *killall gnome-panel*

and then ran the command *gnome-panel*

This brought the default panel back. I logged out and in again and got no more errors 		
 		  		  		 		  		 		 			 				__________________=============================
[weddings in the maldives](http://www.bestatmaldivesholidays.co.uk/pages/honeymoons)
[buy steriod](http://legalsteroids.com)

---

### Post by zggame on 2009-10-03
Thanks.  A logoff certainly solves the problems.  But that really sucks.  

> **bobblu said:**
> I've found a solution to my problem and if anyone else has the same problem.

I ran the command in a terminal *killall gnome-panel*

and then ran the command *gnome-panel*

This brought the default panel back. I logged out and in again and got no more errors 		
 		  		  		 		  		 		 			 				__________________=============================
[weddings in the maldives](http://www.bestatmaldivesholidays.co.uk/pages/honeymoons)
[buy steriod](http://legalsteroids.com)

---

