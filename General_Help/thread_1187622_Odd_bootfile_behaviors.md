---
title: "Odd boot/file behaviors"
date: 2009-06-14
forum: General Help
---

### Post by finch127 on 2009-06-14
So before I start, I have to say this isn't really a problem, more like a bug or something completely strange that I noticed recently. 

Anyway, what happened to me was very strange, I was booting like usual and I got an error, something about my X-Server not having permissions to the tmp directory or some issue. I tried to boot in safe GNOME but I got another weird error, something like "gconf exited with error code 256". So that was ruled out. I tried safe terminal and the tty's and they all worked so I tried to diagnose the problem. I did a few fsck's to see if my drives were fine, i used smartctl to check that as well, and all was good no errors, etc etc. My system was perfectly fine. Obviously though, this wasn't the case; I couldn't boot. That is, it was fine until I started thinking about it. Sure enough, I went to my root filesystem and the /tmp directory had different file permissions to it, so I just used chmod to change the permissions to normal and it works now... but I can't use my printer anymore? 

I don't know, its not important, but I was wondering if anyone knows how something this strange can happen. Could some program have changed the permissions etc? Or was it just a fluke of nature?

---

