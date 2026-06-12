---
title: "Best Streaming Software"
date: 2006-06-29
forum: Desktop Environments
---

### Post by tom purl on 2006-06-29
I've been downloading a lot of public domain videos lately using BitTorrent, and I store them on my Ubuntu server since it has the biggest hard drive.  I would like to be able to view these videos on my laptop (running XP) using streaming.

What's the best streaming video server/client combination that you guys are using?  I found VideoLan (VLC), which is a great client (with streaming server capabilities apparently).  I also found a lot of other choices, but the functionality of a lot of them is vague.

Thanks in advance for any help!

Tom Purl

---

### Post by peter72 on 2006-06-29
This easiest thing to serve it out over http.  Is there a reason you want to do streaming?   There are a lot of benefits to streaming, but most of them involve supporting slow connections, supporting a lot of users, protect content from being copied (doesn't really work), broadcasting content over UDP, etc.  For simple streaming from a server, I'd just set up an apache server and publish the content. 


Pete

---

### Post by magicrobotmonkey on 2006-06-29
hey i have a similar setup at home - a media box with music movies serving a couple of laptops and a desktop. I was, up until a couple of days ago, serving up the data using a samba share, but then i discovered sshfs, which lets you mount a box you have ssh access to and its way faster and more lightweight then samb or nfs. Give it a try I think its in the repos.

---

### Post by tom purl on 2006-06-30
Thanks for all of the advice guys!  I guess the reason that I wanted to stream videos is because it takes up less disk space on the laptops (in the long run), and you can start watching a movie instantly, instead of waiting 15 minutes to download it first.  I'm a big fan of gnump3d, and I was hoping that I could find something similar for videos.

I agree with peter72 though, streaming video is *hard*; there really isn't an easy way to do it yet.  So for my current needs, setting up an Apache site really does sound like the best idea.

Thanks for all of the advice!

Tom Purl

---

