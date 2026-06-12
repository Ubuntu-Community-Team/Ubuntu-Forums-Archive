---
title: "Windows pops up on wrong screen"
date: 2009-04-05
forum: General Help
---

### Post by VII on 2009-04-05
Hello,

This is so annoying, 90% of my apps starts on the wrong screen, that being my left one. It seems like my right one is the main one, because that's where the login screen turns up and where the panels are, but still. Almost all applications and little windows opens up on the left one. Is this because the left one is closer to x=0? Is there anything I can do about it? Like setting an offset or something.


Regards,
Simon


PS. Forgot the specs. It's Ubuntu 8.10 with an nvidia twinview setup.

---

### Post by zigga15 on 2009-04-05
Look at your xorg.conf file. If you are using a nvidia graphics card and you are utilizing dual monitors using Option Twinview then you can add another command like "leftof" to switch the orientation.

Your graphics card will have one primary and one secondary output, this command reverses them. If you mess around with it you should be able to get it sorted. Check this link out (the last part): 

[http://www.ubuntugeek.com/dual-monitors-with-nvidia.html](http://www.ubuntugeek.com/dual-monitors-with-nvidia.html)

~ Dan

---

### Post by VII on 2009-04-05
Thanks for the quick reply. They are already set up in the right order. I have the login screen and the panels on my right screen, and that's how I want it. But it seems like new windows doesn't care about what screen is primary. They go with the most left one.

---

### Post by zigga15 on 2009-04-05
Yea I would say your guess was correct, something along the lines of x=0.

I run dual 22" at home, and I have my primary screen on the left. However some programs (pidgen and firefox particularly) remember where they were when you last closed them and pop up there.

I don't know many people who have the primary monitor on the right. I think the only solution would mean that you would have to move your mouse to the left of your left screen to make it appear on the right of your right screen.

Good luck!

---

### Post by VII on 2009-04-05
Actually Pidgin is the only applications that, for me, will start at the screen they were terminated at. All other will appear on the left screen. Do you mean that those appear on the screen that my mouse is NOT at?!

[ edit: After trying this out it seems to me that they ALWAYS start on the left screen, regardless of mouse location ]

This is a "real pain" for me since my left screen is actually a projector that's turned off. So I have to choose 'move' from their panel item and drag them over to the right screen.. That is if they have a panel item, otherwise I'll be trying to randomly grab the window, of course failing, and then turning on the projector just to move that window. lol please help me.. :D

---

### Post by VII on 2009-04-05
Anyone know about a fix for this? Is there any setting somewhere where you can tell the window manager(?) to remember window positions?

---

### Post by VII on 2009-04-05
I just realized I didn't have this problem earlier, say 6 months ago. Maybe that could be a clue.

---

### Post by wrose51106 on 2009-04-05
What is your Nvidia driver revision?

-Bill

---

### Post by VII on 2009-04-05
NVIDIA X Server Settings says: NVIDIA Driver Version: 173.14.12

---

### Post by wrose51106 on 2009-04-06
There has been a couple of updates since the 173, 177 and 180. Update via the package manager to 180 and post back.

-Bill

---

### Post by VII on 2009-04-06
I've now upgraded to 180. The windows still behave the same, they always open up on the left screen regardless of where I closed it or where my mouse is. Though, the update did solve another problem I had, laggy scrolling in FF3. Thank you for that. =)

Anyway, the window problem remains. =\

---

### Post by wrose51106 on 2009-04-06
I do have a simple "patch" but no fix, you say 90% open on the wrong screen.

Swap vga cables. Now only 10% will open on the wrong monitor ):P

-Bill

---

### Post by VII on 2009-04-10
Anyone else know anything about this?

---

### Post by ITAndrew on 2009-06-16
I am also having the same problem I believe. I have Twinview set up on my box at home (was running jaunty) and was having some issues.

-Firstly, I have two mouse pointers, when I cross screens the pointer persists.

-Secondly, most Gnome apps started from the menue result in opening on left monitor, unless I start with alt-f2 or create a shortcut on the desktop.

Now this hapened in Jaunty, this same box is now running FreeBSD and has the same problem. My hunch is the problem is with Gnome, I have seen a few bugs listed but I have seen no upstream action taken.

This does not happen in XFCE (Which I use GDM to startx) so we can eliminate GDM and alternate window managers. Hrmm Gnome?

Also, this does not happen in 8.04 only > 8.10

---

