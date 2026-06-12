---
title: "Samba suddenly doesn't want to share."
date: 2009-03-10
forum: General Help
---

### Post by Lutrova on 2009-03-10
Maybe that's an inaccurate title for the post, but close enough. I have a server running Ubuntu Server 8.10. I had initially set up Samba and everything was just fine. All Windows PC's on the network could read and write to the public share directory I had set up and I had created a private folder for backing things up for myself.

I bought a Linksys router to replace the D-Link that was having a few minor issues (would just randomly crash once or twice a week). Now keep in mind I have not changed ANY configuration options on the Server by now except the initial configuration. Since installing the Linksys, Server refuses to share properly. Thinking it was the router, I switched the D-Link back.

Every other network issue has been resolved now, however the Server has decided that it won't let me write to the Public directory and thinks that my personal, private directory should be public, allowing anyone on the network to browse all the files. I must reiterate I have not changed anything in the configuration or anything else to make it do this. It did this only after installing the new router.

**Furthermore**.... I am on a laptop running Windows. When I'm using the _wireless_ connection, I see the Server in the Network window, but it won't let me browse, returning the error, "Windows cannot access \\SERVER. Check the spelling of the name. Etc. Etc. Etc." More Info reveals an error code of 0x80070035 saying the network path was not found. If I connect using a wired connection, it can browse the Server just fine (with aforementioned problems in the previous paragraph).

Any ideas what on Earth happened here and how I can fix this? Searches through the forums and anywhere else turned up vaguely similar problems, but none of the solutions worked (or obviously wouldn't work).

---

### Post by cmnorton on 2009-03-10
First thing to do is look in the logs under /var/log. Red Hat has a samba directory. I don't remember how Ubuntu's samba places its logs.

This also sounds like a routing problem. Windows sharing might require you to add a route statement when you start up.

---

### Post by Lutrova on 2009-03-10
> **cmnorton said:**
> First thing to do is look in the logs under /var/log. Red Hat has a samba directory. I don't remember how Ubuntu's samba places its logs.

This also sounds like a routing problem. Windows sharing might require you to add a route statement when you start up.

That sort of doesn't make any sense. Why would it just work the first time, even over wireless, with absolutely zero issues, even through the router crashing, various resets, etc., but literally just decide seemingly by itself after switching the routers that it's not going to let anyone write to the public directory and then expose my private directory to reading?

I'll have to take a look at the logs whenever I get home from work in the morning though.

**EDIT:** I've managed to log on and just poke at the samba logs. I'll be honest, I have absolutely no idea what it is I'm looking for that would even remotely tell me what went wrong.

---

### Post by cmnorton on 2009-03-12
Did this new router change your subnet, like from 192.168.1 to 192.168.0 for example?

Do you have a firewall turned on?

Has the router the capability to change the domain name?

Samba reversing permissions sounds a little weird. Pulling samba messages out of the logs is the only way I know to debug this.

---

