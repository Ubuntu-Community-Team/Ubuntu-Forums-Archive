---
title: "Displays blurred screen after install"
date: 2011-06-19
forum: Desktop Environments
---

### Post by rpbangerter on 2011-06-19
I am in the process of trying to move my parents desktop computer from Windows Vista to Ubuntu 11.04.  They both have used the system and find it far superior to Windows.  The desktop I am attempting to load Ubuntu to is running next to ancient, at the very least 5 years old.  It is either an HP A350N or and HP A500N so we aren't talking any new technology.  They have been running one form or another of windows on the computer since they first purchased it and it has worked with some flaws such as IE not working unless you log in as an admin or forfox not being able to update without an admins permission.  

I am doing the download of the system from Ubuntu using the Wubi mainly because every time I attempt to use my CD it freezes the computer.  I am capable of creating a clean crisp download in a reasonable amount of time and when the computer does the reboot it comes up with a clean crisp picture explaining all the great features Ubuntu has to offer.  Once the final install is complete it brings me to the log in page and it is hear I notice my first problem.  The bar on the bottom of the screen only displays about halfway and therefore it looks strange but the screen is still crystal clear.  When I input their log in I get the traditional log in and a screen that pops up saying this computer needs to be run in classic mode.  I click okay and then it completes the log in and the screen is an absolute blur.  The pixels don't line up and although you can somewhat see halfway what should be displayed it isn't enough to be able to navigate to make any changes to the screen.

I thought initially it was a problem with the monitor so I tried a spare that I had over at their house and got the same effect.  Last week my mother purchased an older dell flat panel monitor and I thought that maybe this one would do the job since I had read somewhere on here that there had been a problem with the other monitor I was attempting to use with the install.

When I run Ubuntu in safe mode the screen is clear but I can't set the monitor for more than a 1 time boot in that screen.  If anyone could help me out this is frustrating the hell out of me.  BTY I will give you as much information as I have at the time, this computer is not at my residence and this is a weekend hobby.

---

### Post by wildmanne39 on 2011-06-20
> **rpbangerter said:**
> I am in the process of trying to move my parents desktop computer from Windows Vista to Ubuntu 11.04.  They both have used the system and find it far superior to Windows.  The desktop I am attempting to load Ubuntu to is running next to ancient, at the very least 5 years old.  It is either an HP A350N or and HP A500N so we aren't talking any new technology.  They have been running one form or another of windows on the computer since they first purchased it and it has worked with some flaws such as IE not working unless you log in as an admin or forfox not being able to update without an admins permission.  

I am doing the download of the system from Ubuntu using the Wubi mainly because every time I attempt to use my CD it freezes the computer.  I am capable of creating a clean crisp download in a reasonable amount of time and when the computer does the reboot it comes up with a clean crisp picture explaining all the great features Ubuntu has to offer.  Once the final install is complete it brings me to the log in page and it is hear I notice my first problem.  The bar on the bottom of the screen only displays about halfway and therefore it looks strange but the screen is still crystal clear.  When I input their log in I get the traditional log in and a screen that pops up saying this computer needs to be run in classic mode.  I click okay and then it completes the log in and the screen is an absolute blur.  The pixels don't line up and although you can somewhat see halfway what should be displayed it isn't enough to be able to navigate to make any changes to the screen.

I thought initially it was a problem with the monitor so I tried a spare that I had over at their house and got the same effect.  Last week my mother purchased an older dell flat panel monitor and I thought that maybe this one would do the job since I had read somewhere on here that there had been a problem with the other monitor I was attempting to use with the install.

When I run Ubuntu in safe mode the screen is clear but I can't set the monitor for more than a 1 time boot in that screen.  If anyone could help me out this is frustrating the hell out of me.  BTY I will give you as much information as I have at the time, this computer is not at my residence and this is a weekend hobby.
Hi go into additional drivers and see if there is a driver for your video card, if so install it, you will have to be connected to the internet to check, if not put this command in a terminal
```
sudo lshw
```also run this command
```
/usr/lib/nux/unity_support_test -p
```
and post the outcome  here by clicking on new reply and click # and paste the information between the brackets.

---

