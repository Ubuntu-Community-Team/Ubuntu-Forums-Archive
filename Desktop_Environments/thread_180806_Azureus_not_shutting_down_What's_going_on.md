---
title: "Azureus not shutting down? What's going on?"
date: 2006-05-23
forum: Desktop Environments
---

### Post by bbitmaster on 2006-05-23
First I want to say that I absolutely love ubuntu, it's been a great introduction to linux for me. This is my first post. I hope I'm posting in the right forum.

I have a small home network, with about 4 computers. Two of them belong to me I run windows on one and Ubuntu exclusively on the other. I had Azureus running on my Ubuntu machine, getting a few torrents. And I decided that I wanted to play some Battlefield 2 on my windows machine. Azureus is a bandwidth hog and makes my ping go insane, so naturally I closed Azureus, before starting BF2 on my windows machine.

Well, interestingly, my ping was still really high. I opened a DOS window on my windows machine and typed "ping [www.google.com](www.google.com) /t" and it was giving insanely high numbers. I suspected someone in the house was downloading, so I checked with everyone, and they all said no. I knew something was going on, so one by one I started unplugging ethernet cables, untill I found the machine that was hogging the bandwidth. It was ubuntu!

I opened terminal and typed netstat, and sure enough, there was a bazillion connections listed. I thought the list would never end as it kept going. Most of them were connected to port 8523, which is what I had azureus set to use!

I don't know of a command to tell what program is using what connection (I'm not a linux guru, I only know a few important commands), so I typed TOP to list all of the processes thinking that whatever had that many connections going would surely be taking some CPU. And there it was, "Java" was using 20-30% of my CPU power. I killed it, and the connections went away.

Basically, I'm wondering what happened here? Azureus was definatly closed, but it was as if it stayed open in memory or something. How can I prevent this from happening again? Any suggestions?

---

### Post by nanotube on 2006-05-23
well, the question is, did you close azureus by going through the menu, selecting File>Quit, and then confirm, or did you just close the window by clicking the little "x" in the top right corner?
if it is the latter, then it is understandable, since the default behavior of azureus when you close the window with the "x" is to keep running in the background. if you want to really quit, do it through File>Quit.

---

### Post by bbitmaster on 2006-05-23
That must have been it, I probably closed it by clicking the X. Thanks for the quick helpful reply, I'll know better now.

---

### Post by nanotube on 2006-05-23
and another thing - (assuming you are using gnome) when azureus is running, it places a tray icon in the notification area (next to where you have the update notification, network status, etc). so you can just look there to see if it is running, and right click and quit from there, as well. 

have fun :)

---

