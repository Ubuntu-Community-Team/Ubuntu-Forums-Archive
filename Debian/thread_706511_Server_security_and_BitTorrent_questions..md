---
title: "Server security and BitTorrent questions."
date: 2008-02-24
forum: Debian
---

### Post by sajro on 2008-02-24
Hello UF users,

I'm setting up a Debian server for a web site, but I also want to set up a BitTorrent tracker on it. It will be to distribute some audio and video files related to the site (the torrents will be multi-tracker, but I want a local one that definitely won't get shutdown by anti-piracy idiots with their lawsuits, since the content I'm distributing is mine). 

I need to know some things about securing a Debian server. Does anyone have some tips or a link to a good tutorial? For the server itself, I'm using learndebian.com's excellent tutorial, but it warns that the server it makes is insecure as is. So I need to know how to keep my server secure from crackers.

Also, I'm wanting to, as mentioned before, set up a small tracker. I want to make it to where only I can put torrents into it, but it's public for downloading. I'm guessing Opentracker would be great, but I need to learn how to use it. If there's other trackers you think would be better please speak up!

Thanks for your time,
Sajro

---

### Post by bwhite82 on 2008-02-24
I would simply google and then read up on as much Debian security documentation you can get your eyes on. Here's a couple links to get you started:

[http://www.servepath.com/support/debian_securitychecklist.htm](http://www.servepath.com/support/debian_securitychecklist.htm)

[http://www.aboutdebian.com/security.htm](http://www.aboutdebian.com/security.htm)

After you feel that you've done as much as you can,  subscribe to the 'debian-security-announce' mailing list and proactively stay on top of the newest threats. Hit up sites like milw0rm and some of the more nefarious sites to keep up on the absolute latest threats. That said, you can't stop the determined cracker/hacker but you *can* stop the average joe script kiddie.

A good rule of thumb regarding security is only running the absolutely necessary miminum services and web applications that you wish to present.

---

