---
title: "GParted is Pi##ing me off - Help"
date: 2008-12-22
forum: General Help
---

### Post by Mike.B on 2008-12-22
You can view my current partitions in the screengrab below. All I want to do is use the free space on /dev/sda1 to give more disk space to /dev/sda5. I've spent hours on it, surely it's not that difficult. I've read tutorials, used Live CD, but I cannot get it to do what I want. Can anyone help! PLEASE.

---

### Post by WillBMX on 2008-12-22
When I used it before, it was as simple as this - just click on the /dev/sda1 bar and drag the edge of it in so it's smaller, then /dev/sda5 should follow the edge and get bigger (talking about the actual bar things in the screenshot there which show the size of each partition). If it just leaves an empty space then I'm not sure what to do...

---

### Post by azmo35 on 2008-12-22
Hi,click on sda1 and you will see the icon RESIZE/MOVE change click on that and move from rigth to the left go ahed and click on sda5 and do the same don't worry because this changes only will be permanent when you click apply,you can do one a time use live cd .

---

### Post by CatKiller on 2008-12-22
> **Mike.B said:**
> I've spent hours on it, surely it's not that difficult.

It isn't difficult. Select sda1. Hit Resize/Move. Resize it as you wish and hit Apply. Do the same for the extended partition (sda2) and sda5 inside it.

You need to be running from a live cd. This isn't optional. You cannot fiddle with a partition that's mounted, and your Linux partition is necessarily mounted if you're using it to run GParted. See the keys in your screenshot? That's what I'm talking about.

---

