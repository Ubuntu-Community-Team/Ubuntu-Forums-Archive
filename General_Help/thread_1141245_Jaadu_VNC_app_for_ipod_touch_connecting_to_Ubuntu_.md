---
title: "Jaadu VNC app for ipod touch connecting to Ubuntu 8.04"
date: 2009-04-28
forum: General Help
---

### Post by scribaniwannabe on 2009-04-28
I am running Ubuntu HArdy Heron and have gotten remote desktop working fine. The server pops up in the app on the ipod when im on the same network as my coputer, but i can't figure out how to connect with needing to be local. i do have the box unchecked in remote desktop that says only allow local users. any ideas?

---

### Post by tnt533 on 2009-09-29
Are you trying to use the same IP address in both cases? The internal IP address you use while on your local network at home will not work when you are trying to connect elsewhere, ie at work or on the road through 3G.

Open a console and type ifconfig and hit <enter>. The output of that command will list all the needed information about your network interface including your external IP address that is assigned to you by your ISP. That is the IP you should be using when not locally connected to your network. You will also have to configure VNC on your desktop to accept external connections as well.

There are quite a few reasons why you would NOT want to use VNC over the internet as it can be very insecure. Google SSH and also read [this]("https://help.ubuntu.com/community/VNC").

---

