---
title: "basic technical minecraft server questions"
date: 2011-03-15
forum: Gaming &amp; Leisure
---

### Post by wog on 2011-03-15
Hi, I've searched for answers to this, but I can't find anything about it. I know there are at least a few minecraft server ops here, so maybe someone can give me some clues.

I want to make a server for some friends and me to play on. The server runs, and I can login from afar, so I know the IP address is being forwarded properly.

When I play on it, it runs okay and I can do whatever I want, but when I shut the server down, all progress is lost. I come back the next day and it's like I was never there.

How do I solve this issue? 

I'm running Minecraft Beta Server 1.3
and Minecraft Beta 1.3_01.

I'm running the server in a ramdrive to minimize lag as per instructions found here: [http://ubuntuforums.org/showthread.php?t=1667154&highlight=minecraft+cron](http://ubuntuforums.org/showthread.php?t=1667154&highlight=minecraft+cron)

I have Back In Time installed as per those instructions, but I don't know how to set it so it backs up the world files or restores them before playing.

Can anyone give me some advice or instructions?

---

### Post by flaak_monkey on 2011-03-15
Here is a link in the Minecraft Forums that explain in depth all the ins and outs for setting up a Minecraft server in Linux. This particular guide was set up in Ubuntu 9.10. 

[http://www.minecraftforum.net/viewtopic.php?t=628](http://www.minecraftforum.net/viewtopic.php?t=628)

---

### Post by wog on 2011-03-16
It also appears to be on a VPS, which is a little rich for my blood. It also says nothing about how to backup or restore data, since I assume the dedicated service does this for you. 

Unless I missed something.

People keep suggesting dedicated servers to me, but they don't explain why. The minecraft server software takes up 9.4 megs (so far), so it isn't a hard drive hog. There's a guy on the Ubuntu Forums here running a server on his home network using a machine with 2 gigs on it, so it clearly isn't a memory hog. 

This leaves bandwidth. Does minecraft require a lot of bandwidth per player? If so, how much?

---

### Post by chasem1991 on 2011-03-16
> **wog said:**
> 

This leaves bandwidth. Does minecraft require a lot of bandwidth per player? If so, how much?



Which brings us to
[http://canihostaminecraftserver.com/]("http://canihostaminecraftserver.com/")

Input your connection speed and it will tell you how many players would be able to connect to your server at a time. Also check out the minecraft forums..... they have loads of threads about hosting servers in linux.

---

### Post by wog on 2011-03-24
That is a beautiful concept for a site! I'm glad someone thought of it, and thank you for telling me about it!

I just wish that when it came back and told you that you can't run a minecraft server because you don't have enough ram, it actually gave you a recommendation for how much ram you need at a minimum for how many people.

This either means they want you to spam their site with multiple requests, or they didn't think this whole recommendation site through very well.

---

