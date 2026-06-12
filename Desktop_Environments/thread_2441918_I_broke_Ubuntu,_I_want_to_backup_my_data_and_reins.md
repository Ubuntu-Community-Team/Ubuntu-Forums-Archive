---
title: "I broke Ubuntu, I want to backup my data and reinstall it."
date: 2020-04-28
forum: Desktop Environments
---

### Post by propereferio on 2020-04-28
Hey everybody! ):P

I love Ubuntu, started using it in December. I was trying to use some terminal commands to resolve an issue with Docker, and I think that's what led to Ubuntu failing to boot thereafter.

(The main question is: **How do I recover my data?**)

Here are the commands I put in (with the link where I got them):

I made my user's .docker folder accessible without sudo like so: sudo chgrp -hR docker ~/.docker && sudo chown -R myuser ~/.docker. the chgrp didn't seem to help though, so probably I should only recommend the chown step. – Birchlabs Jul 28 '17 at 11:24

[https://askubuntu.com/questions/477551/how-can-i-use-docker-without-sudo](https://askubuntu.com/questions/477551/how-can-i-use-docker-without-sudo)

So I'd like to start ubuntu in recovery mode, save my data to a hard drive, and then remove and reinstall ubuntu in that partition of my hard drive.

The first step is the one I'm least sure about: **How do I recover all my data?**

---

### Post by guiverc on 2020-04-28
I personally find it easier to boot a 'live' system (eg. Ubuntu install media and using 'try ubuntu' type option), navigate to my installed system, I usually `apt install nfs-common` (*as my normal backup place is to NFS shares*) and perform my backups from there.

I get the feeling you're talking a server (not desktop), and 'live' mode was the default except for the latest two install ISO media (and being it was in test before then, had less capacity potentially) so it may not be possible with your existing media (you didn't give release details).  Desktops I find easy to re-install Ubuntu (and flavors) without being destructive to data (something-else/manual and no format), but I'm not familiar with docker sorry so cannot advise there.

---

