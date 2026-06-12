---
title: "Strange CD burning problem"
date: 2006-04-17
forum: Desktop Environments
---

### Post by pjbgravely on 2006-04-17
When ever I burn an CD, either a data disk or an ISO ( I haven't tried any audio Cd's) The burning program will run, and then 30 seconds later say I have finished burning the CD. The CD mounts as blank and I can try again, but if I look at the surface I see where it has been written to at the beginning of the CD ( which is the middle) When I first saw this problem I had just upgraded to 5.10 and thought the upgrade messed something up so I did a clean install and still had the problem. 

I have tried 2 different IDE CD-burners, and 1 USB CD/DVD burner, while trying Nautilus, K3B, and Gnome Baker. I have used different brands of CD R's. They all work fine in my laptop running 5.10. Since there is no error message I can't post one.

I also cannot erase any CD-RW's either, that process ends with an unknown error but I am not sure that it is related

Paul

---

### Post by pjbgravely on 2006-04-26
Update,

The burning ISO's problem was solved by using a third brand of CD-R's. 

I also solved the CD-RW burning problem by running Gnome Baker in root. There seems to be a permission problem with the blanking process where it needs root permission to do the thermal test. Strange is that my laptop running breezy worked fine. 

Paul

---

