---
title: "Ubuntu on Dell Laptop invisible to Projector"
date: 2012-02-27
forum: Dell Ubuntu Support (CLOSED)
---

### Post by llanitedave on 2012-02-27
I had a presentation in Libre Office Impress ready to review.  I brought my Dell Vostro 1720 into the room and hooked it up via the video port to the slideshow projector.

Nothing.  The projector didn't see it.  In a totally embarrasing turn of events, I was forced to save the presentation to a .ppt file, modify it on a Windows computer, and then use a Windows laptop to connect to the projector.

Right now I don't know if the problem is Dell or Ubuntu. The Displays option in my system settings shows my laptop monitor as "Unknown", and it did the same thing when the projector was plugged in.

Has anyone else experienced this?

I kind of hope not!  :icon_frown:

---

### Post by Randallflagg on 2012-03-12
I have the same problem with Dell Latitude D820. Am using Ubuntu 11.10. I tried adding new drivers for nvidia

sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get upgrade

and then installing disper as per link: [http://www.baibhav.com.np/article/6-computer-tips-a-tricks/32-projector-external-monitor-display-problem-on-ubuntu-1110-solved-.html](http://www.baibhav.com.np/article/6-computer-tips-a-tricks/32-projector-external-monitor-display-problem-on-ubuntu-1110-solved-.html)
but it didn't help.

Any other recommendations?

---

