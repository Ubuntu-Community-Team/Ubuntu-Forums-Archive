---
title: "Remote access from internet"
date: 2009-03-16
forum: General Help
---

### Post by baer3328 on 2009-03-16
Hello,

I'm in the process of setting up my first dedicated Linux box and need remote access to it.  Remote is the main method I will be connecting to this box so it is almost a necessity to have the full GUI in front of me.  I'm still learning it so I don't want to knock crutches ATM.  I've read about Xforwarding and all that but I was working on the Remote Desktop front.

My question is, why won't this work over the internet?  I've modified the port and forwarded that port (and that port only) to the necessary static IP.  I cannot get to that box.  I've tried using the three biggest viewers, Real, Tight, and Ultra, but none of them will connect.  Is there a hidden port or am I doing something wrong that is preventing this from connecting?

---

### Post by crokett on 2009-03-16
What port are you forwarding?  Default is 5900.  Did you configure the desktop to allow forwarding?  Click System->Preferences-Remote Desktop

I would verify you can do this from your local LAN before trying it over the internet.

FYI, tunneling remote desktop over ssh is a bit more secure.  I recommend you do this for a long term solution.

---

