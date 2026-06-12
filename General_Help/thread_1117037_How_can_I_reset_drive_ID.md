---
title: "How can I reset drive ID?"
date: 2009-04-05
forum: General Help
---

### Post by Roasted on 2009-04-05
This may be a small spin off of Ubuntu, but I figured I'd try anyway.

I have an HP dc5100 SFF computer. I also have an Ubuntu laptop with FOG, an open source cloning utility. I have an XP Pro image on my laptop and I was testing it with the dc5100 SFF.

The original 80gb SATA hard drive in the dc5100 is /dev/sdb.

I wanted to throw in a curve ball to the situation and replace the 80gb SATA drive with another 80gb SATA hard drive I had sitting around. The thing is, FOG errors out because this other hard drive I put in is seen as /dev/sda, so it says invalid partition table or something like that.

How can I get this computer to read it as /dev/sdb or something so I can image it?

EDIT - I just now thought about something. The original image is from a dc5000, which I believe had an IDE hard drive. The dc5100 I'm playing with has a SATA drive. I wasn't counting on the image working, since it's a different model computer, but I tried it anyway just to mess around since they're spare pcs. I wonder if the IDE on 5000 and SATA on 5100 makes the difference.

---

