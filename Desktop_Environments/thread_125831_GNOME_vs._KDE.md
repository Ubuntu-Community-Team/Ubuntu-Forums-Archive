---
title: "GNOME vs. KDE"
date: 2006-02-04
forum: Desktop Environments
---

### Post by BlackJack on 2006-02-04
I am new to Linux and do not have any experience with the different Graphical User Interfaces. I have been playing with Ubuntu for the past week (settled on Ubuntu because neither SUSE or Solaris were able to automatically detect and identify all of my hardware while Ubuntu was (with the exception of my wireless network card which has a Broadcom chipset). 

Well yesterday I reinstalled the OS with Kubuntu (KDE) and it had some things that I liked about it, but  it didn't seem to recognize as much of my hardware as Ubuntu did. One major example is the inability to automatically recognize and mount a USB drive (either Flash Drive or Hard Drive). I don't know whether it was a KDE vs. GNOME thing or if it was just because KDE is still rather new to Ubuntu and there are still some hardware drivers that have not been added to it yet.

Anyway, on to my questions...

Does anybody have enough experience with both interfaces to tell me what the pros and cons are for each?

and

Is there a way to have them both on the system at the same time and switch back and forth as desired?

Sorry about the long post but any feedback would be appreciated. I re-installed Ubuntu this evening since I didn't have time to figure out how to get my USB drives recognized and I needed the data on them.

Thanks............

---

### Post by Hygelac on 2006-02-04
Out of curiousity, when you installed KDE did you get its updates from the repositories?  I have a USB drive which it wouldn't recognize (that GNOME did) until I updated KDE.

---

### Post by PapaWiskas on 2006-02-04
You can run both.  I started out with Gnome, once I got comfortable, I installed Kbuntu.  I have used KDE before and once I booted up into it, I realized why I always hated KDE, it just gets to cluttered.  Then when I went back to Ubuntu, a lot of the KDE stuff infiltrated my menu systems, which really aggravated me.

Personally, I think it is just a matter of choice.  Both have their pros and cons.  I noticed the Gnome desktop just ran faster on my laptop than KDE did.

For the last week however I have been using XFCE, and let me tell you, I think Gnome is going to take a backseat, because XFCE just freakin flies on my laptop.

I did try Fluxbox and Openbox, but for some reason the desktop environment would not load up, not sure why, and I am not experienced enough to go digging around.

For me Ubuntu just worked right off the bat, and I love it.  I have been using it for over a month now, and do not miss Windoze at all.  

And the people here are awesome, this community is great.

Anyway, sorry for the rambling, hope this helps in some way.
In the end it is all just a matter of choice, which is what makes Linux so awesome.

---

### Post by BlackJack on 2006-02-05
Thanks for the quick feedback.

Hygelac
Yes, after installing Kubuntu I did the updates and it installed something like 100 updates and 4 new installs. The USB drives still didn't work and i don't know enough to manually fix that problem. After installing Ubuntu again everything was back to being recognized again.

PapaWiskas
My primary interest in KDE is because some of the guys at work swear by it. Personally I have been in the Microsoft world since DOS 2.0 and the GNOME interface is, I think, every bit as easy if not easier than Windows XP!

I am curious about your mention of XFCE though. I saw your other post on it and it sounds like it has potential. Where did you get it and was it dificult to install? Are you able to have both GNOME and XFCE installed at the same time? If so, is it something you can switch back and forth or do you need to select one or the other at bootup?

Thanks again for your feedback.....

---

### Post by SyL on 2006-02-05
[http://linux.slashdot.org/article.pl?sid=05/12/13/1340215](http://linux.slashdot.org/article.pl?sid=05/12/13/1340215)

but under ubuntu gnome rules!

---

### Post by Perfect Storm on 2006-02-05
[QUOTE=BlackJack]

I am curious about your mention of XFCE though. I saw your other post on it and it sounds like it has potential. Where did you get it and was it dificult to install? Are you able to have both GNOME and XFCE installed at the same time? If so, is it something you can switch back and forth or do you need to select one or the other at bootup?[/QUOTE]

just
```

sudo apt-get install xubuntu-desktop
```
and you have it (around 100 mb)
When you want to log into it, choose session at the login screen. Here you can switch between the diffrent DE.
Also if you want you can make a server/minimal install of ubuntu so you don't get gnome by default. You'll end up in command screen. then 
```

sudo apt-get install xubuntu-desktop
```

---

### Post by PapaWiskas on 2006-02-05
If you do what Artificial Intelligence said to do, you are on your way.  

I would recommend using Gnome for awhile though, just to get more comfortable.  Like yourself I come from a long line of Windoze products, and getting used to the way Linux does things is not easy for me.  XFCE is slightly less userfriendly out of the box, compared to Gnome.

I am terrified of breaking something for the fear that I will have no clue on how to fix it.  At least if I messed something up in Windoze I knew I would be OK.

XFCE does fly, it is awesome.  But finding help on certain things takes a bit of digging.  I wish they had a XFCE section to ask questions.

---

### Post by Navyblue on 2006-02-05
When Kubuntu Breezy is released the USB drives automount is broken. Update to the latest "parts" may or may not help in my limited personal experience.

I have 2 boxes with Kubuntu (and more in the past). One automounted USB drives fine. On another I need to add the corresponding fstab line for it to mount at all. Software wise the two boxes are almost identical. I have no idea what went wrong and didn't bother to find out.

---

### Post by bartbes on 2006-02-05
about the same question and the same name: [here](http://ubuntuforums.org/showthread.php?t=125976)

---

### Post by BlackJack on 2006-02-05
Thanks for all your input everybody. I will check it out. Right now I am not really to worried about breaking anything because I am lucky enough to have a spare hard drive for my laptop. I am playing with Linux on that, without disturbing my Windows install, until I find teh configuration i am comfortable with and have everything working at an acceptable level.

Basicaly this puts me in a position where now is the best time for me to play and break things before I go to far and cannot go back.

I am also planning on hitting a local Linux User Group to see what they can tell me.

Thanks again.........

---

### Post by MacV on 2006-02-05
Odd, kubuntu could automount my USB sticks just fine. I fine KDE too convoluted though.

---

### Post by BlackJack on 2006-02-05
OK, now I am starting to get confused.........

I have looked at the other thread and a few in other places as well. It seams that KDE is more flexible/configurable and some people think that is is more powerful than GNOME. I can accept that from a user interface standpoint but then they started getting into compatibility issues and lost me altogether.

I thought the application compatibility was based on the kernel that you were running, is there also a compatibility issue between apps and the user interface?? Doesn't the user interface, whether it be GNOME or KDE or something else, just give you a more intuitive and "easier" interface than a command prompt? Does it also generate issues of compatibility where an app will work on one but not the other, even if you are running both on the same kernel?

---

