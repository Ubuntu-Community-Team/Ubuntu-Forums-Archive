---
title: "Boot from to RAM and persist"
date: 2009-03-19
forum: General Help
---

### Post by OliW on 2009-03-19
In the coming weeks (or months depending on the prices of DDR3), I'm going to be looking to buy a new computer. I don't do that terribly often so when I do, I tend to get a little carried away.

I mention RAM because I'm looking to stuff 12 or 24gigs of DDR3 in this new creation with the dream that I could, at boot, load Ubuntu into RAM and run at the speed of light from thereon.

Before anybody jumps in and hoses me down with a sample of your best "but RAM is volatile;  you'll lose everything when you reboot!", I realise this. Part of my dream (because that's all it is at the moment) is dumping the ram-disk to real-disk once every few hours.

/home would live on its RAID1 array where it currently is... 

---

So first of all, am I crazy? Am I dreaming if I think this would be much faster? Because on paper, this looks like it would beat that crazy Samsung SSD demo that went out a couple of weeks ago (below) by a colossal margin.

[http://www.youtube.com/watch?v=96dWOEa4Djs&fmt=22](http://www.youtube.com/watch?v=96dWOEa4Djs&fmt=22)

Is it possible? Can you dump an active volume to an image or disk? Can you load one up at boot?

And finally and by no means least, how on earth would one go about doing all this?

---

My install is about 10 gigs. I'd like to cut that down to 6-8 by the time I'm doing this seriously. I reckon I'm looking at between 3 and 5 minutes for a boot at 40-50MB/s read for ~7 gigs

---

### Post by dusan.saiko on 2009-03-19
I woun't give you a precise advice how to do it, but I like this idea too and I am sure it is achievable.

I was trying to do something simillar some week ago with Eclipse and my programming stuff, where I made a script which first unpacked eclipse and workspace into tmpfs, started the eclipse from there and after closing the app script pakced the files into tar archive back to the disk again. May be you could do some scripting like that in your bootscripts. 

I can imagine mounting /var /user etc into tmpfs which should be memory based, then mounting /realfsdata partition, copiing the system from there and scheduling 
rsync command in the cron scheduler.

I would be quite interested in your progress and problems you would eventually meet, please keep this thread updated :-).

Good luck.

---

